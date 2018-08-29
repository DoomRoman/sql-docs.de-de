---
title: Sp_changereplicationserverpasswords (Transact-SQL) | Microsoft-Dokumentation
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
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 4ae1883006db7eaffe1e10ffcee2c36619f66c73
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43029961"
---
# <a name="spchangereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Kennwörter für die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Replikations-Agents auf Servern in einer Replikationstopologie Herstellen einer Verbindung verwendete Anmeldename. Normalerweise müssten Sie das Kennwort für jeden einzelnen Agent ändern, der auf dem Server ausgeführt wird, und zwar selbst dann, wenn alle Agents den gleichen Anmeldenamen oder das gleiche Konto verwenden. Diese gespeicherte Prozedur ermöglicht Ihnen die Änderung des Kennworts für alle Instanzen eines gegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamens oder Windows-Kontos, der bzw. das von allen auf einem Server ausgeführten Replikations-Agents verwendet wird. Die gespeicherte Prozedur wird auf jedem Server in der Replikationstopologie der master-Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changereplicationserverpasswords [ @login_type = ] login_type  
        , [ @login = ] 'login'   
        , [ @password = ] 'password'  
    [ , [ @server = ] 'server' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@login_type** =] *Login_type*  
 Der Authentifizierungstyp für die angegebenen Anmeldeinformationen. *LOGIN_TYPE* ist **Tinyint**, hat keinen Standardwert.  
  
 **1** = integrierte Windows-Authentifizierung  
  
 **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung  
  
 [ **@login** =] **"***Anmeldung***"**  
 Der Name des Windows-Kontos oder der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung, das bzw. die geändert wird. *Anmeldung* ist **nvarchar(257)**, hat keinen Standardwert  
  
 [ **@password** =] **"***Kennwort***"**  
 Das neue Kennwort gespeichert werden für den angegebenen *Anmeldung*. *Kennwort* ist **Sysname**, hat keinen Standardwert.  
  
> [!NOTE]  
>  Nachdem Sie ein Replikationskennwort geändert haben, müssen Sie jeden Agent, der dieses Kennwort verwendet, beenden und neu starten, damit die Änderung für diesen Agent in Kraft tritt.  
  
 [ **@server** =] **"***Server***"**  
 Die Serververbindung, für die das gespeicherte Kennwort geändert wird. *Server* ist **Sysname**, und kann einen der folgenden Werte:  
  
|value|Description|  
|-----------|-----------------|  
|**Verteiler**|Alle Agentverbindungen zum Verteiler|  
|**publisher**|Alle Agentverbindungen zum Verleger|  
|**subscriber**|Alle Agentverbindungen zum Abonnenten|  
|**%** (Standard)|Alle Agentverbindungen zu allen Servern in einer Replikationstopologie|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changereplicationserverpasswords** wird für alle Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_changereplicationserverpasswords**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern von Replikationssicherheitseinstellungen](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
