---
title: Lektion 4 Sie Data-Funktionen, die mithilfe von T-SQL-Funktionen (SQL Server-Machine Learning) | Microsoft Docs
description: Lernprogramm zur Einbettung von R in SQL Server gespeicherte Prozeduren und Funktionen des T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 98182e8e602b8bba8ca7d7fd58cf23f3fcaaa435
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249543"
---
# <a name="lesson-4-create-data-features-using-r-and-t-sql"></a>Lektion 4: Erstellen von Data-Funktionen, die mittels R und T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Lernprogramms für SQL-Entwicklern zum Verwenden von R in SQL Server.

In diesem Schritt erfahren Sie, wie Sie Funktionen aus Rohdaten mithilfe einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktion erstellen. Sie rufen anschließend die Funktion aus einer gespeicherten Prozedur auf, um eine Tabelle zu erstellen, die die Funktionswerte enthält.

## <a name="about-feature-engineering"></a>Informationen zu namens Feature engineering

Nachdem Sie eine Zeit damit verbracht haben, Daten zu durchsuchen, haben Sie einige Einsichten in die Daten gesammelt und sind nun bereit, mit der *Featureentwicklung*fortzufahren. Dieser Vorgang zum Erstellen von aussagekräftigen Merkmalen aus Rohdaten ist ein wichtiger Schritt im Erstellen von analytischer Models.

In diesem Dataset Abstandswerte basieren auf den Abstand gemeldeten Messgerät, und nicht notwendigerweise geografische Entfernung oder der tatsächliche Abstand zurückgelegt dar. Aus diesem Grund müssen Sie die direkte Entfernung zwischen den Abhol- und den Zielorten berechnen, indem Sie die verfügbaren Koordinaten in im Quell-Dataset NYC Taxi verwenden. Sie erreichen dies, indem Sie die [Haversine-Formel](https://en.wikipedia.org/wiki/Haversine_formula) in einer benutzerdefinierten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktion verwenden.

Verwenden Sie eine benutzerdefinierte T-SQL-Funktion, _fnCalculateDistance_, um die Entfernung mithilfe der Haversine-Formel zu berechnen, und verwenden Sie eine zweite benutzerdefinierte T-SQL-Funktion, _fnEngineerFeatures_, um eine Tabelle mit allen Funktionen zu erstellen.

Das generelle Verfahren ist wie folgt aus:

- Erstellen Sie die T-SQL-Funktion, die Berechnungen ausführt

- Rufen Sie die Funktion zum Generieren der Funktionsdaten

- Speichert die Funktionsdaten in einer Tabelle

## <a name="calculate-trip-distance-using-fncalculatedistance"></a>Berechnet Reise Abstand FnCalculateDistance verwenden

Die Funktion _FnCalculateDistance_ sollte heruntergeladen und mit registriert wurden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Rahmen der Vorbereitung für dieses Lernprogramm. Nehmen Sie sich an den Code überprüfen.
  
1. Erweitern Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Programmierbarkeit**, erweitern Sie **Funktionen** und anschließend **Skalarwertfunktionen**.   

2. Klicken Sie mit der rechten Maustaste auf _fnCalculateDistance_, und wählen Sie **Ändern** aus, um das [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript in einem neuen Abfragefenster zu öffnen.
  
    ```SQL
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function that calculates the direct distance between two geographical coordinates.  
    RETURNS float  
    AS  
    BEGIN  
      DECLARE @distance decimal(28, 10)  
      -- Convert to radians  
      SET @Lat1 = @Lat1 / 57.2958  
      SET @Long1 = @Long1 / 57.2958  
      SET @Lat2 = @Lat2 / 57.2958  
      SET @Long2 = @Long2 / 57.2958  
      -- Calculate distance  
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))  
      --Convert to miles  
      IF @distance <> 0  
      BEGIN  
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);  
      END  
      RETURN @distance  
    END
    GO
    ```
  
    - Die Funktion ist eine Skalarwertfunktion, die einen einzelnen Datenwert eines vordefinierten Typs zurückgibt.
  
    - Sie übernimmt die Werte der Längen- und Breitengrade als Eingaben, die sie von den Abhol- und Zielorten der Fahrten erhält. Die Haversine-Formel wandelt Orte ins Bogenmaß um und verwendet diese Werte, um die direkte Entfernung zwischen zwei Orten in Meilen zu berechnen.

## <a name="generate-the-features-using-fnengineerfeatures"></a>Generieren Sie die Features, die mit _FnEngineerFeatures_

Um die berechneten Werte in einer Tabelle hinzuzufügen, die zum Trainieren des Modells verwendet werden können, verwenden Sie eine andere Funktion _FnEngineerFeatures_. Die neue Funktion ruft die zuvor erstellte T-SQL-Funktion, _FnCalculateDistance_, um den direkten Abstand zwischen Standorten übernommen und Ladengeschäft abzurufen. 

1. Nehmen Sie sich ein paar Minuten Zeit, um den Code für die benutzerdefinierte T-SQL-Funktion _fnEngineerFeatures_zu überprüfen, die für Sie als Teil der Vorbereitung für diese exemplarische Vorgehensweise erstellt wurde.
  
    ```SQL
    CREATE FUNCTION [dbo].[fnEngineerFeatures] (  
    @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0)  
    RETURNS TABLE  
    AS
      RETURN
      (
      -- Add the SELECT statement with parameter references here
      SELECT
        @passenger_count AS passenger_count,
        @trip_distance AS trip_distance,
        @trip_time_in_secs AS trip_time_in_secs,
        [dbo].[fnCalculateDistance](@pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude) AS direct_distance
  
      )
    GO
    ```

    + Diese Tabellenwertfunktion, die mehrere Spalten als Eingaben und gibt eine Tabelle mit mehreren Funktionsspalten.

    + Der Zweck dieser Funktion werden neue Funktionen für die Verwendung bei der Erstellung eines Modells erstellen.

2.  Um sicherzustellen, dass diese Funktion funktioniert, verwenden sie um die geografische Entfernung für diese Roundtrips zu berechnen, denen der gemessene Abstand 0 jedoch die übernommen und Ladengeschäft Speicherorte wurden verschiedene.
  
    ```SQL
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Wie Sie sehen können, entspricht die vom Taxameter angezeigte Entfernung nicht immer der geografischen Distanz. Daher ist die Featureentwicklung so wichtig. Diese verbesserte Data-Funktionen können Sie zum Trainieren eines Machine Learning-Modells mit r

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 5: Trainieren Sie, und speichern Sie ein Modell mithilfe des T-SQL](../r/sqldev-train-and-save-a-model-using-t-sql.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Lektion 3: Durchsuchen Sie und Visualisieren Sie die Daten mithilfe von R und gespeicherte Prozeduren](../tutorials/sqldev-explore-and-visualize-the-data.md)
