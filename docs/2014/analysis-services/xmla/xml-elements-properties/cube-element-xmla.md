---
title: Cube-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cube Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cube
- urn:schemas-microsoft-com:xml-analysis#Cube
- http://schemas.microsoft.com/analysisservices/2003/engine#Cube
helpviewer_keywords:
- Cube element
ms.assetid: 2e8662f4-fb2e-43af-b70a-9e0b5872c9b9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: de5c375e5e517e155bd6efb4beeeef61e9f31a79
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103360"
---
# <a name="cube-element-xmla"></a>Cube-Element (XMLA)
  Gibt den Cube an, die die vom übergeordneten Element dargestellte Dimension enthält [Objekt](object-element-dimension-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Object>  
   ...  
   <Cube>...</Cube>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Objekt](object-element-dimension-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `Cube` Element ist ein Objektbezeichner, der den Namen des Cubes, die Dimension enthält, dargestellt durch die `Object` Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Database-Element &#40;XMLA&#41;](database-element-xmla.md)   
 [Dimension-Element &#40;XMLA&#41;](dimension-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
