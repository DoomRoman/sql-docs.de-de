---
title: MSSQLSERVER_2020 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2020 (Database Engine error)
ms.assetid: 4a8bf90f-a083-4c53-84f0-d23c711c8081
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e54a04cc9d787ae4d6d4545bbc5d9661bbba213d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192770"
---
# <a name="mssqlserver2020"></a>MSSQLSERVER_2020
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2020|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Die für die Entität "% * ls" gemeldeten Abhängigkeiten beinhalten keine Verweise auf Spalten. Dies hängt entweder damit zusammen, dass die Entität auf ein Objekt verweist, das nicht vorhanden ist, oder mit einem Fehler in einer oder mehreren Anweisungen in der Entität.  Bevor Sie die Abfrage erneut ausführen, stellen Sie sicher, dass die Entität keine Fehler enthält und dass alle Objekte, auf die die Entität verweist, vorhanden sind.|  
  
## <a name="explanation"></a>Erklärung  
 Die Systemfunktion **sys.dm_sql_referenced_entities** meldet jede Abhängigkeit auf Spaltenebene für schemagebundene Verweise. Die Funktion meldet z. B. alle Abhängigkeiten auf Spaltenebene für eine indizierte Sicht, da für eine indizierte Sicht Schemabindung erforderlich ist. Wenn die Entität, auf die verwiesen wird, jedoch nicht schemagebunden ist, werden Spaltenabhängigkeiten nur gemeldet, wenn alle Anweisungen, in denen auf die Spalten verwiesen wird, gebunden werden können. Anweisungen können nur erfolgreich gebunden werden, wenn alle Objekte vorhanden sind, wenn die Anweisungen analysiert werden. Wenn eine in der Entität definierte Anweisung nicht gebunden werden kann, werden Spaltenabhängigkeiten nicht gemeldet, und die Spalte **referenced_minor_id** gibt 0 zurück. Wenn Spaltenabhängigkeiten nicht aufgelöst werden können, wird Fehler 2020 ausgelöst. Dieser Fehler verhindert nicht, dass die Abfrage Abhängigkeiten auf Objektebene zurückgibt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Korrigieren Sie alle in der Meldung vor Fehler 2020 identifizierten Fehler. Im folgenden Codebeispiel wird z. B. die Sicht `Production.ApprovedDocuments` für die Spalten `Title`, `ChangeNumber` und `Status` in der Tabelle `Production.Document` definiert. Die Systemfunktion **sys.dm_sql_referenced_entities** wird für die Objekte und Spalten abgefragt, von denen die `ApprovedDocuments`-Sicht abhängig ist. Da die Sicht nicht mit der WITH SCHEMA_BINDING-Klausel erstellt wird, können die Spalten, auf die in der Sicht verwiesen wird, in der Tabelle geändert werden, auf die verwiesen wird. Im Beispiel wird die Spalte `ChangeNumber` in der Tabelle `Production.Document` geändert, indem sie in `TrackingNumber` umbenannt wird. Die Katalogsicht wird erneut für die `ApprovedDocuments`-Sicht abgefragt. Es ist jedoch keine Bindung an alle in der Sicht definierten Spalten möglich. Die Fehler 207 und 2020 werden zurückgegeben und geben das Problem an. Um das Problem zu beheben, muss die Sicht geändert so werden, dass der neue Name der Spalte angegeben wird.  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `CREATE VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title, ChangeNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 `EXEC sp_rename 'Production.Document.ChangeNumber', 'TrackingNumber', 'COLUMN';`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 Die Abfrage gibt die folgenden Fehlermeldungen zurück:  
  
 `Msg 207, Level 16, State 1, Procedure ApprovedDocuments, Line 3`  
  
 `Invalid column name 'ChangeNumber'.`  
  
 `Msg 2020, Level 16, State 1, Line 1`  
  
 `The dependencies reported for entity`  
  
 `"Production.ApprovedDocuments" do not include references to`  
  
 `columns. This is either because the entity references an`  
  
 `object that does not exist or because of an error in one or`  
  
 `more statements in the entity. Before rerunning the query,`  
  
 `ensure that there are no errors in the entity and that all`  
  
 `objects referenced by the entity exist.`  
  
 Im folgenden Beispiel wird der Spaltenname in der Sicht korrigiert.  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `ALTER VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title,TrackingNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
  
