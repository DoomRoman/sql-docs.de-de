---
title: Erstellen von SQL-Anweisungen für Cursor | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16eefd4b60bc3c6c23cec3e628d6e7e8604bb316
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057172"
---
# <a name="constructing-sql-statements-for-cursors"></a>Erstellen von SQL-Anweisungen für Cursor
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet Servercursor, die in der ODBC-Spezifikation definierte Cursorfunktionalität zu implementieren. Eine ODBC-Anwendung kontrolliert das Cursorverhalten mit [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) auf andere Anweisungsattribute festlegt. Nachfolgend sind die Attribute und ihre Standardwerte aufgeführt.  
  
|attribute|Default|  
|---------------|-------------|  
|SQL_ATTR_CONCURRENCY|SQL_CONCUR_READ_ONLY|  
|SQL_ATTR_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE|SQL_NONSCROLLABLE|  
|SQL_ATTR_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_ATTR_ROW_ARRAY_SIZE|1|  
  
 Wenn diese Optionen auf ihre Standardwerte festgelegt sind eine SQL­Anweisung ausgeführt wird, zum Zeitpunkt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet einen Servercursor zur Implementierung des Resultsets kein; stattdessen wird ein Standardresultset. Wenn eine dieser Optionen nicht auf ihre Standardeinstellung zum Zeitpunkt geändert werden eine SQL­Anweisung ausgeführt wird, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber versucht, einen Servercursor verwenden, um das Resultset zu implementieren.  
  
 Standardresultsets unterstützen alle [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen. Es gibt keine Einschränkungen hinsichtlich der Arten von SQL-Anweisungen, die bei Verwendung eines Standardresultsets ausgeführt werden können.  
  
 Nicht alle [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen werden von Servercursorn unterstützt. Servercursor unterstützen keine SQL-Anweisungen, die mehrere Resultsets generieren.  
  
 Die folgenden Typen von Anweisungen werden von Serversursorn nicht unterstützt:  
  
-   Batches  
  
     Aus zwei oder mehr einzelnen SQL SELECT-Anweisungen erstellte SQL-Anweisungen, Beispiel.:  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   Gespeicherte Prozeduren mit mehreren SELECT-Anweisungen  
  
     SQL-Anweisungen, die eine gespeicherte Prozedur ausführen, die mehr als eine SELECT-Anweisung enthält Hierzu gehören auch SELECT-Anweisungen, mit denen Parameter- oder Variablenwerte abgerufen werden.  
  
-   Schlüsselwörter  
  
     SQL-Anweisungen, die die Schlüsselwörter FOR BROWSE oder INTO enthalten.  
  
 Wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine SQL-Anweisung ausgeführt wird, die eine dieser Bedingungen erfüllt, dann wird der Servercursor implizit in ein Standardresultset konvertiert. Nach dem **SQLExecDirect** oder **SQLExecute** gibt SQL_SUCCESS_WITH_INFO zurück, der Cursor Attribute wieder auf ihre Standardeinstellungen zurückgesetzt werden werden.  
  
 SQL-Anweisungen, die nicht in die oben genannten Kategorien passen, können mit beliebigen Anweisungsattributeinstelllungen ausgeführt werden. Sie funktionieren sowohl mit einem Standardresultset als auch einem Servercursor gleich gut.  
  
## <a name="errors"></a>Fehler  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 und höher führt der Versuch, eine Anweisung auszuführen, die mehrere Resultsets erzeugt, zur Ausgabe von SQL_SUCCESS_WITH INFO und der folgenden Meldung:  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 ODBC-Anwendungen, die diese Nachricht empfängt erreichen [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) um die aktuellen cursoreinstellungen zu bestimmen.  
  
 Der Versuch, bei Verwendung von Servercursorn eine Prozedur mit mehreren SELECT-Anweisungen auszuführen, erzeugt folgenden Fehler:  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 Der Versuch, bei Verwendung von Servercursorn einen Batch mit mehreren SELECT-Anweisungen auszuführen, erzeugt folgenden Fehler:  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 ODBC-Anwendungen, die diese Fehler erhalten, müssen alle Cursoranweisungsattribute auf die jeweilige Standardeinstellung zurücksetzen, bevor sie die Anweisung auszuführen versuchen.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  