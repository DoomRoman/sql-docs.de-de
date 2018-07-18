---
title: Sp_syscollector_run_collection_set (Transact-SQL) | Microsoft Docs
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
- sp_syscollector_run_collection_set_TSQL
- sp_syscollector_run_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_run_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 7bbaee48-dfc7-45c0-b11f-c636b6a7e720
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 599cc4a9f8603b8248c7241cbb2ba68055e6fb55
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "33260163"
---
# <a name="spsyscollectorruncollectionset-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Startet einen Sammlungssatz, wenn der Sammler bereits aktiviert ist und der Sammlungssatz für den Auflistmodus ohne Zwischenspeicherung konfiguriert ist.  
  
> [!NOTE]  
>  Bei dieser Prozedur tritt ein Fehler auf, wenn sie für einen Sammlungssatz ausgeführt wird, der für den Auflistmodus mit Zwischenspeicherung konfiguriert ist.  
  
 sp_syscollector_run_collection_set ermöglicht dem Benutzer die bedarfsgesteuerte Aufnahme von Datenmomentaufnahmen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_run_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Argumente  
 [  **@collection_set_id =** ] *Collection_set_id*  
 Der eindeutige lokale Bezeichner für den Sammlungssatz. *Collection_set_id* ist **Int** und muss einen Wert aufweisen, wenn *Namen* ist NULL.  
  
 [ **@name =** ] **'***name***'**  
 Ist der Name des Sammlungssatzes. *Namen* ist **Sysname** und muss einen Wert aufweisen, wenn *Collection_set_id* ist NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Entweder *Collection_set_id* oder *Namen* muss über einen Wert verfügen, können nicht beide NULL sein.  
  
 Diese Prozedur startet die Sammlungs- und Uploadaufträge für den angegebenen Sammlungssatz und startet umgehend den Auftrag des Sammlungs-Agent aus, wenn der Sammlungssatz verfügt über seine **@collection_mode** ohne Zwischenspeicherung (1) festgelegt. Weitere Informationen finden Sie unter [Sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 sp_sycollector_run_collection_set kann auch verwendet werden, um einen Sammlungssatz auszuführen, der über keinen Zeitplan verfügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Dc_operator** (mit EXECUTE-Berechtigung) festen Datenbankrolle "" zum Ausführen dieser Prozedur.  
  
## <a name="example"></a>Beispiel  
 Starten Sie einen Sammlungssatz unter Verwendung des zugehörigen Bezeichners.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_run_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
