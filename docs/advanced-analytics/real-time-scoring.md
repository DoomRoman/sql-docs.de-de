---
title: Bewerten von Realtime | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: eda95bf4cd16c5c38277e6d139c224f225c9b10a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31202772"
---
# <a name="realtime-scoring"></a>Echtzeit-Bewertung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Thema wird beschrieben, ein Feature in SQL Server 2016 und SQL Server-2017, der Machine Learning-Modellen in beinahe in Echtzeit unterstützt Bewertung verfügbar.

> [!TIP]
> Systemeigene bewerten ist eine spezielle Implementierung der Echtzeit-Bewertung, verwendet die systemeigene VORHERZUSAGEN, T-SQL-Funktion für sehr schnell bewerten und steht nur in SQL Server-2017. Weitere Informationen finden Sie unter [Native Bewertung](sql-native-scoring.md).

## <a name="how-realtime-scoring-works"></a>Funktionsweise der Echtzeit-Bewertung

Echtzeit-Bewertung wird für bestimmte Modelltypen mit Tabellenparameter "revoscaler" oder MicrosoftML Algorithmen erstellt wurden in SQL Server-2017 und SQL Server 2016 unterstützt. Er verwendet die systemeigene C++-Bibliotheken zum Generieren von Bewertungen, basierend auf Benutzereingaben bereitgestellt, um ein Machine learning-Modell in einem speziellen binären Format gespeichert.

Da einem trainierten Modell für die Bewertung ohne eine externe Sprachlaufzeit Aufruf verwendet werden kann, wird der Aufwand von mehreren Prozessen reduziert. Dadurch wird eine schnellere vorhersageleistung für die Produktion Bewertung Szenarien unterstützt. Da die Daten niemals SQL Server verlässt, können Ergebnisse generiert und in eine neue Tabelle ohne jegliche Daten Übersetzung zwischen R und SQL eingefügt werden.

Echtzeit bewerten ist ein mehrstufiger Prozess:

1. Die gespeicherte Prozedur, die Bewertung ist, muss regelmäßig pro Datenbank aktiviert sein.
2. Sie laden das vortrainierte Modell im Binärformat.
3. Geben Sie neue Eingabedaten, tabellarische oder einzelne Zeilen als Eingabe für das Modell.
4. Generieren von Bewertungen, rufen Sie die Sp_rxPredict Prozedur enthält.

## <a name="get-started"></a>Erste Schritte

Codebeispiele und Anleitungen finden Sie unter [wie systemeigene Bewertung oder Echtzeit Bewertung](r/how-to-do-realtime-scoring.md).

Ein Beispiel für RxPredict wie kann für die Bewertung verwendet, finden Sie unter [End-to-End Loan ChargeOff Vorhersage erstellt mithilfe von Azure HDInsight Spark-Cluster und SQL Server 2016-R-Dienst](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> Wenn Sie ausschließlich in R-Code arbeiten, können Sie auch die [RxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) Funktion zur schnellen Bewertung.

## <a name="requirements"></a>Anforderungen

Echtzeit-Bewertung wird auf diesen Plattformen unterstützt:

+ SQL Server 2017-Machine Learning-Dienste
+ SQL Server R Services 2016 mit einer Aktualisierung der R-Services-Instanz für Microsoft R Server 9.1.0 oder höher
+ Machine Learning-Server (eigenständig)

Auf SQL Server müssen Sie die Funktion im Voraus Bewertung Echtzeit aktivieren. Dies ist, da die Funktion, die Installation der CLR-basierten Bibliotheken in SQL Server erfordert.

Informationen zu Echtzeit Bewertung in einer verteilten Umgebung basierend auf Microsoft R Server finden Sie auf der [PublishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice) Funktion zur Verfügung, in der [MrsDeploy Paket](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package), welche unterstützt Veröffentlichen von Modellen in Echtzeit Bewertung als neue einen Webdienst, der auf R-Server ausgeführt wird.

### <a name="restrictions"></a>Einschränkungen

+ Das Modell muss im voraus mit einer der unterstützten trainiert **Rx** Algorithmen. Weitere Informationen finden Sie unter [Algorithmen unterstützt](#bkmk_rt_supported_algos). Echtzeit-batchbewertung mit `sp_rxPredict` "revoscaler" und MicrosoftML Algorithmen unterstützt.

+ Das Modell muss gespeichert werden, mit den neuen Serialisierungsfunktionen: [RxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) für R, und [Rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) für Python. Diese Serialisierungsfunktionen wurden zur Unterstützung von schnellen Bewertung optimiert.

+ Echtzeit-Bewertung wird ein Interpreter Interpreter nicht verwendet werden. solche Funktionen verwendet werden, die möglicherweise ein Interpreter wird deshalb nicht während des Schritts bewerteten unterstützt.  Hierzu gehören zum Beispiel:

  + Modelle mit der `rxGlm` oder `rxNaiveBayes` Algorithmen werden derzeit nicht unterstützt.

  + "Revoscaler"-Modelle, verwenden ein R-Transformationsfunktion oder eine Formel, die eine Transformation enthält, z. B. <code>A ~ log(B)</code> werden in Echtzeit Bewertung nicht unterstützt. Ein Modell für diesen Typ verwenden, empfiehlt es sich, dass das Ausführen der Transformations für die Eingabe von Daten vor der Übergabe an die Echtzeit-Bewertung.

+ Echtzeit-Bewertung ist zurzeit für schnelle Vorhersagen in kleinere Datasets, die im Bereich von ein paar Zeilen bis Hunderte von tausend Zeilen optimiert. In sehr großen Datasets können mit [RxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) möglicherweise schneller.

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-realtime-scoring"></a><a name="bkmk_rt_supported_algos">Algorithmen, die Echtzeit-Bewertung unterstützen

+ "Revoscaler"-Modelle

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  Modelle mit markierten \* unterstützen auch die systemeigenen batchbewertung mit der PREDICT-Funktion.

+ MicrosoftML Modelle

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Transformationen von MicrosoftML bereitgestellten

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Nicht unterstützte Modelltypen

Die folgenden Modelltypen werden nicht unterstützt:

+ Modelle, die mit anderen, nicht unterstützte Arten von R-Transformationen
+ Modelle mit der `rxGlm` oder `rxNaiveBayes` Algorithmen in "revoscaler"
+ PMML-Modelle
+ Mit anderen R-Bibliotheken von CRAN oder anderen Repositorys erstellte Modelle
+ Modelle, die eine beliebige andere Art von R-Transformation, andere als die hier aufgeführten enthält

### <a name="known-issues"></a>Bekannte Probleme

+ `sp_rxPredict` Gibt eine fehlerhafte Nachricht zurück, wenn ein NULL-Wert wie das Modell übergeben wird: "System.Data.SqlTypes.SqlNullValueException:Data in Null".

## <a name="next-steps"></a>Nächste Schritte

[Wie Sie Echtzeit-Bewertung](r/how-to-do-realtime-scoring.md)
