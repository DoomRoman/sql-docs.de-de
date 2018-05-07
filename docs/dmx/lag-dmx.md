---
title: Verzögerung (DMX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LAG
dev_langs:
- DMX
helpviewer_keywords:
- Lag function
ms.assetid: 2da6df1a-5506-4871-a0f0-83292f1df41e
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 929924bc7ef571a64bc4d7f6c26d20dece081821
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="lag-dmx"></a>Lag (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Zeitscheibe zwischen dem Datum des aktuellen Falles und dem letzten Datum der Trainingsmenge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert mit dem Typ integer.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die **Lag** Funktion dient für ein Modell, in denen die KEY TIME-Spalte in einer geschachtelten Tabelle befindet, kann die Funktion muss in der untergeordneten Select-Anweisung die gefunden werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Fälle zurückgegeben, die in den letzten 12 Monaten der Daten liegen, die zum Trainieren des Modells verwendet wurden.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis-Funktion](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
