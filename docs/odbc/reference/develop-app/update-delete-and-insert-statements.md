---
title: UPDATE, DELETE und INSERT-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92fb7b0e9722c52c7f1e9fc071d434f531b2fc46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721908"
---
# <a name="update-delete-and-insert-statements"></a>UPDATE-, DELETE- und INSERT-Anweisungen
SQL-basierten Anwendungen und nehmen Sie Änderungen an Tabellen durch Ausführen der **UPDATE**, **löschen**, und **einfügen** Anweisungen. Diese Anweisungen sind Teil der Konformitätsgrad des mindestens SQL-Grammatik und von allen Treibern und Datenquellen unterstützt werden müssen.  
  
 Die Syntax dieser Anweisungen lautet:  
  
 **UPDATE***Tabellenname*   
  
 **Legen Sie** *Spaltenbezeichner* **=** {*Ausdruck* &#124; **NULL**}  
  
 [**,** *Spaltenbezeichner* **=** {*Ausdruck* &#124; **NULL**}]...  
  
 [**, In denen** *Suchbedingung*]  
  
 **DELETE FROM** *Tabellenname*[**, in denen** *Suchbedingung*]  
  
 **INSERT INTO** *Tabellenname*[**(*** Spaltenbezeichner* [**,** *Spaltenbezeichner*]... **)**]  
  
 {*-Abfragespezifikation* &#124;  **Werte (*** Wert einfügen* [**,** *Wert einfügen*]... **)**}  
  
 Beachten Sie, dass die *-Abfragespezifikation* Element ist nur in der Core und erweiterte SQL-Grammatik, und dass die *Ausdruck* und *Suchbedingung* Elemente steigern. komplexe, in der Core und erweiterte SQL-Grammatik.  
  
 Andere SQL-Anweisungen, wie **UPDATE**, **löschen**, und **einfügen** Anweisungen sind häufig effizienter, wenn sie Parameter verwenden. Beispielsweise kann die folgende Anweisung vorbereitet und wiederholt ausgeführt, um mehrere Zeilen in der Tabelle Orders einzufügen:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Diese Effizienz kann durch Übergeben von Arrays für Parameterwerte erhöht werden. Weitere Informationen über Parameter und Arrays von Parameterwerten finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md).
