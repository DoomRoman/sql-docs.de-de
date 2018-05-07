---
title: Sysmail_delete_principalprofile_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6f1f7fc964f5be9e045614f7a49c7f5fec194537
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="sysmaildeleteprincipalprofilesp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt für einen Datenbankbenutzer oder eine Rolle die Berechtigung zum Verwenden eines öffentlichen oder privaten Datenbank-E-Mail-Profils.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@principal_id** =] *Principal_id*  
 Die ID des Datenbankbenutzers oder der Rolle in der **Msdb** Datenbank für die Zuordnung zu löschen. *principal_id* ist vom Datentyp **int**und hat den Standardwert NULL. Um ein privates Profil für ein öffentliches Profil festzulegen, geben Sie die Prinzipal-ID **0** oder den Prinzipalnamen **'public'**. Es muss entweder *principal_id* oder *principal_name* angegeben werden.  
  
 [ **@principal_name** =] **"***Principal_name***"**  
 Der Name des Datenbankbenutzers oder der Rolle in der **Msdb** Datenbank für die Zuordnung zu löschen. *principal_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Um ein privates Profil für ein öffentliches Profil festzulegen, geben Sie die Prinzipal-ID **0** oder den Prinzipalnamen **'public'**. Es muss entweder *principal_id* oder *principal_name* angegeben werden.  
  
 [ **@profile_id** =] *Profile_id*  
 Die ID des Profils für die Zuordnung, die gelöscht werden soll. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
 [ **@profile_name** =] **"***Profile_name***"**  
 Der Name des Profils für die Zuordnung, die gelöscht werden soll. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein öffentliches Profil in ein privates Profil umgewandelt werden, geben **'public'** für den Prinzipalnamen oder **0** Prinzipal-ID.  
  
 Gehen Sie vorsichtig vor, wenn Sie für einen Benutzer die Berechtigungen für das private Standardprofil entfernen oder das öffentliche Standardprofil entfernen. Wenn kein Standardprofil verfügbar ist, wird **Sp_send_dbmail** erfordert den Namen eines Profils als Argument. Aus diesem Grund Entfernen eines Standardprofils kann dazu führen, dass Aufrufe **Sp_send_dbmail** fehlschlägt. Weitere Informationen finden Sie unter [Sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 Die gespeicherte Prozedur **Sysmail_delete_principalprofile_sp** befindet sich in der **Msdb** Datenbank und im Besitz der **Dbo** Schema. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Zuordnung zwischen dem Profil **AdventureWorks Administrator** und den Anmeldenamen **ApplicationUser** in der **Msdb** Datenbank.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail Configuration Objects](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
