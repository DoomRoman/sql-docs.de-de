---
title: TuningOptions-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4e0a20be1c4ff3dbaf9a0d833c5c029cbe6e2d30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775148"
---
# <a name="tuningoptions-element-dta"></a>TuningOptions-Element (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Enthält die Optimierungsoptionen für eine bestimmte Optimierungssitzung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Kann bei Verwendung nur einmalig pro **DTAInput** -Element verwendet werden.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[DTAInput-Element &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**Untergeordnete Elemente**|**ReportSet** -Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **TuningLogTable** -Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **NumberOfEvents** -Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TuningTimeInMin-Element &#40;DTA&#41;](../../tools/dta/tuningtimeinmin-element-dta.md)<br /><br /> [StorageBoundInMB-Element &#40;DTA&#41;](../../tools/dta/storageboundinmb-element-dta.md)<br /><br /> **MaxKeyColumnsInIndex** -Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **MaxColumnsInIndex** -Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **MinPercentageImprovement** -Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TestServer-Element &#40;DTA&#41;](../../tools/dta/testserver-element-dta.md)<br /><br /> [FeatureSet-Element &#40;DTA&#41;](../../tools/dta/featureset-element-dta.md)<br /><br /> [Partitioning-Element &#40;DTA&#41;](../../tools/dta/partitioning-element-dta.md)<br /><br /> [DropOnlyMode-Element &#40;DTA&#41;](../../tools/dta/droponlymode-element-dta.md)<br /><br /> [KeepExisting-Element &#40;DTA&#41;](../../tools/dta/keepexisting-element-dta.md)<br /><br /> [OnlineIndexOperation-Element &#40;DTA&#41;](../../tools/dta/onlineindexoperation-element-dta.md)<br /><br /> [DatabaseToConnect-Element &#40;DTA&#41;](../../tools/dta/databasetoconnect-element-dta.md)<br /><br /> **IgnoreConstantsInWorkload** -Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **RetainShellDB** -Element. Weitere Informationen finden Sie im [XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Beispiel  
 Beispiele für das **TuningOptions**-Element finden Sie unter [Beispiele für XML-Eingabedateien &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [XML-Eingabedateireferenz &amp;amp;#40;Datenbankoptimierungsratgeber&amp;amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
