---
title: cdc_jobs (Transact-SQL) | Microsoft-Dokumentation
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
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 55bbf5390a79f762c7e247c65c38e58a4bdb35de
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103488"
---
# <a name="dbocdcjobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert die Change Data Capture-Konfigurationsparameter für Aufzeichnungs- und Cleanupaufträge. Diese Tabelle befindet sich in **Msdb**.  
  
 
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID der Datenbank, in der der Auftrag ausgeführt wird.|  
|**Der Standardwert ist**|**nvarchar(20)**|Typ des Auftrags, entweder 'capture' oder 'cleanup'.|  
|**job_id**|**uniqueidentifier**|Dem Auftrag zugeordnete eindeutige ID.|  
|**maxtrans**|**int**|Die maximale Anzahl der in jedem Scanzyklus zu verarbeitenden Transaktionen.<br /><br /> **Maxtrans** ist nur für aufzeichnungsaufträge gültig.|  
|**maxscans**|**int**|Die maximale Anzahl der scanzyklen, ausführen, um alle Zeilen aus dem Protokoll zu extrahieren.<br /><br /> **Maxscans** ist nur für aufzeichnungsaufträge gültig.|  
|**fortlaufende**|**bit**|Flag, das angibt, ob der Aufzeichnungsauftrag fortlaufend (1) oder einmalig (0) ausgeführt werden soll. Weitere Informationen finden Sie unter [sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **fortlaufende** ist nur für aufzeichnungsaufträge gültig.|  
|**PollingInterval**|**bigint**|Anzahl der Sekunden zwischen Protokollscanzyklen.<br /><br /> **PollingInterval** ist nur für aufzeichnungsaufträge gültig.|  
|**Beibehaltungsdauer**|**bigint**|Anzahl der Minuten, die Änderungszeilen in Änderungstabellen beibehalten werden sollen.<br /><br /> **Aufbewahrung** ist nur für cleanupaufträge gültig.|  
|**threshold**|**bigint**|Die maximale Anzahl von Einträgen für Löschvorgänge, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können.|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [sp_cdc_change_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [sp_cdc_help_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [sp_cdc_drop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
