---
title: Inkrementelles Durchsuchen eines aktiven Dokuments | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8978358051fef46be1f6d89f0775cc0ef8714ebf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742670"
---
# <a name="search-an-active-document-incrementally"></a>Inkrementelles Durchsuchen eines aktiven Dokuments
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Sie können ein einzelnes Dokument oder Fenster inkrementell durch Eingabe von Text durchsuchen. Beim Suchvorgang wird die erste Zeichenfolge hervorgehoben, die mit der eingegebenen Zeichenfolge für die inkrementelle Suche im Dokument bzw. Fenster übereinstimmt. Bei der inkrementellen Suche wird automatisch der gesamte Text in einem Dokument bzw. Fenster durchsucht, ausgenommen ausgeblendeter Text.  
  
 Bei der Option **Groß-/Kleinschreibung beachten** verwendet die inkrementelle Suche die Kriterien aus der vorherigen Suche. Wenn Sie z. B. mit dem Dialogfeld **In Dateien suchen** eine Suche in mehreren Dateien ausgeführt haben, die Option **Groß-/Kleinschreibung beachten**aktivieren und jetzt einen inkrementellen Suchvorgang ausführen, wird bei der Suche die Groß-/Kleinschreibung beachtet.  
  
### <a name="to-search-incrementally"></a>So führen Sie einen inkrementellen Suchvorgang aus  
  
1.  Öffnen Sie die zu durchsuchende Datei bzw. das Fenster.  
  
2.  Zeigen Sie im Menü **Bearbeiten** auf **Erweitert**, und klicken Sie dann auf **Inkrementelle Suche**.  
  
     Der Cursor wird jetzt als Fernglas mit einem Pfeil zur Anzeige der Suchrichtung dargestellt, und in der Statusleiste wird "Inkrementelle Suche" angezeigt.  
  
3.  Beginnen Sie mit der Eingabe der Textzeichenfolge.  
  
     In der Statusleiste wird der Text angezeigt, den Sie eingeben, und der Editor hebt die erste Übereinstimmung hervor. Wenn Sie mit der Eingabe fortfahren, hebt der Editor die nächste Übereinstimmung hervor. Wenn es keine Übereinstimmungen gibt, wird in der Statusleiste Folgendes angezeigt:  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 Inkrementelle Suchvorgänge werden abwärts von links nach rechts von der aktuellen Position im Dokument ausgeführt. Inkrementelle Suchvorgänge können mithilfe von Tastenkombinationen ausgeführt werden.  
  
> [!NOTE]  
>  Eine vollständige Liste der Tastenkombinationen finden Sie unter [Tastenkombinationen für SQL Server Management Studio](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Suchen und Ersetzen](../../relational-databases/scripting/search-and-replace.md)   
 [Interaktives Durchsuchen von Dokumenten](../../relational-databases/scripting/search-documents-interactively.md)   
 [Durchsuchen von Dokumenten mithilfe von Ergebnislisten](../../relational-databases/scripting/search-documents-using-results-lists.md)   
 [Suchen von Text mit Platzhaltern](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [Suchen von Text mit regulären Ausdrücken](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  
