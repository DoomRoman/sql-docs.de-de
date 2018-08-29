---
title: Sp_replmonitorhelppublicationthresholds (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
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
- sp_replmonitorhelppublicationthresholds
- sp_replmonitorhelppublicationthresholds_TSQL
helpviewer_keywords:
- sp_replmonitorhelppublicationthresholds
ms.assetid: d6b1aa4b-3369-4255-a892-c0e5cc9cb693
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d87de8d4ab74bc5c9d776b9d08e9e0680e2530cd
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032238"
---
# <a name="spreplmonitorhelppublicationthresholds-transact-sql"></a>sp_replmonitorhelppublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die für eine überwachte Veröffentlichung festgelegten Schwellenwertmetriken zurück. Diese gespeicherte Prozedur, die zum Überwachen der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelppublicationthresholds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publisher**=] **"***Verleger***"**  
 Der Name des Verlegers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@publisher_db**=] **"***Publisher_db***"**  
 Der Name der veröffentlichten Datenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@publication**=] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@publication_type**=] *Publication_type*  
 Der Typ der Veröffentlichung. *Publication_type* ist **Int**, und kann einen der folgenden Werte sein.  
  
|value|Description|  
|-----------|-----------------|  
|**0**|Transaktionsveröffentlichung.|  
|**1**|Momentaufnahmeveröffentlichung.|  
|**2**|Mergeveröffentlichung.|  
|NULL (Standard)|Die Replikation versucht, den Veröffentlichungstyp zu ermitteln.|  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|ID der Replikationsleistungsmetrik. Folgende Werte sind möglich.<br /><br /> **1expiration** -überwacht den bevorstehenden Ablauf von Abonnements für transaktionsveröffentlichungen.<br /><br /> **2latency** -überwacht die Leistung von Abonnements für transaktionsveröffentlichungen.<br /><br /> **4mergeexpiration** -überwacht den bevorstehenden Ablauf von Abonnements für mergeveröffentlichungen.<br /><br /> **5mergeslowrunduration** -überwacht die Dauer von mergesynchronisierungen über Verbindungen mit niedriger Bandbreite (DFÜ).<br /><br /> **6mergefastrunduration** -überwacht die Dauer von mergesynchronisierungen über Verbindungen mit hoher Bandbreite (LAN).<br /><br /> **7mergefastrunspeed** -überwacht die synchronisierungsgeschwindigkeit von mergesynchronisierungen über Verbindungen mit hoher Bandbreite (LAN).<br /><br /> **8mergeslowrunspeed** -überwacht die synchronisierungsgeschwindigkeit von mergesynchronisierungen über Verbindungen mit niedriger Bandbreite (DFÜ).|  
|**title**|**sysname**|Der Name der Replikationsleistungsmetrik.|  
|**Wert**|**int**|Der Schwellenwert der Leistungsmetrik.|  
|**shouldalert**|**bit**|Ist eine Warnung generiert werden soll, wenn die Metrik den definierten Schwellenwert für diese Veröffentlichung überschreitet. der Wert **1** gibt an, dass eine Warnung ausgelöst werden soll.|  
|**IsEnabled**|**bit**|Ist, wenn die Überwachung für die replikationsleistungsmetrik für diese Veröffentlichung aktiviert ist. der Wert **1** gibt an, dass die Überwachung aktiviert ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replmonitorhelppublicationthresholds** wird für alle Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Db_owner** oder **Replmonitor** -Datenbankrolle in der Verteilungsdatenbank kann ausführen **Sp_replmonitorhelppublicationthresholds**.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
