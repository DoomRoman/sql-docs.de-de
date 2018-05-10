---
title: Generieren von XML aus Rowsets mit FOR XML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, generating XML from rowsets
ms.assetid: d061c0f1-3de9-4ad1-bbca-ce45d064b6c8
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6ebe3216692f8a42bdb805c01bbc20f5255f78c3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="generate-xml-from-rowsets-with-for-xml"></a>Generieren von XML aus Rowsets mit FOR XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Sie können eine **xml** -Datentypinstanz aus einem Rowset generieren, indem Sie FOR XML mit der neuen **TYPE** -Direktive verwenden.  
  
 Das Ergebnis kann einer Spalte, einer Variablen oder einem Parameter mit dem **xml** -Datentyp zugewiesen werden. Außerdem kann FOR XML geschachtelt werden, um jede beliebige hierarchische Struktur zu generieren. Damit kann geschachteltes FOR XML viel bequemer geschrieben werden als FOR XML EXPLICIT, es zeigt aber möglicherweise eine weniger gute Leistung bei tiefen Hierarchien. FOR XML führt auch einen neuen PATH-Modus ein. Dieser neue Modus gibt den Pfad im XML-Baum an, in dem der Wert einer Spalte erscheint.  
  
 Die neue **FOR XML TYPE** -Direktive kann verwendet werden, um schreibgeschützte XML-Sichten für relationale Daten mit SQL-Syntax zu definieren. Die Sicht kann mit SQL-Anweisungen und eingebettetem XQuery abgefragt werden, wie das im folgenden Beispiel gezeigt wird. Sie können auf diese SQL-Sichten auch in gespeicherten Prozeduren verweisen.  
  
## <a name="example-sql-view-returning-generated-xml-data-type"></a>Beispiel: SQL-Sicht zum Zurückgeben des generiertem xml-Datentyps  
 Die folgende SQL-Sichtdefinition erstellt eine XML-Sicht für eine relationale Spalte pk und ruft die Buchautoren aus einer XML-Spalte ab.  
  
```  
CREATE VIEW V (xmlVal) AS  
SELECT pk, xCol.query('/book/author')  
FROM   T  
FOR XML AUTO, TYPE  
```  
  
 Die V-Sicht enthält eine einzelne Zeile mit einem einzelnen columnxmlVal des XML-Typs`.` . Diese kann wie eine reguläre **xml** -Datentypinstanz abgefragt werden. Beispielsweise gibt die folgende Abfrage den Autor zurück, dessen Vorname "David" ist:  
  
```  
SELECT xmlVal.query('//author[first-name = "David"]')  
FROM   V  
```  
  
 SQL-Sichtdefinitionen ähneln in gewisser Weise XML-Sichten, indem Sie durch Verwenden von Schemas mit Anmerkungen erstellt werden. Es gibt jedoch auch wichtige Unterschiede. Die SQL-Sichtdefinition ist schreibgeschützt und muss mit eingebettetem XQuery bearbeitet werden. Die XML-Sichten werden ebenfalls durch Verwenden von Schemas mit Anmerkungen erstellt. Darüber hinaus materialisiert die SQL-Sicht das XML-Ergebnis, bevor der XQuery-Ausdruck angewendet wird, während die XPath-Abfragen für XML-Sichten SQL-Abfragen für die zugrunde liegenden Tabellen auswerten.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [FOR XML &#40;SQL Server&#41;](../../relational-databases/xml/for-xml-sql-server.md)  
  
  
