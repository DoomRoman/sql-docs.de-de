---
title: Sys. fn_cdc_get_column_ordinal (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_get_column_ordinal
- fn_cdc_get_column_ordinal_TSQL
- fn_cdc_get_column_ordinal
- sys.fn_cdc_get_column_ordinal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_column_ordinal
- sys.fn_cdc_get_column_ordinal
ms.assetid: 4bb21a57-2b94-4208-8bdf-6a3e2681d881
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b82aac8f856c1e057f389ac0af7d06dfee549fa5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624208"
---
# <a name="sysfncdcgetcolumnordinal-transact-sql"></a>sys.fn_cdc_get_column_ordinal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Spaltenordnungszahl angegebene Spalte, wie er angezeigt, in wird der [Änderungstabelle](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) der angegebenen Aufzeichnungsinstanz zugeordnet.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_cdc_get_column_ordinal ( 'capture_instance','column_name')  
```  
  
## <a name="arguments"></a>Argumente  
 **"** *Capture_instance* **"**  
 Der Name der Aufzeichnungsinstanz, in der die angegebene Spalte als aufgezeichnete Spalte identifiziert wird. *Capture_instance* ist **Sysname**.  
  
 **"** *Column_name* **"**  
 Die Spalte, über die berichtet werden soll. *Column_name* ist **Sysname**.  
  
## <a name="return-type"></a>Rückgabetyp  
 **int**  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion dient zum Identifizieren der Ordnungsposition einer in der Change Data Capture-Updatemaske aufgezeichneten Spalte. Sie dient hauptsächlich in Verbindung mit der Funktion [Sys. fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md) Informationen aus der updatemaske zu extrahieren, bei der Abfrage von Änderungsdaten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die SELECT-Berechtigung für alle aufgezeichneten Spalten der Quelltabelle. Wenn für die Aufzeichnungsinstanz eine Datenbankrolle für die Change Data Capture-Komponente angegeben ist, erfordert dies ebenfalls die Mitgliedschaft in der entsprechenden Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird für die Aufzeichnungsinstanz `VacationHours` die Ordnungsposition der `HumanResources_Employee`-Spalte in der Updatemaske abgerufen. Der Wert wird daraufhin für den Aufruf von `sys.fn_cdc_is_bit_set` verwendet, um Informationen aus der zurückgegebenen Updatemaske zu extrahieren.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10),  @VacationHoursOrdinal int;  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SET @VacationHoursOrdinal = sys.fn_cdc_get_column_ordinal   
    ( 'HumanResources_Employee','VacationHours');  
SELECT *, sys.fn_cdc_is_bit_set(@VacationHoursOrdinal,  
    __$update_mask) as 'VacationHours'  
FROM cdc.fn_cdc_get_net_changes_HumanResources_Employee  
    ( @from_lsn, @to_lsn, 'all with mask');  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Change Data Capture-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)   
 [Über Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)   
 [sys.sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [sys.sp_cdc_get_captured_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)   
 [sys.fn_cdc_is_bit_set &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md)  
  
  
