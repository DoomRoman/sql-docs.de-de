---
title: DiagnosticInformation-Element (Ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0e7bf7140b5340e90517d65cf76fbeccf46ebc34
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148293"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a>DiagnosticInformation-Element (ssbdiagnose)
  Das **DiagnosticInformation** -Element enthält alle Elemente, die die vom Hilfsprogramm gefundenen Diagnoseinformationen melden. **DiagnosticInformation** ist das Stammelement einer XML-Ausgabedatei von **ssbdiagnostic** .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|Description|  
|---------------|-----------------|  
|`None`|–|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro **ssbdiagnose** -XML-Ausgabedatei|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|Keine.|  
|**Untergeordnete Elemente**|[Banner-Element &#40;Ssbdiagnose&#41;](banner-element-ssbdiagnose.md)<br /><br /> [Issue-Element &#40;Ssbdiagnose&#41;](issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu XML-Namespaces finden Sie unter [Namespaces in an XML Document](http://go.microsoft.com/fwlink/?LinkId=7341) (in Englisch) in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="see-also"></a>Siehe auch  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  