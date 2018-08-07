---
title: Schreiben internationaler Transact-SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a8959ff278807ced475c63ea1e56388ba23ab9d3
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39564424"
---
# <a name="write-international-transact-sql-statements"></a>Schreiben internationaler Transact-SQL-Anweisungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Datenbanken und Datenbankanwendungen, die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwenden, können leichter von einer Sprache in eine andere übertragen werden bzw. unterstützen mehrere Sprachen, wenn die folgenden Richtlinien eingehalten werden:  
  
-   Ersetzen Sie alle Vorkommen von der **char**, **varchar**, und **text** Datentypen mit **nchar**, **nvarchar**, und **nvarchar(max)**. Auf diese Weise müssen Sie keine Schwierigkeiten mit der Codepagekonvertierung berücksichtigen. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Wenn Vergleiche und Vorgänge in bestimmten Monaten oder an bestimmten Arbeitstagen ausgeführt werden, verwenden Sie die numerischen Datumseinheiten anstelle der Namenszeichenfolgen. Unterschiedliche Spracheinstellungen geben verschiedene Namen für Monate und Arbeitstage zurück. Beispielsweise gibt DATENAME(MONTH,GETDATE()) den Monat May zurück, wenn die Sprache auf US- Englisch festgelegt ist, beim Festlegen der Sprache Deutsch wird Mai und beim Festlegen der Sprache Französisch mai zurückgegeben. Verwenden Sie stattdessen eine Funktion wie DATEPART, die die Monatszahl anstelle des Namens verwendet. Verwenden Sie DATEPART-Namen, wenn Sie Resultsets erstellen, die für einen Benutzer angezeigt werden sollen, da Datumsbezeichnungen häufig aussagekräftiger sind als eine numerische Darstellung. Kopieren Sie jedoch keine logischen Befehle, die davon abhängen, dass die angezeigten Namen aus einer bestimmten Sprache stammen.  
  
-   Wenn Sie Datumseingaben in Vergleichen oder als Eingabe in INSERT- oder UPDATE-Anweisungen angeben, verwenden Sie Konstanten, die in allen Spracheinstellungen gleich interpretiert werden:  
  
    -   ADO-, OLE DB- und ODBC-Anwendungen sollten folgende ODBC-Timestamps und folgende ESCAPE-Klauseln für Datum und Zeit verwenden:  
  
         **{ ts'** yyyy**-***mm***-***dd**hh ***:*** mm ***:*** ss *[**.***fff*] **'}** Beispiel: **{ ts'** 1998**-** 09**-** 24 10 **:** 02 **:** 20 **' }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** Beispiel: **{ d'** 1998**-** 09**-** 24 **'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** Beispiel: **{ t'** 10:02:20 **'}**  
  
    -   Anwendungen, die andere APIs verwenden, oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts, gespeicherte Prozedure und Trigger sollten unstrukturierte Zeichenfolgen verwenden. Zum Beispiel *yyyymmdd* für 19980924.  
  
    -   Anwendungen, die andere APIs oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts, gespeicherte Prozeduren und Trigger verwenden, sollten die CONVERT-Anweisung mit dem expliziten Parameter „style“ für alle Konvertierungen zwischen den Datentypen **time**, **date**, **smalldate**, **datetime**, **datetime2**und **datetimeoffset** sowie Zeichenfolgen-Datentypen verwenden. Die folgende Anweisung wird beispielsweise für alle Verbindungseinstellungen für Sprach- oder Datumsformate gleich interpretiert:  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Weitere Informationen finden Sie unter [CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
  
