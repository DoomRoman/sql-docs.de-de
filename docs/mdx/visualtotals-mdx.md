---
title: VisualTotals (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2690807cc3438773c3c2de613dedf7c1419ba0f1
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581812"
---
# <a name="visualtotals-mdx"></a>VisualTotals (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt eine Menge zurück, die durch dynamische Gesamtwertbildung der untergeordneten Elemente in einer angegebenen Menge generiert wird. Optional wird im Resultset ein Muster für den Namen des übergeordneten Elements verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
VisualTotals(Set_Expression[,Pattern])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Muster*  
 Ein gültiger Zeichenfolgenausdruck für das übergeordnete Element der Menge, der ein Sternchen (*) als Ersatzzeichen für den Namen des übergeordneten Elements enthält.  
  
## <a name="remarks"></a>Hinweise  
 Der angegebene Mengenausdruck kann eine Menge angeben, die Elemente auf beliebigen Ebenen innerhalb ein und derselben Dimension enthält, im Allgemeinen Elemente, die in einer Vorgänger-Nachfolger-Beziehung zueinander stehen. Die **VisualTotals** Funktion fasst die Werte der untergeordneten Elemente in der angegebenen Menge und ignoriert die untergeordneten Elemente, die nicht in der Gruppe in das Ergebnis eingeschlossen sind. Bei hierarchisch geordneten Mengen werden die Gesamtwerte visuell summiert. Wenn die Reihenfolge der Elemente in der Menge die Hierarchie durchbricht, werden die Ergebnisse nicht als sichtbare Gesamtwerte zurückgegeben. Beispielsweise gibt VisualTotals (USA, WA, CA, Seattle) nicht WA als Seattle zurück. Vielmehr werden die Werte für WA, CA und Seattle zurückgegeben und anschließend zum sichtbaren Gesamtwert für USA summiert, wobei die Umsätze für Seattle doppelt gezählt werden.  
  
> [!NOTE]  
>  Anwenden der **VisualTotals** -Funktion auf Dimensionselemente, die nicht mit einem Measure verknüpft sind oder sich unterhalb der Granularität der Measure-Gruppe befinden führt dazu, dass Werte durch Null ersetzt werden.  
  
 *Muster*, ist optional und gibt das Format für die gesamtbetragsbezeichnung an. *Muster* erfordert ein Sternchen (*) als Ersatzzeichen für das übergeordnete Element und den Rest des Texts in der Zeichenfolge in das Ergebnis mit dem übergeordneten Namen verkettet angezeigt wird. Wenn Sie ein Sternchen anzuzeigen, verwenden Sie zwei Sternchen (\*\*).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der sichtbare Gesamtwert für das dritte Quartal des Kalenderjahres 2001 basierend auf dem einzigen angegebenen nachfolgenden Wert, dem Monat Juli, zurückgegeben.  
  
```  
SELECT VisualTotals  
   ({[Date].[Calendar].[Calendar Quarter].&[2001]&[3]  
      ,[Date].[Calendar].[Month].&[2001]&[7]}) ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird das [All]-Element der Category-Attributhierarchie in der Product-Dimension zusammen mit zwei seiner vier untergeordneten Elemente zurückgegeben. Der zurückgegebene Gesamtwert für das [All]-Element für das Internet Sales Amount-Measure stellt lediglich den Gesamtwert der Accessories- und Clothing-Elemente dar. Außerdem wird das Pattern-Argument zur Angabe der Bezeichnung für die [All Products]-Spalte verwendet.  
  
```  
SELECT  
   VisualTotals  
   ({[Product].[Category].[All Products]  
      ,[Product].[Category].[Accessories]  
      ,[Product].[Category].[Clothing]}  
      , '* - Visual Total'  
   ) ON Columns  
, [Measures].[Internet Sales Amount] ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
