---
title: dm_os_stacks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e5870f8b45d507a7f5eeffdee3ac46c1db2e669f
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Diese dynamische verwaltungssicht wird intern von verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die folgenden Schritte ausführen:  
  
-   Nachverfolgen von Debugdaten wie z. B. ausstehenden Zuordnungen.  
  
-   Voraussetzen oder Überprüfen von Logik, mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Komponenten stellen die Komponente wird, in denen davon ausgegangen, dass ein bestimmter Aufruf erfolgt ist.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|Eindeutige Adresse für diese Stapelzuordnung. Lässt keine NULL-Werte zu.|  
|**frame_index**|**int**|Jede Zeile stellt einen Funktionsaufruf dar, der bei Sortierung in aufsteigender Reihenfolge nach Rahmenindex für einen bestimmten **stack_address**-Wert die vollständige Aufrufliste zurückgibt. Lässt keine NULL-Werte zu.|  
|**frame_address**|**varbinary(8)**|Adresse des Funktionsaufrufes. Lässt keine NULL-Werte zu.|  
  
## <a name="remarks"></a>Hinweise  
 **sys.dm_os_stacks** erfordert, dass die Symbole des Servers und anderer Komponenten auf dem Server vorhanden sein müssen, damit die Informationen richtig angezeigt werden.  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   


## <a name="see-also"></a>Siehe auch  
  [SQL Server-Betriebssystem verbundene dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
