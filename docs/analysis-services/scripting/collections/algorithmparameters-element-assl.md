---
title: AlgorithmParameters-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8fd80caa311b43ed713b8d36ef99f4e5035f9e57
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="algorithmparameters-element-assl"></a>AlgorithmParameters-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die Auflistung der Parameter für den Algorithmus, der verwendet wird, indem Sie eine [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModel>  
   ...  
   <AlgorithmParameters>  
      <AlgorithmParameter>...</AlgorithmParameter>  
   </AlgorithmParameters>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine (Auflistung)|  
|Standardwert|Keine (Auflistung)|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Untergeordnete Elemente|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die **AlgorithmParameters** -Auflistung enthält eine erweiterbare Menge aus Parametern für einen Miningmodellalgorithmus, die als Name/Wert-Paare dargestellt werden. Die Menge aus anwendbaren Parametern ist algorithmusabhängig. Weitere Informationen zu Algorithmusparametern für einen gegebenen Algorithmus finden Sie in der entsprechenden Dokumentation des Algorithmus.  
  
 Verfügbare Algorithmusparameter, einschließlich Überprüfung und Anzeigeinformationen, können vom DMSCHEMA_MINING_SERVICE_PARAMETERS-Schemarowset abgerufen werden.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Algorithm-Element &#40;ASSL&#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
