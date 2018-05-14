---
title: Ändern von Tabellen-, Spalten- oder zeilenfilterzuordnungen | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6eab5a756fb52afeb69c5f4c7646d768b9ec263f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="change-table-column-or-row-filter-mappings"></a>Ändern von Tabellen-, Spalten- oder Zeilenfilterzuordnungen 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  In diesem Artikel wird beschrieben, wie so ändern Sie Tabellen-, Spalten- oder zeilenfilterzuordnungen mit der **Tabelleneigenschaften bearbeiten** im Dialogfeld [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
 Die Optionen im Dialogfeld **Tabelleneigenschaften bearbeiten** variieren, je nachdem, ob Daten ursprünglich durch Auswahl von Tabellen aus einer Liste oder mithilfe einer SQL-Abfrage importiert wurden. Wenn die Daten ursprünglich durch Auswahl aus einer Liste importiert wurden, wird das Dialogfeld **Tabelleneigenschaften bearbeiten** im Tabellenvorschaumodus angezeigt. In diesem Modus wird nur eine Teilmenge angezeigt, die auf die ersten 50 Zeilen der Quelltabelle beschränkt ist. Wenn die Daten ursprünglich durch Verwendung einer SQL-Anweisung importiert wurden, wird im Dialogfeld **Tabelleneigenschaften bearbeiten** nur eine SQL-Anweisung angezeigt. Mithilfe einer SQL-Abfrageanweisung können Sie eine Teilmenge der Zeilen abrufen, indem Sie entweder einen Filter entwerfen oder die SQL-Anweisung manuell bearbeiten.  
  
 Wenn Sie die Quelle in eine Tabelle ändern, die andere Spalten als die aktuelle Tabelle enthält, wird eine entsprechende Warnmeldung angezeigt. Sie müssen dann die Spalten auswählen, die Sie in die aktuelle Tabelle einfügen möchten, und auf **Speichern**klicken. Sie können die gesamte Tabelle ersetzen, indem Sie das Kontrollkästchen links von der Tabelle aktivieren.  
  
> [!NOTE]  
>  Wenn die Tabelle über mehrere Partitionen verfügt, können Sie die Zeilenfilterzuordnungen nicht im Dialogfeld Tabelleneigenschaften bearbeiten ändern. Verwenden Sie zum Ändern der Zeilenfilterzuordnungen für Tabellen mit mehreren Partitionen den Partitions-Manager. Weitere Informationen finden Sie unter [Partitionen](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a>So ändern Sie Tabellen-, Spalten- oder Zeilenfilterzuordnungen  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle und dann auf das Menü **Tabelle** und auf **Tabelleneigenschaften**.  
  
2.  Suchen Sie im Dialogfeld **Tabelleneigenschaften bearbeiten** nach der Spalte, die die Filterkriterien enthält, und klicken Sie dann rechts von der Spaltenüberschrift auf den Pfeil nach unten.  
  
3.  Führen Sie im Menü **AutoFilter** einen der folgenden Schritte aus:  
  
    -   Wählen Sie in der Liste der Spaltenwerte mindestens einen Wert aus, nach dem gefiltert werden soll, bzw. heben Sie die Auswahl auf, und klicken Sie auf OK.  
  
         Wenn die Anzahl der Werte sehr groß ist, kann es sein, dass einzelne Elemente nicht in der Liste angezeigt werden. Stattdessen wird eine Meldung angezeigt, dass zu viele Elemente zum Anzeigen vorhanden sind.  
  
    -   Klicken Sie je nach Typ der Spalte auf **Zahlenfilter** oder **Textfilter** , und klicken Sie anschließend auf einen der Vergleichsoperatorbefehle (wie „Ist gleich“), oder klicken Sie auf „Benutzerdefinierter Filter“. Erstellen Sie im Dialogfeld **Benutzerdefinierter Filter** den Filter, und klicken Sie dann auf **OK**.  
  
         Falls Sie erneut beginnen möchten, klicken Sie auf **Zeilenfilter löschen**.  
  
  
  
