---
title: Zusammenfassung der PolyBase-Funktionen mit Versionsangabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: polybase
ms.reviewer: ''
ms.suite: sql
ms.technology: database
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d1374b8620a469fef746a71e20ca938b4736f096
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34334261"
---
# <a name="polybase-versioned-feature-summary"></a>Zusammenfassung der PolyBase-Funktionen mit Versionsangabe
[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]
Zusammenfassung der PolyBase-Funktionen, die für SQL Server-Produkte und -Dienste verfügbar sind.  
  
## <a name="feature-summary-for-product-releases"></a>Zusammenfassung der Funktionen für Produktversionen  
 In dieser Tabelle sind die wichtigsten Funktionen für PolyBase sowie die Produkte zusammengefasst, in denen sie verfügbar sind.  
  
||||||
|-|-|-|-|-|   
|**Feature**|**SQL Server 2016**|**Azure SQL-Datenbank**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|Hadoop-Daten abfragen mit [!INCLUDE[tsql](../../includes/tsql-md.md)]|ja|nein|nein|ja|
|Daten aus Hadoop importieren|ja|nein|nein|ja|
|Daten für Hadoop exportieren  |ja|nein|nein| ja|
|Abfragen, Importieren aus und Exportieren in HDInsights |nein|nein|nein|nein
|Abfrageberechnungen auf Hadoop verlagern|ja|nein|nein|ja|  
|Daten aus Azure-BLOB-Speicher importieren|ja|nein|ja|ja| 
|Daten für Azure-BLOB-Speicher exportieren|ja|nein|ja|ja|  
|Daten aus Azure Data Lake Store importieren|nein|nein|ja|nein|    
|Daten aus Azure Data Lake Store exportieren|nein|nein|ja|nein|
|PolyBase-Abfragen über Microsoft BI-Tools ausführen|ja|nein|ja|ja|   


## <a name="pushdown-computation-supported-t-sql-operators"></a>Von der Weitergabeberechnung unterstützte T-SQL-Operatoren
In SQL Server und APS können nicht alle T-SQL-Operatoren an den Hadoop-Cluster weitergegeben werden. Die folgende Tabelle listet alle unterstützten und eine Teilmenge der nicht unterstützten Operatoren auf. 

||||
|-|-|-| 
|**Operatortyp**|**Weitergabe an Hadoop möglich**|**Weitergabe an Blob Storage möglich**|
|Spaltenprojektionen|ja|nein|
|Prädikate|ja|nein|
|Aggregate|Teilweise|nein|
|Joins zwischen externen Tabellen|nein|nein|
|Joins zwischen externen und lokale Tabellen|nein|nein|
|Sortierungen|nein|nein|

Partielle Aggregation bedeutet, dass eine endgültige Aggregation erfolgen muss, sobald die Daten SQL Server erreichen, aber ein Teil der Aggregation in Hadoop erfolgt. Dies ist eine häufig verwendete Methode zum Berechnen von Aggregationen in MPP-Systemen (Massively Parallel Processing).  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [PolyBase-Leitfaden](../../relational-databases/polybase/polybase-guide.md)  
  
  
