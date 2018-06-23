---
title: Hinzufügen einer Datenquelle (ODBC) | Microsoft Docs
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
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4bfc1030cba65196858d05e3c57230b4930b2b21
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694471"
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>Konfigurieren des SQL Server-ODBC-Treibers - Hinzufügen einer Datenquelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Vor der Verwendung von ODBC-Anwendungen mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher müssen Sie wissen, wie so aktualisieren Sie die Version der gespeicherten Prozeduren für Kataloginformationen in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und hinzufügen, löschen und Testen von Datenquellen.  
  
  Hinzufügen einer Datenquelle können Sie mithilfe des ODBC-Administrators, programmgesteuert (mit [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)), oder indem Sie eine Datei erstellen.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>So fügen Sie eine Datenquelle mit dem ODBC-Administrator hinzu  
  
1.  Aus der **Systemsteuerung**, Zugriff **Verwaltung** , und klicken Sie dann entweder **ODBC-Datenquellen (64-Bit)** oder **ODBC-Datenquellen (32-Bit)**. Alternativ können Sie odbcad32.exe aufrufen.  
  
2.  Klicken Sie auf die Registerkarte **Benutzer-DSN**, **System-DSN**oder **Datei-DSN** , und klicken Sie dann auf **Hinzufügen**.  
  
3.  Klicken Sie auf **SQL Server**und dann auf **Fertig stellen**.  
  
4.  Führen Sie die Schritte in der **erstellen Sie eine neue Datenquelle mit SQL Server** Assistenten.  
  
### <a name="to-add-a-data-source-programmatically"></a>So fügen Sie eine Datenquellen programmgesteuert hinzu  
  
1.  Rufen Sie [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) mit auf entweder ODBC_ADD_DSN oder ODBC_ADD_SYS_DSN festgelegtem zweiten Parameter.  
  
### <a name="to-add-a-file-data-source"></a>So fügen Sie eine Dateidatenquelle hinzu  
  
1.  Rufen Sie [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) mit einem SAVEFILE = File_name-Parameter in der Verbindungszeichenfolge. Wenn die Verbindung erfolgreich ist, erstellt der ODBC-Treiber eine Dateidatenquelle mit den Verbindungsparametern an dem Speicherort, auf den der SAVEFILE-Parameter zeigt.  
  
## <a name="see-also"></a>Siehe auch  
[Löschen einer Datenquelle &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
