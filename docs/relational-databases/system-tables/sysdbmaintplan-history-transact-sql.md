---
title: Sysdbmaintplan_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 70afaf6e607f5c8455747a42429f815a6616a8a5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="sysdbmaintplanhistory-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|Von den Datenbankwartungsplänen erstellte Verlaufssequenz.|  
|**plan_id**|**uniqueidentifier**|ID des Datenbankwartungsplans.|  
|**plan_name**|**sysname**|Name des Datenbankwartungsplans.|  
|**database_name**|**sysname**|Der Name der Datenbank, die dem Datenbank-Wartungsplan zugeordnet ist.|  
|**server_name**|**sysname**|Systemname.|  
|**Aktivität**|**nvarchar(128)**|Die vom Datenbankwartungsplan durchgeführte Aktivität (z. B. Transaktionsprotokoll sichern usw.).|  
|**succeeded**|**bit**|**0** = Erfolgreich **1** = Fehler|  
|**end_time**|**datetime**|Zeitpunkt, an dem die Aktion abgeschlossen wurde.|  
|**duration**|**int**|Erforderliche Zeitspanne, um die Aktion im Rahmen des Datenbankwartungsplans abzuschließen.|  
|**start_time**|**datetime**|Zeitpunkt, an dem die Aktion gestartet wurde.|  
|**error_number**|**int**|Fehlernummer, die bei einem Fehler gemeldet wird.|  
|**Nachricht**|**nvarchar(512)**|Von **sqlmaint**generierte Meldung.|  
  
  
