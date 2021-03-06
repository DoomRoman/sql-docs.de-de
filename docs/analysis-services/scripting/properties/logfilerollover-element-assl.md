---
title: LogFileRollover-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 73762fbfb606067d7f90beb2b11364d9e8dd0b4d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035981"
---
# <a name="logfilerollover-element-assl"></a>LogFileRollover-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt an, ob die Protokollierung [Ablaufverfolgung](../../../analysis-services/scripting/objects/trace-element-assl.md) -Ausgabe an eine neue Datei, oder beenden, wenn die maximale Protokolldateigröße, sollte angegeben werden, [LogFileSize](../../../analysis-services/scripting/properties/logfilesize-element-assl.md) erreicht ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Trace>  
   ...  
   <LogFileRollover>...</LogFileRollover>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Trace](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Ist der Wert des **LogFileRollover** -Elements auf "True" festgelegt, wird eine neue Datei begonnen, wenn die Größe der Protokolldatei den Wert übersteigt, der im **LogFileSize** -Element des übergeordneten **Trace** -Elements angegeben ist. Anderenfalls wird die Protokollierung beendet.  
  
 Das Element, das das übergeordnete Element des entspricht **LogFileRollover** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Siehe auch  
 [Traces-Element & #40; ASSL & #41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
