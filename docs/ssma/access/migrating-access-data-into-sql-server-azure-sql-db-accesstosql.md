---
title: Migrieren von Access-Daten in SQLServer – Azure SQL-Datenbank (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- bulk loading data
- data, loading into SQL Azure
- data, loading into SQL Server
- migrating databases, loading data
- migrating databases, options
- options, migrating data
- SQL Azure, migrating data into
- SQL Server, migrating data into
ms.assetid: f3b18af7-1af0-499d-a00d-a0af94895625
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ab3ce18b1b79951c76b34be3f90b2d8782ba64e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773823"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>Migrieren von Access-Daten in SQLServer – Azure SQL-Datenbank (AccessToSQL)
Nachdem Sie die Datenbankobjekte in erstellt haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie Daten aus den Zugriff auf migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
## <a name="setting-migration-options"></a>Festlegen von Migrationsoptionen für die  
Vor dem Migrieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, überprüfen die Projektoptionen für die Migration in die **Projekteinstellungen** Dialogfeld. In diesem Dialogfeld können Sie festlegen, die Batchgröße für die Migration, Tabellensperre, einschränkungsüberprüfung, Einfügung auslösen, Identität und Behandlung von null-Wert und wie Sie Datumsangaben verarbeiten, die von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bereich. Weitere Informationen finden Sie unter [Project Settings (Migration)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>Migrieren von Daten  
Migrieren von Daten ist ein Massenladen-Vorgang, der Zeilen von Daten in Verschiebt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Transaktionen. Die Anzahl der Zeilen in geladen werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure in jeder Transaktion in den projekteinstellungen konfiguriert ist.  
  
Migration Nachrichten sicher, dass im Ausgabebereich angezeigt wird. Ist dies nicht der Fall, in der **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**Zum Migrieren von Daten**  
  
1.  Stellen Sie sicher, dass Sie geladen haben, die Zugriff auf Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
2.  Wählen Sie im Metadaten-Explorer für den Zugriff die Objekte, die die Daten enthalten, die Sie migrieren möchten:  
  
    -   Wählen Sie das Kontrollkästchen neben dem Datenbanknamen, zum Migrieren von Daten für eine gesamte Datenbank.  
  
    -   Zum Migrieren von Daten aus einzelnen Tabellen die Datenbank, erweitern Sie dann **Tabellen**, und wählen Sie dann das Kontrollkästchen neben der Tabelle. Um Daten aus den einzelnen Tabellen zu unterdrücken, deaktivieren Sie das Kontrollkästchen.  
  
3.  Mit der rechten Maustaste **Datenbanken** und wählen Sie dann **Migrieren von Daten**.  
  
Sie können auch Daten außerhalb von SSMA mithilfe Migrieren der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Bcp** Befehlszeilen-Hilfsprogramm oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Weitere Informationen zu diesen Tools finden Sie unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Wenn Sie eine Access-Datenbank-Anwendungen, die Sie nach der Migration weiterhin verwenden möchten verfügen, verknüpfen Sie die Tabellen der Access-Datenbank, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellen. Weitere Informationen finden Sie unter [Verknüpfen von Access-Anwendungen mit SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Einstellung Konvertierung und Migrationsoptionen](setting-conversion-and-migration-options-accesstosql.md)  
  
