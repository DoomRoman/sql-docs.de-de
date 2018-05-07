---
title: MDSCHEMA_MEASURES-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 38dcc34b13b7b65508dc99f925fffa76f3420173
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemameasures-rowset"></a>MDSCHEMA_MEASURES-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt jedes Measure innerhalb eines Cubes.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die **MDSCHEMA_MEASURES** Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Der Name des Katalogs, zu dem dieses Measure gehört. **NULL** , wenn der Anbieter keine Kataloge unterstützt.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Der Name des Schemas, zu dem dieses Measure gehört. **NULL** , wenn der Anbieter keine Schemas unterstützt.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Der Name des Cubes, zu dem dieses Measure gehört.|  
|**MEASURE_NAME**|**DBTYPE_WSTR**||Der Name des Measures.|  
|**MEASURE_UNIQUE_NAME**|**DBTYPE_WSTR**||Der eindeutige Name des Measures. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|**MEASURE_CAPTION**|**DBTYPE_WSTR**||Eine Bezeichnung oder Beschriftung, die dem Measure zugeordnet ist. Wird hauptsächlich für Anzeigezwecke verwendet. Wenn keine Beschriftung vorhanden, **MEASURE_NAME** wird zurückgegeben.|  
|**MEASURE_GUID**|**DBTYPE_GUID**||Nicht unterstützt.|  
|**MEASURE_AGGREGATOR**|**DBTYPE_I4**||Eine Enumeration, die angibt, wie ein Measure abgeleitet wurde. Folgende Werte sind möglich:<br /><br /> **MDMEASURE_AGGR_SUM** (**1**) gibt an, dass das Measure aus aggregierten **Summe**.<br /><br /> **MDMEASURE_AGGR_COUNT** (**2**) gibt an, dass das Measure aus aggregierten **Anzahl**.<br /><br /> **MDMEASURE_AGGR_MIN** (**3**) gibt an, dass das Measure aus aggregierten **MIN**.<br /><br /> **MDMEASURE_AGGR_MAX** (**4**) gibt an, dass das Measure aus aggregierten **MAX**.<br /><br /> **MDMEASURE_AGGR_AVG** (**5**) gibt an, dass das Measure aus aggregierten **AVG**.<br /><br /> **MDMEASURE_AGGR_VAR** (**6**) gibt an, dass das Measure aus aggregierten **VAR**.<br /><br /> **MDMEASURE_AGGR_STD** (**7**) gibt an, dass das Measure aus aggregierten **STDEV**.<br /><br /> **MDMEASURE_AGGR_DST** (**8**) gibt an, dass das Measure aus aggregierten **DISTINCT COUNT**.<br /><br /> **MDMEASURE_AGGR_NONE** (**9**) gibt an, dass das Measure aus aggregierten **NONE**.<br /><br /> **MDMEASURE_AGGR_AVGCHILDREN** (**10**) gibt an, dass das Measure aus aggregierten **AVERAGEOFCHILDREN**.<br /><br /> **MDMEASURE_AGGR_FIRSTCHILD** (**11**) gibt an, dass das Measure aus aggregierten **FIRSTCHILD**.<br /><br /> **MDMEASURE_AGGR_LASTCHILD** (**12**) gibt an, dass das Measure aus aggregierten **LASTCHILD**.<br /><br /> **MDMEASURE_AGGR_FIRSTNONEMPTY** (**13**) gibt an, dass das Measure aus aggregierten **FIRSTNONEMPTY**,<br /><br /> **MDMEASURE_AGGR_LASTNONEMPTY** (**14**) gibt an, dass das Measure aus aggregierten **LASTNONEMPTY**.<br /><br /> **MDMEASURE_AGGR_BYACCOUNT** (**15**) gibt an, dass das Measure aus aggregierten **BYACCOUNT**.<br /><br /> **MDMEASURE_AGGR_CALCULATED** (**127**) gibt an, dass das Measure aus einer Formel abgeleitet wurde, die nicht die oben genannten Einzelfunktionen war.<br /><br /> **MDMEASURE_AGGR_UNKNOWN** (**0**) gibt an, dass das Measure aus einer unbekannten Aggregatfunktion oder Formel abgeleitet wurde.|  
|**DATA_TYPE**|**DBTYPE_UI2**||Der Datentyp des Measures.|  
|**"NUMERIC_PRECISION"**|**DBTYPE_UI2**||Die maximale Genauigkeit der Eigenschaft, wenn der Datentyp des Measureobjekts genau numerisch ist. **NULL** für alle anderen Eigenschaftentypen.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||Die Anzahl der Ziffern rechts neben dem Dezimaltrennzeichen auf, wenn das measureobjekt Typindikator **DBTYPE_NUMERIC** oder **DBTYPE_DECIMAL**. Andernfalls wird dieser Wert **NULL**.|  
|**MEASURE_UNITS**|**DBTYPE_WSTR**||Nicht unterstützt|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Eine lesbare Beschreibung des Measures. **NULL** , wenn keine Beschreibung vorhanden ist.|  
|**AUSDRUCK**|**DBTYPE_WSTR**||Ein Ausdruck für das Element.|  
|**MEASURE_IS_VISIBLE**|**DBTYPE_BOOL**||Ein boolescher Wert zurückgegeben, die immer "true". Wenn das Measure nicht sichtbar ist, wird es nicht im Schemarowset angezeigt.|  
|**LEVELS_LIST**|**DBTYPE_WSTR**||Eine Zeichenfolge, die immer zurückgibt **NULL**.|  
|**MEASURE_NAME_SQL_COLUMN_NAME**|**DBTYPE_WSTR**||Der Name der Spalte in der SQL-Abfrage, die dem Namen des Measures entspricht.|  
|**MEASURE_UNQUALIFIED_CAPTION**|**DBTYPE_WSTR**||Der Name des Measures, der nicht mit dem Namen der Measuregruppe qualifiziert ist.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Der Name der Measuregruppe, zu der dieses Measure gehört.|  
|**MEASURE_DISPLAY_FOLDER**|**DBTYPE_WSTR**||Der zu verwendende Pfad beim Anzeigen des Measures in der Benutzeroberfläche. Ordnernamen werden durch ein Semikolon voneinander getrennt. Geschachtelte Ordner werden durch einen umgekehrten Schrägstrich angegeben (\\).|  
|**DEFAULT_FORMAT_STRING**|**DBTYPE_WSTR**||Die Standardformatzeichenfolge für das Measure.|  
  
 Das Rowset wird sortiert nach **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**, **MEASURE_NAME**.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die **MDSCHEMA_MEASURES** Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Optional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**MEASURE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**MEASURE_UNIQUE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Optional) Standardeinschränkung besitzt den Wert 1. Eine Bitmap mit einem der folgenden gültigen Werten:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**MEASURE_VISIBILITY**|**DBTYPE_UI2**|(Optional) Standardeinschränkung besitzt den Wert 1. Eine Bitmap mit einem der folgenden gültigen Werten:<br /><br /> 1 Sichtbar<br /><br /> 2 Nicht sichtbar|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
