---
title: KpiGoal-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fd8afbe7-b57d-4b47-862d-eb7b2489c327
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b64e3124ba7a848921e1b0844b20d03e9aa82af4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165241"
---
# <a name="kpigoal-element-csdlbi"></a>KpiGoal-Element (CSDLBI)
  Das KpiGoal-Element stellt einen Verweis auf die Spalte bereit, die verwendet wird, um das Ziel für einen Key Performance Indicator (KPI) zu definieren.  
  
 In CSDLBI basieren KPIs auf Measures, und das Measureelement beinhaltet die Formel (sofern vorhanden), während andere dem KPI zugeordnete Metadaten als Teil des [KPI-Elements &#40;CSDLBI&#41;](kpi-element-csdlbi.md) definiert sind.  Das Kpigoal-Element ist ein Untertyp des KPI-Elements.  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 In der folgenden Tabelle werden die Attribute aufgelistet, die das KpiGoal-Element definieren.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|ja|Ein Verweis auf die Spalte, die den KPI-Zielwert enthält.<br /><br /> Das Kpigoal-Element muss genau ein PropertyRef-Element enthalten.<br /><br /> Weitere Informationen finden Sie unter [PropertyRef-Element &#40;CSDLBI&#41;](propertyref-element-csdlbi.md).|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Das folgende Beispiel veranschaulicht einen KPI aus dem tabellarischen AdventureWorks-Modellbeispiel in CSDLBI, Version 1.1.  
  
```  
  
<Property Name="InternetCurrentSalesPerformance" Type="Double">  
  <bi:Measure>  
    <bi:Kpi StatusGraphic="Three Stars Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Im folgenden Beispiel wird in CSDLBI, Version 1.1, ein KPI aus dem Contoso-Vorgangscube veranschaulicht.  
  
```  
<bi:Measure   
       Caption="Sum of SalesAmount"   
       ReferenceName="Sum of SalesAmount"   
       FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
    <bi:Kpi   
       StatusGraphic="Three Circles Colored">  
      <bi:KpiGoal>  
         <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Goal" />  
       </bi:KpiGoal>  
       <bi:KpiStatus>  
          <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Status" />  
        </bi:KpiStatus>  
       </bi:Kpi>  
</bi:Measure>  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [KPI-Element &#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
  
