---
title: Semiadditives Verhalten definieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- semiadditive
- Business Intelligence enhancements [Analysis Services], semiadditive behavior
- measures [Analysis Services], semiadditive
ms.assetid: b25726bc-728b-4601-ad87-9015c39dc615
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5a96921b37affe35fcb4344a66ef36aaf26cadeb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265416"
---
# <a name="define-semiadditive-behavior"></a>Semiadditives Verhalten definieren
  Semiadditive Measures, die nicht in allen Dimensionen einheitlich aggregiert werden, kommen in vielen Geschäftsszenarien sehr häufig vor. Jeder Cube, der auf Momentaufnahmen von Bilanzen über einen Zeitraum basiert, weist dieses Problem auf. Sie finden diese Momentaufnahmen in Anwendungen, die mit Wertpapiere, Kontostände, Budgetierung, Humanressourcen, Versicherungspolicen, Schadensansprüchen und viele andere Geschäftsfelder behandeln.  
  
 Fügen Sie semiadditives Verhalten einem Cube hinzu, um eine Aggregationsmethode für einzelne Measures oder Elemente eines Kontotypattributs zu definieren. Wenn der Cube eine Kontodimension enthält, können Sie automatisch semiadditives Verhalten auf der Basis des Kontotyps festlegen.  
  
 Öffnen Sie einen Cube im Cube-Designer, und wählen Sie im Menü Cube die Option **Business Intelligence hinzufügen** aus, um semiadditives Verhalten hinzuzufügen. Wählen Sie im Business Intelligence-Assistenten auf der Seite **Erweiterung auswählen** die Option **Semiadditives Verhalten definieren** aus. Dieser Assistent führt Sie anschließend durch die Schritte zum Identifizieren der Measures, die semiadditives Verhalten aufweisen.  
  
 Mit Ausnahme von LastChild, das in der Standard Edition verfügbar ist, ist semiadditives Verhalten nur in der Business Intelligence Edition oder der Enterprise Edition verfügbar.  
  
## <a name="define-semiadditive-behavior"></a>Semiadditives Verhalten definieren  
 Auf der Seite **Semiadditives Verhalten definieren** des Assistenten können Sie durch Auswählen einer der folgenden Optionen auswählen, wie semiadditiv definiert werden soll:  
  
 **Semiadditives Verhalten deaktivieren**  
 Deaktiviert das semiadditive Verhalten für einen Cube, für den vorher semiadditives Verhalten definiert war. Diese Option setzt ein Measure zum `SUM` , wenn sie auf eines der folgenden aggregationsfunktionstypen festgelegt ist:  
  
-   By Account  
  
-   Average of Children  
  
-   First Child  
  
-   Last Child  
  
-   Last Nonempty Child  
  
-   First Nonempty Child  
  
-   InclusionThresholdSetting  
  
 Diese Option werden keine Measures mit einer regulären Aggregationsfunktion geändert: `Sum`, `Min`, `Max`, `Count`, oder `Distinct``Count`.  
  
 **Die Account-Kontodimension, die semiadditive Elemente enthält, wurde vom Assistenten erkannt. Elemente dieser Dimension gemäß dem semiadditiven Verhalten, die für den jeweiligen Kontotyp angegeben werden vom Server aggregiert.**  
 Bewirkt, dass alle Measures aus einer Measuregruppe, die durch eine Dimension des Typs Account dimensioniert wurden, vom System auf die Aggregationsfunktion By Account festgelegt und Elemente dieser Dimension gemäß dem semiadditiven Verhalten, das für den jeweiligen Kontotyp angegeben ist, vom Server aggregiert werden.  
  
> [!NOTE]  
>  Diese Option wird standardmäßig ausgewählt, wenn der Assistent eine Dimension des Typs Account erkennt.  
  
 **Semiadditives Verhalten für einzelne Measures definieren**  
 Wählt das semiadditive Verhalten für jedes Measure einzeln aus. Die Standardeinstellung ist `SUM` (vollständig additiv).  
  
> [!NOTE]  
>  Diese Option wird standardmäßig ausgewählt, wenn der Assistent keine Dimension des Typs Account erkennt.  
  
 Für die einzelnen Measures können Sie einen der Typen der semiadditiven Funktionalität auswählen, die in der folgenden Tabelle beschrieben sind.  
  
|Semiadditive Funktion|Description|  
|---------------------------|-----------------|  
|Average of Children|Die Aggregation eines Elements ist der Durchschnitt seiner untergeordneten Elemente.|  
|ByAccount|Das System liest das für den Kontotyp angegebene semiadditive Verhalten.|  
|Count|Die Aggregation ist eine Anzahl von Elementen.|  
|Distinct Count|Die Aggregation ist eine Anzahl von eindeutigen Elementen.|  
|First Child|Der Elementwert wird als der Wert seines ersten untergeordneten Elements in der Zeitdimension ausgewertet.|  
|FirstNonEmpty|Der Elementwert wird als der Wert seines ersten untergeordneten Elements in der Zeitdimension ausgewertet, das Daten enthält.|  
|LastChild|Der Elementwert wird als der Wert seines letzten untergeordneten Elements in der Zeitdimension ausgewertet.|  
|LastNonEmpty|Der Elementwert wird als der Wert seines letzten untergeordneten Elements in der Zeitdimension ausgewertet, das Daten enthält.|  
|Max|Die Standardfunktion für maximale Aggregation wird angewendet.|  
|Min|Die Standardfunktion für minimale Aggregation wird angewendet.|  
|InclusionThresholdSetting|Keine Aggregation wird angewendet.|  
|SUM|Die Standardfunktion zur Summierung wird angewendet.|  
  
 Vorhandenes semiadditive Verhalten wird nach Abschluss des Assistenten überschrieben.  
  
  
