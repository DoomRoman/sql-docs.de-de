---
title: Sp_get_distributor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 088b2d2c6e334d48fae3e9257f76c5fd8129c15d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021289"
---
# <a name="spgetdistributor-transact-sql"></a>sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Bestimmt, ob ein Verteiler auf einem Server installiert ist. Diese gespeicherte Prozedur wird auf dem Computer, auf dem nach dem Verteiler gesucht wird, für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**installiert**|**int**|**0** = Nein; **1** = Ja|  
|**Verteilungsserver**|**sysname**|Name des Verteilerservers|  
|**Distribution-Datenbank installiert**|**int**|**0** = Nein; **1** = Ja|  
|**Verteilungsverleger ist**|**int**|**0** = Nein; **1** = Ja|  
|**hat Remoteverteilungsverleger**|**int**|**0** = Nein; **1** = Ja|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_get_distributor** dient in erster Linie durch die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer kann ausführen **Sp_get_distributor**. Ein nicht-NULL-Resultset wird zurückgegeben, wenn diese gespeicherte Prozedur wird ausgeführt, von einem Mitglied der **Db_owner** oder **Replmonitor** festen Datenbankrollen für die Verteilungsdatenbank oder die Mitglieder der  **Db_owner** -Datenbankrolle in mindestens einer veröffentlichten Datenbank. Ein nicht-NULL-Resultset wird auch zurückgegeben, wenn diese gespeicherte Prozedur von Benutzern in der veröffentlichungszugriffsliste (PAL), mindestens ausgeführt wird einer veröffentlichten Datenbank oder in der PAL der Verteilungsdatenbank für einen nicht - SQL Server-Verleger, können auch ausführen **sp _get_distributor**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Informationsskript für Verleger und Verteiler](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
