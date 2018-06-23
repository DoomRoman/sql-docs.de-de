---
title: Löschen einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database removal [SQL Server], SQL Server Management Studio
- removing databases
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- database removal [SQL Server]
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 73b61cf660cdc0a7a56f84c4fd86cf2d18f7f2a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163349"
---
# <a name="delete-a-database"></a>Löschen einer Datenbank
  In diesem Thema wird beschrieben, wie eine benutzerdefinierte Datenbank unter [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]gelöscht wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So löschen Sie eine Datenbank mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Löschen einer Datenbank](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Systemdatenbanken können nicht gelöscht werden.  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Löschen Sie alle Datenbankmomentaufnahmen, die in der Datenbank vorhanden sind. Weitere Informationen finden Sie unter [Löschen einer Datenbank-Momentaufnahme &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).  
  
-   Wenn für die Datenbank der Protokollversand konfiguriert ist, entfernen Sie diesen.  
  
-   Wenn die Datenbank für die Transaktionsreplikation oder für die Mergereplikation veröffentlicht ist bzw. Abonnent der Mergereplikation ist, entfernen Sie die Replikation aus der Datenbank.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Ziehen Sie in Betracht, eine vollständige Sicherung der Datenbank vorzunehmen. Eine gelöschte Datenbank kann nur neu erstellt werden, indem eine Sicherungskopie wiederhergestellt wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Für die Ausführung von DROP DATABASE benötigt ein Benutzer zumindest die CONTROL-Berechtigung für die Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-database"></a>So löschen Sie eine Datenbank  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung zu einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, klicken Sie mit der rechten Maustaste auf die zu löschende Datenbank, und klicken Sie dann auf **Löschen**.  
  
3.  Bestätigen Sie, dass die richtige Datenbank ausgewählt ist, und klicken Sie dann auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-database"></a>So löschen Sie eine Datenbank  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel werden die Datenbanken `Sales` und `NewSales` entfernt.  
  
```tsql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="FollowUp"></a> Nachverfolgung: Nach dem Löschen einer Datenbank  
 Sichern Sie die **master** -Datenbank. Wenn die **master** -Datenbank wiederhergestellt werden muss, können Fehlermeldungen auftreten, falls in den Systemkatalogsichten weiterhin Verweise auf Datenbanken bestehen, die seit der letzten Sicherung der **master** -Datenbank gelöscht wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
