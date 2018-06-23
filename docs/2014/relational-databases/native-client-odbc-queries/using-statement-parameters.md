---
title: Verwenden von Anweisungsparametern | Microsoft Docs
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
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c359db9f39f659ac497adcf3bc6e343e1dd6796
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163127"
---
# <a name="using-statement-parameters"></a>Verwenden von Anweisungsparametern
  Ein Parameter ist eine Variable in einer SQL-Anweisung, die eine ODBC-Anwendung für folgende Vorgänge aktivieren kann:  
  
-   Werte für Spalten in einer Tabelle effizient bereitstellen  
  
-   Benutzerinteraktion beim Aufstellen von Abfragekriterien verbessern  
  
-   Verwalten von **Text**, **Ntext**, und **Image** Daten und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen C-Datentypen.  
  
 Z. B. eine **Teile** Tabelle enthält, Spalten, die mit dem Namen **PartID**, **Beschreibung**, und **Preis**. Um ein Teil ohne Parameter hinzuzufügen, ist eine SQL-Anweisung erforderlich. Beispiel:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Diese Anweisung ist zwar zum Einfügen einer Zeile in eine bekannte Menge von Werten akzeptabel, sie ist jedoch umständlich, wenn die Anwendung mehrere Zeilen einfügen muss. ODBC löst dieses Problem, indem eine Anwendung jeden Datenwert in einer SQL-Anweisung durch eine Parametermarkierung ersetzen kann. Diese wird durch ein Fragezeichen (?) angegeben. Im folgenden Beispiel werden drei Datenwerte durch Parametermarkierungen ersetzt:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Die Parametermarkierungen werden dann an Anwendungsvariablen gebunden. Um eine neue Zeile einzufügen, muss die Anwendung nur die Werte der Variablen festlegen und die Anweisung ausführen. Der Treiber ruft dann die aktuellen Werte der Variablen ab und sendet sie an die Datenquelle. Wenn die Anweisung mehrfach ausgeführt wird, kann die Anwendung den Prozess durch Vorbereiten der Anweisung noch effizienter gestalten.  
  
 Auf jede Parametermarkierung wird durch die entsprechende Ordnungszahl, die den Parametern von links nach rechts zugewiesen wurde, verwiesen. Die äußere linke Parametermarkierung in einer SQL-Anweisung besitzt den Ordnungswert 1, die nächste Markierung den Wert 2 usw.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Binden von Parametern](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  