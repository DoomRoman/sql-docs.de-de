---
title: Löschen einer Datenquelle (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c914989c04226991f0df573b60bea0b69ff15802
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703211"
---
# <a name="configuring-the-sql-server-odbc-driver---delete-a-data-source"></a>Konfigurieren des SQL Server-ODBC-Treibers - Löschen einer Datenquelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Vor der Verwendung von ODBC-Anwendungen mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher müssen Sie wissen, wie so aktualisieren Sie die Version der gespeicherten Prozeduren für Kataloginformationen in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und hinzufügen, löschen und Testen von Datenquellen.  
  
  Löschen einer Datenquelle können Sie mithilfe des ODBC-Administrators, programmgesteuert (mit [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)), oder durch Löschen einer Datei (bei einem dateiquellennamen).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>So löschen Sie eine Datenquelle mit dem ODBC-Administrator  
  
1.  In **Systemsteuerung**öffnen **Verwaltung**, und doppelklicken Sie dann auf entweder **ODBC-Datenquellen (64-Bit)** oder **ODBC-Datenquellen (32-Bit)**. Stattdessen können Sie auch odbcad32.exe über die Eingabeaufforderung ausführen:  
  
2.  Klicken Sie auf die Registerkarte **Benutzer-DSN**, **System-DSN**oder **Datei-DSN** .  
  
3.  Wählen Sie die zu löschende Datenquelle.  
  
4.  Klicken Sie auf **Entfernen**, und bestätigen Sie dann das Löschen.  
  
## <a name="example"></a>Beispiel  
 Um eine Datenquelle programmgesteuert zu löschen, rufen [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) entweder mit ODBC_REMOVE_DSN oder mit ODBC_REMOVE_SYS_DSN als zweiten Parameter.  
  
 Im folgenden Beispiel wird gezeigt, wie Sie eine Datenquelle programmgesteuert löschen können.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include \<windows.h>  
#include \<odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen einer Datenquelle &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-add-a-data-source.md)  
  
  
