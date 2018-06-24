---
title: Verwenden der Rowsetbindung (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2ef6f3651cb1cb1c80247f5853b4d4bd05bc13fc
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694441"
---
# <a name="use-rowset-binding-odbc"></a>Verwenden der Rowsetbindung (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-use-column-wise-binding"></a>So verwenden Sie spaltenbezogene Bindungen  
  
1.  Gehen Sie für jede gebundene Spalte wie folgt vor:  
  
    -   Weisen Sie ein Array von R (oder mehr) Spaltenpuffern zum Speichern von Datenwerten zu, wobei R die Anzahl der Zeilen im Rowset ist.  
  
    -   Weisen Sie optional ein Array von R (oder mehr) Spaltenpuffern zum Speichern von Datenlängen zu.  
  
    -   Rufen Sie [SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md) auf die Spalte Datenwert und die datenlängenarrays an die Spalte des Rowsets zu binden.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) um die folgenden Attribute festzulegen:  
  
    -   Stellen Sie SQL_ATTR_ROW_ARRAY_SIZE auf die Anzahl der Zeilen im Rowset ein (R).  
  
    -   Stellen Sie SQL_ATTR_ROW_BIND_TYPE auf SQL_BIND_BY_COLUMN ein.  
  
    -   Legen Sie fest, dass das SQL_ATTR_ROWS FETCHED_PTR-Attribut auf eine SQLUINTEGER-Variable verweist, die die Anzahl der abgerufenen Zeilen enthält.  
  
    -   Lassen Sie SQL_ATTR_ROW_STATUS_PTR auf ein Array[R] von SQLUSSMALLINT-Variablen verweisen, die die Zeilenstatusindikatoren enthalten.  
  
3.  Ausführen der Anweisung.  
  
4.  Jeder Aufruf von [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) oder [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) ruft R-Zeilen ab und überträgt die Daten in die gebundenen Spalten.  
  
### <a name="to-use-row-wise-binding"></a>So verwenden Sie zeilenbezogene Bindungen  
  
1.  Weisen Sie ein Array [R] mit Strukturen zu, wobei R der Anzahl der Zeilen im Rowset entspricht. Die Struktur verfügt über ein Element für jede Spalte, und jedes Element besteht aus zwei Teilen:  
  
    -   Der erste Teil ist eine Variable des entsprechenden Datentyps zum Speichern der Spaltendaten.  
  
    -   Der zweite Teil ist eine SQLINTEGER-Variable zum Speichern des Spaltenstatusindikators.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) um die folgenden Attribute festzulegen:  
  
    -   Stellen Sie SQL_ATTR_ROW_ARRAY_SIZE auf die Anzahl der Zeilen im Rowset ein (R).  
  
    -   Legen Sie SQL_ATTR_ROW_BIND_TYPE auf die Größe der in Schritt 1 zugeordneten Struktur fest.  
  
    -   Legen Sie fest, dass das SQL_ATTR_ROWS_FETCHED_PTR-Attribut auf eine SQLUINTEGER-Variable verweist, die die Anzahl der abgerufenen Zeilen enthält.  
  
    -   Lassen Sie SQL_ATTR_PARAMS_STATUS_PTR auf ein Array[R] von SQLUSSMALLINT-Variablen verweisen, die die Zeilenstatusindikatoren enthalten.  
  
3.  Rufen Sie für jede Spalte im Resultset, [SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md) , zeigen Sie den Datenwert- und den datenlängenzeigern der Spalte auf die Variablen im ersten Element des Arrays von Strukturen, die in Schritt 1 zugewiesen wurden.  
  
4.  Ausführen der Anweisung.  
  
5.  Jeder Aufruf von [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) oder [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) ruft R-Zeilen ab und überträgt die Daten in die gebundenen Spalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Cursor Gewusst-wie-Themen zum Verwenden von &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)   
 [Implementieren von Cursorn](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [Verwenden von Cursorn &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/use-cursors-odbc.md)  
  
  
