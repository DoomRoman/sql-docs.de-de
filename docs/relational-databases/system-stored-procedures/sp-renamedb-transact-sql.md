---
title: Sp_renamedb (Transact-SQL) | Microsoft-Dokumentation
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
- sp_renamedb
- sp_renamedb_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_renamedb
ms.assetid: 7dd9d4ff-20e1-4857-9a8e-a5bff767cf76
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3e1763b46d3d98616685878b27f60d76b398ab49
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984187"
---
# <a name="sprenamedb-transact-sql"></a>sp_renamedb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert den Namen einer Datenbank.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen ALTER DATABASE MODIFY NAME. Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_renamedb [ @dbname = ] 'old_name' , [ @newname = ] 'new_name'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@dbname=**] **"***Old_name***"**  
 Der aktuelle Name der Datenbank. *Old_name* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@newname=**] **"***New_name***"**  
 Ist der neue Name der Datenbank. *New_name* müssen den Regeln für Bezeichner entsprechen. *New_name* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Sysadmin** oder **Dbcreator** festen Serverrollen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die `Accounting`-Datenbank erstellt und der Name anschließend in `Financial` geändert. Danach wird eine Abfrage der `sys.databases`-Katalogsicht ausgeführt, um den Namen der Datenbank zu überprüfen.  
  
```  
USE master;  
GO  
CREATE DATABASE Accounting;  
GO  
EXEC sp_renamedb N'Accounting', N'Financial';  
GO  
SELECT name, database_id, modified_date  
FROM sys.databases  
WHERE name = N'Financial';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_changedbowner &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
