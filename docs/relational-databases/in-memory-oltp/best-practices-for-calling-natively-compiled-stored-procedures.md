---
title: Bewährte Vorgehensweisen für den Aufruf von systemintern kompilierten gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a027599604de8d63021647fd684689fea7d86b74
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645818"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>Bewährte Vorgehensweisen für den Aufruf von systemintern kompilierten gespeicherten Prozeduren
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Für systemintern kompilierte gespeicherte Prozeduren gilt Folgendes:  
  
-   Sie werden üblicherweise in leistungskritischen Anwendungskomponenten verwendet.  
  
-   Sie werden häufig ausgeführt.  
  
-   Sie zeichnen sich erwartungsgemäß durch eine sehr schnelle Ausführung aus.  
  
 Der Leistungsvorteil bei Verwendung einer systemintern kompilierten gespeicherten Prozedur nimmt mit der Anzahl der Zeilen und dem Umfang der Logik zu, die von der Prozedur verarbeitet werden. Beispielsweise lässt sich die Leistung einer systemintern kompilierten gespeicherten Prozedur durch eine oder mehrere der folgenden Maßnahmen verbessern:  
  
-   Aggregation.  
  
-   Joins geschachtelter Schleifen.  
  
-   Auswahl-, Einfüge-, Update- und Löschvorgänge mit mehreren Anweisungen.  
  
-   Komplexe Ausdrücke.  
  
-   Prozedurale Logik, wie Bedingungsanweisungen und Schleifen.  
  
 Wenn Sie nur eine einzelne Zeile verarbeiten müssen, bietet eine systemintern kompilierte gespeicherte Prozedur u. U. keinen Leistungsvorteil.  
  
 So vermeiden Sie, dass der Server Parameternamen zuordnen und Typen konvertieren muss:  
  
-   Gleichen Sie die Typen der an die Prozedur übergebenen Parameter mit den Typen in der Prozedurdefinition ab.  
  
-   Verwenden Sie Ordnungszahlparameter (namenlos), wenn Sie systemintern kompilierte gespeicherte Prozeduren aufrufen. Verwenden Sie für die effizienteste Ausführung keine benannten Parameter.  
  
 Ineffizienz in Parametern mit nativen kompilierten gespeicherten Prozeduren kann über das XEvent **natively_compiled_proc_slow_parameter_passing** erkannt werden:
 - Nicht übereinstimmende Typen: **reason=parameter_conversion**
 - Benannte Parameter: **reason=named_parameters**
 - Standardwerte: **reason=default** 
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Systemintern kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
