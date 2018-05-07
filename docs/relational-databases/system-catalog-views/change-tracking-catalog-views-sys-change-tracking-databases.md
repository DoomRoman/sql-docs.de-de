---
title: Sys. change_tracking_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- change_tracking_databases
- sys.change_tracking_databases_TSQL
- sys.change_tracking_databases
- change_tracking_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.change_tracking_databases
- change tracking [SQL Server], sys.change_tracking_databases
ms.assetid: bb233baa-2991-4904-a0eb-3772b81121a4
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a3ec7102bbbdc01694bea11911d0de9a89dbacc8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="change-tracking-catalog-views---syschangetrackingdatabases"></a>Ändern Sie die Katalogsichten für den Tracking - Sys. change_tracking_databases
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Datenbank zurück, für die die Änderungsnachverfolgung aktiviert ist.  

|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Die ID der Datenbank. Sie ist innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eindeutig.|  
|is_auto_cleanup_on|**bit**|Gibt an, ob Änderungsnachverfolgungsdaten nach der konfigurierten Beibehaltungsdauer automatisch bereinigt werden.<br /><br /> 0 = Aus<br /><br /> 1 = Ein|  
|retention_period|**int**|Wenn die automatische Bereinigung verwendet wird, gibt die Beibehaltungsdauer an, wie lange die Änderungsnachverfolgungsdaten in der Datenbank beibehalten werden.|  
|retention_period_units_desc|**nvarchar(60)**|Gibt die Beschreibung der Aufbewahrungsdauer an:<br /><br /> Minuten<br /><br /> Stunden<br /><br /> Tage|  
|retention_period_units|**tinyint**|Zeiteinheit für die Beibehaltungsdauer:<br /><br /> 1 = Minuten<br /><br /> 2 = Stunden<br /><br /> 3 = Tage|  
  
## <a name="permissions"></a>Berechtigungen  
 Für sys.change_tracking_databases werden die gleichen Berechtigungsprüfungen wie für sys.databases durchgeführt. Wenn der Aufrufer von sys.change_tracking_databases nicht der Besitzer der Datenbank ist, sind zum Anzeigen der entsprechenden Zeile mindestens die Berechtigungen ALTER ANY DATABASE oder VIEW ANY DATABASE auf Serverebene oder die CREATE DATABASE-Berechtigung für die Masterdatenbank oder aktuelle Datenbank erforderlich.  
  
## <a name="see-also"></a>Siehe auch  
 [Änderungsnachverfolgung für Katalogsichten &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Nachverfolgen von Datenänderungen &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
