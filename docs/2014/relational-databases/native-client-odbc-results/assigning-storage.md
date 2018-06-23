---
title: Zuweisen von Speicher | Microsoft Docs
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
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb77a63cb3522d86b40742780e44a141dc0a6c15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148126"
---
# <a name="assigning-storage"></a>Zuweisen von Speicher
  Eine Anwendung kann vor oder nach der Ausführung einer SQL-Anweisung Speicher für Ergebnisse zuweisen. Wenn eine Anwendung die SQL-Anweisung zum ersten Mal vorbereitet oder ausführt, kann sie Informationen zum Resultset einholen, bevor sie Speicher für die Ergebnisse zuweist. Wenn das Resultset beispielsweise unbekannt ist, muss die Anwendung die Anzahl der Spalten abrufen, bevor sie diesen Speicher zuweisen kann.  
  
 Um Speicher für eine Spalte mit Daten zuzuordnen, eine Anwendung ruft [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)und übergibt sie:  
  
-   Den Datentyp, in den die Daten konvertiert werden sollen.  
  
-   Die Adresse eines Ausgabepuffers für die Daten.  
  
     Die Anwendung muss Speicher für diesen Puffer zuweisen, und der Puffer muss so groß sein, dass die Daten in dem Format, in das sie konvertiert werden sollen, darin Platz finden.  
  
-   Die Länge des Ausgabepuffers.  
  
     Dieser Wert wird ignoriert, wenn die zurückgegebenen Daten über eine feste Breite in C verfügen, z. B. eine ganze Zahl, reelle Zahl oder Datumsstruktur.  
  
-   Die Adresse eines Speicherpuffers, in den die Anzahl von Bytes verfügbarer Daten zurückgegeben werden soll.  
  
 Eine Anwendung kann auch Resultsetspalten an Arrays von Programmvariablen binden, um das Abrufen von Resultsetzeilen in Blöcken zu unterstützen. Es gibt zwei verschiedene Arten der Arraybindung:  
  
-   Die spaltenweise Bindung ist fertig gestellt, wenn jede Spalte an sein eigenes Array von Variablen gebunden wurde.  
  
     Die spaltenweise Bindung wird angegeben, durch den Aufruf [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) mit *Attribut* auf SQL_ATTR_ROW_BIND_TYPE festgelegt und *ValuePtr* auf SQL_BIND_BY_COLUMN festgelegt wird. Alle Arrays müssen über die gleiche Anzahl von Elementen verfügen.  
  
-   Die zeilenweise Bindung ist fertig gestellt, wenn alle Parameter in der SQL-Anweisung als Einheit an ein Array von Strukturen gebunden wurden, die die einzelnen Variablen für die Parameter enthalten.  
  
     Zeilenweise Bindung wird angegeben, indem **SQLSetStmtAttr** mit *Attribut* auf SQL_ATTR_ROW_BIND_TYPE festgelegt und *ValuePtr* legen Sie auf die Größe des Betriebs Struktur der Variablen, die das Ergebnis zu erhalten, werden die Resultsetspalten an.  
  
 Die Anwendung legt zudem SQL_ATTR_ROW_ARRAY_SIZE auf die Anzahl der Elemente im Spalten- oder Zeilenarray sowie SQL_ATTR_ROW_STATUS_PTR und SQL_ATTR_ROWS_FETCHED_PTR fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Verarbeiten von Ergebnissen &#40;ODBC&#41;](processing-results-odbc.md)  
  
  