---
title: "' sysarticleupdates ' (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sysarticleupdates_TSQL
- sysarticleupdates
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticleupdates system table
ms.assetid: 11a53bcd-a215-4d0b-9db8-233981d3ef5d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6a6617adf3ef8aca68b0876d62eaeda5d953b3a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47665968"
---
# <a name="sysarticleupdates-transact-sql"></a>sysarticleupdates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden Artikel, der sofort aktualisierte Abonnements unterstützt. Diese Tabelle wird in der replizierten Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Die Identity-Spalte, die eine eindeutige ID für den Artikel bereitstellt.|  
|**pubid**|**int**|Die ID der Veröffentlichung, zu der der Artikel gehört.|  
|**sync_ins_proc**|**int**|Die ID der gespeicherten Prozedur, die synchrone Einfügetransaktionen verarbeitet.|  
|**sync_upd_proc**|**int**|Die ID der gespeicherten Prozedur, die synchrone Updatetransaktionen verarbeitet.|  
|**sync_del_proc**|**int**|Die ID der gespeicherten Prozedur, die synchrone Löschtransaktionen verarbeitet.|  
|**autogen**|**bit**|Zeigt an, dass gespeicherte Prozeduren automatisch generiert werden:<br /><br /> **0** = false, nicht automatisch.<br /><br /> **1** = true, automatisch.|  
|**sync_upd_trig**|**int**|Die ID des Triggers für die automatische Versionsverwaltung für die Artikeltabelle.|  
|**conflict_tableid**|**int**|Die ID für die Konflikttabelle.|  
|**ins_conflict_proc**|**int**|Die ID der Prozedur verwendet, um zum Schreiben des Konflikts das **Conflict_table**.|  
|**identity_support**|**bit**|Gibt an, ob die automatische Behandlung des Identitätsbereichs aktiviert ist, wenn das verzögerte Aktualisieren über eine Warteschlange verwendet wird. **0** bedeutet, dass keine identitätsbereichsunterstützung vorhanden ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
