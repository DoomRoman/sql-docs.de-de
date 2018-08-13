---
title: Sys. dm_exec_query_resource_semaphores (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_query_resource_semaphores_TSQL
- dm_exec_query_resource_semaphores_TSQL
- sys.dm_exec_query_resource_semaphores
- dm_exec_query_resource_semaphores
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_resource_semaphores dynamic management view
ms.assetid: e43a2aa9-dd52-4c89-911e-1a7d05f7ffbb
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: c1b2d08d519e6765a4ba00972d257432341407df
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39544350"
---
# <a name="sysdmexecqueryresourcesemaphores-transact-sql"></a>sys.dm_exec_query_resource_semaphores (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Informationen zum aktuellen Status des Abfrageressourcensemaphors in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück. **Sys. dm_exec_query_resource_semaphores** bietet Statusinformationen zum Arbeitsspeicher für allgemeine abfrageausführung und ermöglicht Ihnen zu bestimmen, ob das System genügend Speicher zugreifen können. Diese Sicht ergänzt Arbeitsspeicherinformationen aus [Sys. dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md) ein vollständiges Bild von Statusinformationen zum Arbeitsspeicher für Server bereitstellen. **Sys. dm_exec_query_resource_semaphores** gibt eine Zeile für das normale ressourcensemaphor und eine weitere Zeile für das ressourcensemaphor für kleine Abfragen. Es gibt zwei Anforderungen für ein Semaphor kleine Abfragen aus:  
  
-   Die angeforderte arbeitsspeicherzuweisung sollte weniger als 5 MB sein.  
  
-   Die Abfragekosten sollte weniger als 3 Kosteneinheiten sein.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_exec_query_resource_semaphores**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**resource_semaphore_id**|**smallint**|Nicht eindeutige ID des Ressourcensemaphors. 0 für das normale Ressourcensemaphor und 1 für das Ressourcensemaphor für kleine Abfragen.|  
|**target_memory_kb**|**bigint**|Zuweisungsziel in Kilobytes.|  
|**max_target_memory_kb**|**bigint**|Maximal mögliches Ziel in Kilobytes. NULL für das Ressourcensemaphor für kleine Abfragen.|  
|**total_memory_kb**|**bigint**|Der vom Ressourcensemaphor belegte Arbeitsspeicher in Kilobytes. Wenn das System nicht genügend Arbeitsspeicher vorhanden ist oder wenn der erzwungene minimale Arbeitsspeicher häufig zugewiesen wird, dieser Wert kann größer sein als die **Target_memory_kb** oder **Max_target_memory_kb** Werte. Der Gesamtarbeitsspeicher ist die Summe aus dem verfügbaren und dem zugewiesenen Arbeitsspeicher.|  
|**available_memory_kb**|**bigint**|Der für eine neue Zuweisung verfügbare Arbeitsspeicher in Kilobytes.|  
|**granted_memory_kb**|**bigint**|Der insgesamt zugewiesene Arbeitsspeicher in Kilobytes.|  
|**used_memory_kb**|**bigint**|Der physisch verwendete Teil des zugewiesenen Arbeitsspeichers in Kilobytes.|  
|**grantee_count**|**int**|Die Anzahl aktiver Abfragen, deren Zuweisungen erfüllt wurden.|  
|**waiter_count**|**int**|Die Anzahl von Abfragen, die auf die Erfüllung ihrer Zuweisungen warten.|  
|**timeout_error_count**|**bigint**|Die Gesamtanzahl von Timeoutfehlern seit dem Start des Servers. NULL für das Ressourcensemaphor für kleine Abfragen.|  
|**forced_grant_count**|**bigint**|Die Gesamtanzahl erzwungener Zuweisungen des minimalen Arbeitsspeichers seit dem Start des Servers. NULL für das Ressourcensemaphor für kleine Abfragen.|  
|**pool_id**|**int**|ID des Ressourcenpools, zu dem dieses Ressourcensemaphor gehört.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   
  
## <a name="remarks"></a>Hinweise  
 Abfragen mithilfe dynamischer Verwaltungssichten, die ORDER BY oder Aggregate enthalten, können die Arbeitsspeichernutzung erhöhen und so zu dem Problem beitragen, das mit ihnen behandelt werden soll.  
  
 Verwenden Sie **Sys. dm_exec_query_resource_semaphores** für die Problembehandlung, aber schließen Sie es nicht in Anwendungen, die zukünftige Versionen von verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Mit der Ressourcenkontrollen-Funktion kann ein Datenbankadministrator Serverressourcen auf Ressourcenpools verteilen, bis zu maximal 64 Pools. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher verhält sich jeder Pool wie eine kleine unabhängige Serverinstanz und erfordert 2 Semaphore.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführung bezogene dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
  


