---
title: CalculationType-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CalculationType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalculationType
helpviewer_keywords:
- CalculationType element
ms.assetid: b974b3d3-fbf7-4d77-8f6e-4e05a258fe84
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 434d0151009119a5e05d49180c6a9d1eb9519d77
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057280"
---
# <a name="calculationtype-element-assl"></a>CalculationType-Element (ASSL)
  Beschreibt den Typ der Berechnung, die in der zugeordneten definiert [CalculationProperty](../objects/calculationproperty-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CalculationProperty>  
   ...  
   <CalculationType>...</CalculationType>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Datenmember*|Die Berechnungseigenschaft gilt für eine berechnete Elementdefinition.|  
|*Festlegen*|Die Berechnungseigenschaft gilt für eine benannte Satzdefinition.|  
|*Zellen*|Die Berechnungseigenschaft gilt für eine berechnete Zelldefinition.|  
  
 Die Enumeration, die den zulässigen Werten für die entsprechende `CalculationType` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.CalculationType>.  
  
## <a name="see-also"></a>Siehe auch  
 [CalculationProperties-Element &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript-Element &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts-Element &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  