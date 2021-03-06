---
title: INSERT - SQL-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa2211ddef09e127b66430968792007d29dd5eb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840098"
---
# <a name="insert---sql-command"></a>INSERT (SQL-Befehl)
Fügt einen Datensatz am Ende eine Tabelle mit der angegebenen Feldwerte.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die systemeigene Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie in den Hinweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Argumente  
 INSERT INTO *Dbf_name*  
 Gibt den Namen der Tabelle, die der neue Datensatz angefügt wird. *Dbf_name* kann einen Pfad enthalten und kann ein Namensausdruck sein.  
  
 Wenn die Tabelle, die Sie angeben, nicht geöffnet ist, wird sie ausschließlich in einen neuen Arbeitsbereich geöffnet, und des neuen Datensatzes in der Tabelle hinzugefügt wird. Der neue Arbeitsbereich ist nicht ausgewählt. aktuellen Arbeitsbereich bleibt ausgewählt.  
  
 Wenn die Tabelle, die Sie angeben, geöffnet ist, fügt Einfügen des neuen Datensatzes in die Tabelle an. Ist die Tabelle außer dem aktuellen Arbeitsbereich in einen Arbeitsbereich öffnen, wird nicht es ausgewählt, nachdem der Datensatz angefügt wurde. aktuellen Arbeitsbereich bleibt ausgewählt.  
  
 [( *fname1*[, *fname2*[,...]])]  
 Gibt an, den Namen der Felder im neuen Datensatz in die die Werte eingefügt werden.  
  
 Werte ( *eExpression1*[, *eExpression2*[,...]])  
 Gibt an, die Werte der Felder des neuen Datensatzes eingefügt. Wenn Sie die Feldnamen weglassen, müssen Sie die Feldwerte in der Reihenfolge definiert, durch die Tabellenstruktur angeben.  
  
## <a name="remarks"></a>Hinweise  
 Der neue Datensatz enthält, die Daten, die in der VALUES-Klausel aufgeführt wird.  
  
## <a name="driver-remarks"></a>Treiber "Hinweise".  
 Wenn Ihre Anwendung die ODBC-SQL-Anweisung INSERT an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber den Befehl in der Visual FoxProINSERT-Befehl ohne Übersetzung an.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen Sie Tabelle - SQL-Befehl.](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (SQL-Befehl)](../../odbc/microsoft/select-sql-command.md)
