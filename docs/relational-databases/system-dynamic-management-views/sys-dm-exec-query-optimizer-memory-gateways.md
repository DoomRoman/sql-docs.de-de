---
title: Sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL) | Microsoft Docs
description: Gibt den aktuellen Status der Ressource Semaphore verwendet, um gleichzeitige abfrageoptimierung Drosselung
ms.custom: ''
ms.date: 04/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_memory_gateways_TSQL
- dm_exec_query_optimizer_memory_gateways
- sys.dm_exec_query_optimizer_memory_gateways_TSQL
- sys.dm_exec_query_optimizer_memory_gateways
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_memory_gateways dynamic management view
author: josack
ms.author: josack
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b9d36c4a67fab2f9f7c867a3ba6b7e7d01fc5d29
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34468066"
---
# <a name="sysdmexecqueryoptimizermemorygateways-transact-sql"></a>Sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Gibt den aktuellen Status der Ressource Semaphore verwendet, um gleichzeitige abfrageoptimierung zu drosseln.

|Column|Typ|Description|  
|----------|---------------|-----------------|  
|**pool_id**|**int**|ID des Ressourcenpools unter Ressourcenkontrolle|  
|**name**|**sysname**|Kompilieren Sie Gate-Namen (kleine Gateway Gateway Mittel, Groß Gateway)|
|**max_count**|**int**|Der konfigurierten Maximalanzahl von gleichzeitigen kompiliert|
|**active_count**|**int**|Die Anzahl der derzeit aktiven Kompilierungen ein, die in dieses gate|
|**waiter_count**|**int**|Die Anzahl der Wartevorgänge in dieses gate|
|**threshold_factor**|**bigint**|Schwellenwertfaktor, der der maximale Arbeitsspeicheranteil verwendet, durch die abfrageoptimierung definiert.  Für das kleine Gateway gibt Threshold_factor die maximale Optimierer Auslastung des Speichers in Bytes für eine Abfrage an, bevor ein Zugriff in das small-Gateway muss.  Für das Gateway mittelgroßen und großen zeigt Threshold_factor den Teil des gesamten Serverspeichers für dieses Gate verfügbar. Es wird als Divisor verwendet, bei der Berechnung der nutzungsschwellenwert für Speicher für das Gate.|
|**threshold**|**bigint**|Nächste Schwellenwert-Speicher in Bytes.  Die Abfrage ist erforderlich, um einen Zugriff auf dieses Gateway zu erhalten, wenn ihren Arbeitsspeicherverbrauch dieser Schwellenwert erreicht.  "1", wenn die Abfrage nicht erforderlich ist, um einen Zugriff auf dieses Gateway zu erhalten.|
|**is_active**|**bit**|Gibt an, ob die Abfrage erforderlich ist, um die aktuellen Gate oder nicht übergeben.|


## <a name="permissions"></a>Berechtigungen  
SQL Server erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.

Azure SQL-Datenbank erfordert die VIEW DATABASE STATE-Berechtigung in der Datenbank.


## <a name="remarks"></a>Hinweise  
SQL Server verwendet einen mehrstufigen Gateway-Ansatz zum Einschränken der Anzahl der zugelassenen gleichzeitigen Kompilierungen.  Drei Gateways werden verwendet, einschließlich klein, Mittel und groß. Gateways verhindern, dass die Überbeanspruchung der insgesamt verfügbaren Speicherressourcen von größeren Kompilierung Arbeitsspeicher erfordern Consumern.

Wartet auf ein Gateway Ergebnis verzögerte Kompilierung. Zusätzlich zu Verzögerungen bei der Kompilierung müssen begrenzte Anforderungen eine zugeordnete RESOURCE_SEMAPHORE_QUERY_COMPILE Typ Accumulation / warten. Der Wartetyp RESOURCE_SEMAPHORE_QUERY_COMPILE hinweisen, dass Abfragen eine große Menge an Arbeitsspeicher für die Kompilierung verwenden und, dass der Arbeitsspeicher ist erschöpft, oder Sie können auch ausreichend Arbeitsspeicher verfügbar ist insgesamt jedoch verfügbaren Einheiten in einer bestimmten Gateway abgearbeitet wurden. Die Ausgabe des **sys.dm_exec_query_optimizer_memory_gateways** können verwendet werden, um die Problembehandlung hilfreich, obwohl Sie einen Abfrageausführungsplan Kompilieren nicht genügend Arbeitsspeicher vorhanden war.  

## <a name="examples"></a>Beispiele  

### <a name="a-viewing-statistics-on-resource-semaphores"></a>A. Anzeigen von Statistiken zur Ressource Semaphoren  
Was sind die aktuellen Optimierer Arbeitsspeicher Gateway Statistiken für diese Instanz von SQL Server?

```  
SELECT [pool_id], [name], [max_count], [active_count],
       [waiter_count], [threshold_factor], [threshold],
       [is_active]
FROM sys.dm_exec_query_optimizer_memory_gateways;   

```  

## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](./system-dynamic-management-views.md)   
 [Ausführung dynamische Verwaltungssichten und-Funktionen im Zusammenhang &#40;Transact-SQL&#41;](./execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[Gewusst wie: Verwenden Sie den Befehl DBCC MEMORYSTATUS zur Überwachung der arbeitsspeichernutzung für SQL Server 2005](https://support.microsoft.com/help/907877/how-to-use-the-dbcc-memorystatus-command-to-monitor-memory-usage-on-sql-server-2005)
[große Abfragekompilierung wartet auf RESOURCE_SEMAPHORE_QUERY_COMPILE in SQL Server 2014](https://support.microsoft.com/help/3024815/large-query-compilation-waits-on-resource-semaphore-query-compile-in-sql-server-2014)
