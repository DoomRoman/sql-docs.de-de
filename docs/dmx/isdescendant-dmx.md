---
title: IsDescendant (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c33a607587ee19de0f47942cd2c1e5b350229a88
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061038"
---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Zeigt an, ob der aktuelle Knoten ein untergeordneter Knoten des angegebenen Knotens ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein boolescher Typ.  
  
## <a name="remarks"></a>Hinweise  
 **IsDescendant** wird nur verwendet, [SELECT FROM &#60;Modell&#62;. Inhalt &#40;DMX&#41; ](../dmx/select-from-model-content-dmx.md) und [SELECT FROM &#60;Modell&#62;. DIMENSION_CONTENT &#40;DMX&#41; ](../dmx/select-from-model-dimension-content-dmx.md) Abfragen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Fälle zurückgegeben, die Nachfolger des Knotens sind, der in der IsDescendant-Funktion angegeben ist.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
