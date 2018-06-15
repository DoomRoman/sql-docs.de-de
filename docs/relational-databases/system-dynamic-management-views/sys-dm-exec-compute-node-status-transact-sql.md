---
title: dm_exec_compute_node_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 79f0c7a7596f04f768a0ec4398ec90800bbbd08e
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34464176"
---
# <a name="sysdmexeccomputenodestatus-transact-sql"></a>dm_exec_compute_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält zusätzliche Informationen über die Leistung und Status aller PolyBase-Knoten. Enthält eine Zeile pro Knoten an.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Eindeutige numerische Id, die dem Knoten zugeordnet.|Für Cluster mit horizontaler Skalierung, unabhängig vom Typ eindeutig.|  
|process_id|**int**|||  
|process_name|**nvarchar(255)**|Logischer Name des Knotens.|Eine beliebige Zeichenfolge entsprechenden Länge.|  
|allocated_memory|**bigint**|Insgesamt zugeordneter Arbeitsspeicher auf diesem Knoten.||  
|available_memory|**bigint**|Insgesamt verfügbare Arbeitsspeicher auf diesem Knoten.||  
|process_cpu_usage|**bigint**|Insgesamt Prozess CPU-Auslastung in Ticks.||  
|total_cpu_usage|**bigint**|Gesamter CPU-Auslastung in Ticks.||  
|Thread_Count|**bigint**|Gesamtanzahl der Threads auf diesem Knoten verwendet.||  
|handle_count|**bigint**|Die Gesamtanzahl der Handles auf diesem Knoten verwendet.||  
|total_elapsed_time|**bigint**|Insgesamt verstrichene Zeit seit System gestartet oder neu gestartet.|Insgesamt verstrichene Zeit seit System gestartet oder neu gestartet. Wenn Total_elapsed_time den maximalen Wert für eine ganze Zahl (24.8 Tage in Millisekunden) überschreitet, führt es Materialisierung Fehler aufgrund einer dazu, dass "Überlauf". Der maximale Wert in Millisekunden entspricht 24.8 Tage.|  
|is_available|**bit**|Ein Flag, der angibt, ob dieser Knoten verfügbar ist.||  
|sent_time|**datetime**|Zuletzt wurde ein Netzwerk-Paket von diesem gesendet.||  
|received_time|**datetime**|Zuletzt ein Netzwerk-Paket wurde von diesem Knoten gesendet werden.||  
|error_id|**nvarchar(36)**|Eindeutiger Bezeichner des letzten Fehlers, der auf diesem Knoten aufgetreten ist.||  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase, Problembehandlung mit dynamischen Verwaltungssichten](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Datenbank verbundene dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
