---
title: MSpeer_originatorid_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54dfad713a9955791cc786bb89ef8d61cac2b3ca
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103828"
---
# <a name="mspeeroriginatoridhistory-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Absender-ID, die in der Topologie definiert wurde. Dies beinhaltet IDs für Knoten, die nicht mehr aktiv sind. Die Tabelle wird verwendet, wenn Sie einen neuen Knoten für die Konflikterkennung konfigurieren, um sicherzustellen, dass die angegebene Absender-ID noch nicht verwendet wurde. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert. Weitere Informationen zur konflikterkennung finden Sie unter [Conflict Detection in Peer-zu-Peer-Replikation](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|Veröffentlichung, für welche die Absender-ID angegeben wurde|  
|originator_id|**int**|Nummer, die jeden Knoten in der Topologie zum Zweck der Konflikterkennung kennzeichnet|  
|originator_node|**sysname**|Serverinstanz, für welche die Absender-ID angegeben wurde|  
|originator_db|**sysname**|Veröffentlichungsdatenbank, für welche die Absender-ID angegeben wurde|  
|originator_db_version|**int**|Kennzeichnet die Versionsnummer der ursprünglichen Datenbank.|  
|originator_version|**int**|Kennzeichnet die Versionsnummer des Verlegers|  
|inserted_date|**datetime**|Datum und Zeit, zu der die Zeile für die Absender-ID in diese Tabelle eingefügt wurde|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
