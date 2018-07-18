---
title: "\"Revoscaler\"-Paket in SQL Server-Machine Learning | Microsoft Docs"
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ecca127e3b929772c465ae7e1f694b525cc7dd00
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201972"
---
# <a name="revoscaler"></a>"Revoscaler"
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

"Revoscaler" ist ein Paket von Machine Learning, bereitgestellten Funktionen von Microsoft, die Data Science Größenordnungen unterstützt.

+ Funktionen unterstützen die Daten importieren, Datentransformation, Zusammenfassung, Visualisierung und Analyse.

+ _Die gatewaypooltopologie_ bedeutet, dass die Vorgänge können sehr großen Datasets können parallel ausgeführt und auf der verteilten-Dateisysteme. Algorithmen können über Datasets arbeiten, die nicht groß im Arbeitsspeicher, genug ist indem Sie die Aufteilung und vereiteln Ergebnisse, wenn Vorgänge abgeschlossen wurden.

+ "Revoscaler" bietet zahlreiche Verbesserungen gegenüber open Source-R-Funktionen. Es gibt viele der beliebtesten Basis R-Funktionen für "revoscaler"-Funktionen. RevoScaleR-Funktionen mit gekennzeichnet sind ein **Rx** oder **Rx** Präfix, das sie einfach identifizieren zu können.

+ "Revoscaler" dient als eine Plattform für die verteilte Data Science. Beispielsweise können Sie die "revoscaler" rechenkontexte und Transformationen mit dem Status der Art-Algorithmus in [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Sie können auch [RxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) Basis R-Funktionen parallel ausgeführt.

Beispiele von "revoscaler" in Aktion finden Sie in folgenden Blogs: 

+ [Erstellen und Bereitstellen eines Vorhersagemodells mittels R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Vorhersagen von einer Million pro Sekunde mit Machine Learning-Server](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [Vorhersagen von Taxi Tipps MicrosoftML](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [Leistungsoptimierung mit rxExec](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

## <a name="how-to-get-revoscaler"></a>Gewusst wie: Abrufen von "revoscaler"

"Revoscaler"-Paket für R ist kostenlos im Microsoft-R-Client installiert. Wenn Sie Machine Learning-Server haben oder R in SQL Server verwenden, ist standardmäßig "revoscaler" enthalten.

Bei Verwendung von Python, die [Revoscalepy](../python/what-is-revoscalepy.md) Paket stellt die entsprechende Funktionalität bereit.

> [!IMPORTANT]
> Die RevoScaleR-Paket kann nicht heruntergeladen oder unabhängig von der Produkte und Dienste, die diese bereitstellen verwendet werden.

## <a name="use-revoscaler-in-sql-server"></a>Verwenden Sie "revoscaler" in SQLServer

Diese Lernprogramme und Beispiele veranschaulichen, wie RevoScaleR-Funktionen zum Abrufen von Daten aus SQL Server, Modelle erstellen und Speichern von Modellen in einer Datenbank für die Bewertung verwenden.

+ [Erfahren, wie Sie rechenkontexte verwenden](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R für SQL-Entwickler: trainieren und operationalisieren ein Modells](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft-Produkt-Beispielen auf GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)

## <a name="learn-more-about-revoscaler"></a>Weitere Informationen zu "revoscaler"

Diese Lernprogramme veranschaulichen das Verwenden von "revoscaler" in anderen rechenkontexte, die von unterstützt [Machine Learning-Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), z. B. Hadoop.

+ [Was ist "revoscaler"?](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler)

+ ["Revoscaler" in 25 Funktionen durchsuchen](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)

+ [Referenz zur RevoScaleR-Paket](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

