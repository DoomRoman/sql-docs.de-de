---
title: DROP COLUMN ENCRYPTION KEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP COLUMN ENCRYPTION
- DROP COLUMN ENCRYPTION KEY
- DROP_COLUMN_ENCRYPTION_TSQL
- DROP_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP COLUMN ENCRYPTION KEY statement
- column encryption key, drop
ms.assetid: 86415302-1383-4d36-9fc7-f780831a2d37
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f3a17a32fd9b44ea8c2d5fd2de4f9a77375cf227
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607808"
---
# <a name="drop-column-encryption-key-transact-sql"></a>DROP COLUMN ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Entfernt einen Spaltenverschlüsselungsschlüssel (Column Encryption Key, CEK) aus der Datenbank.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP COLUMN ENCRYPTION KEY key_name [;]  
```  
  
## <a name="arguments"></a>Argumente  
 *key_name*  
 Der Name des CEK, der aus der Datenbank entfernt werden soll.  
  
## <a name="remarks"></a>Remarks  
 CEKs können nicht entfernt werden, wenn sie verwendet werden, um eine Spalte in der Datenbank zu verschlüsseln. Alle Spalten, die den CEK verwenden, müssen zunächst entfernt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **ALTER ANY COLUMN ENCRYPTION KEY**-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-dropping-a-column-encryption-key"></a>A. Entfernen eines CEK  
 Im folgenden Beispiel wird ein CEK mit der Bezeichnung `MyCEK` entfernt.  
  
```  
DROP COLUMN ENCRYPTION KEY MyCEK;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Always Encrypted &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)  
  
  
