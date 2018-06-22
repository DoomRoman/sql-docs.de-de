---
title: Umbenennen von Tabellen (Datenbank-Engine) | Microsoft-Dokumentation
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
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 258997de3639b208c8b977a0d245780fdfa889f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149020"
---
# <a name="rename-tables-database-engine"></a>Umbenennen von Tabellen (Datenbank-Engine)
  Sie können in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] eine Tabelle mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]umbenennen.  
  
> [!CAUTION]  
>  Das Umbenennen einer Tabelle muss sorgfältig überlegt sein. Alle Abfragen, Sichten, benutzerdefinierten Funktionen, gespeicherten Prozeduren und Programme, die auf diese Tabelle verweisen, werden durch die Namensänderung ungültig.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So benennen Sie eine Tabelle um mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Durch Umbenennen einer Tabelle werden die Verweise auf diese Tabelle nicht automatisch umbenannt. Sie müssen Objekte, die auf die umbenannte Tabelle verweisen, manuell ändern. Wenn Sie z. B. eine Tabelle umbenennen und in einem Trigger auf diese Tabelle verwiesen wird, müssen Sie den Trigger ändern, sodass er den neuen Tabellennamen wiedergibt. Verwenden Sie [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) für eine Auflistung der Abhängigkeiten von der Tabelle, bevor Sie sie umbenennen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-rename-a-table"></a>So benennen Sie eine Tabelle um  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, die umbenannt werden soll, und wählen Sie im Kontextmenü **Entwerfen** aus.  
  
2.  Wählen Sie im Menü **Ansicht** die Option **Eigenschaften**aus.  
  
3.  Geben Sie im Fenster **Eigenschaften** im Feld **Name** einen neuen Namen für die Tabelle ein.  
  
4.  Wenn Sie diesen Vorgang abbrechen möchten, drücken Sie die ESC-TASTE, bevor Sie das Feld verlassen.  
  
5.  Klicken Sie im Menü **Datei** auf **Speichern** > *Tabellenname*.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-rename-a-table"></a>So benennen Sie eine Tabelle um  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Im folgenden Beispiel wird die `SalesTerritory` -Tabelle im Schema `SalesTerr` in `Sales` umbenannt. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 Weitere Beispiele finden Sie unter [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).  
  
  
