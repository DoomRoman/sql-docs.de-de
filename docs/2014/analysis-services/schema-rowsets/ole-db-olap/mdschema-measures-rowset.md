---
title: MDSCHEMA_MEASURES-Rowset | Microsoft Docs
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
- MDSCHEMA_MEASURES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASURES rowset
ms.assetid: 6ff5bd1a-aad0-49b8-9f8d-7df2637caacf
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6608c64caa882499282ad7a7e30090ab4118b522
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046281"
---
# <a name="mdschemameasures-rowset"></a>MDSCHEMA_MEASURES-Rowset
  Beschreibt jedes Measure innerhalb eines Cubes.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_MEASURES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name des Katalogs, zu dem dieses Measure gehört. `NULL`, wenn der Anbieter keine Kataloge unterstützt.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Der Name des Schemas, zu dem dieses Measure gehört. `NULL`, wenn der Anbieter keine Schemas unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes, zu dem dieses Measure gehört.|  
|`MEASURE_NAME`|`DBTYPE_WSTR`||Der Name des Measures.|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name des Measures. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`MEASURE_CAPTION`|`DBTYPE_WSTR`||Eine Bezeichnung oder Beschriftung, die dem Measure zugeordnet ist. Wird hauptsächlich für Anzeigezwecke verwendet. Wenn keine Beschriftung vorhanden ist, wird `MEASURE_NAME` zurückgegeben.|  
|`MEASURE_GUID`|`DBTYPE_GUID`||Wird nicht unterstützt.|  
|`MEASURE_AGGREGATOR`|`DBTYPE_I4`||Eine Enumeration, die angibt, wie ein Measure abgeleitet wurde. Folgende Werte sind möglich:<br /><br /> -   `MDMEASURE_AGGR_SUM` (`1`) gibt an, dass das Measure aus aggregierten `SUM`.<br />-   `MDMEASURE_AGGR_COUNT` (`2`) gibt an, dass das Measure aus aggregierten `COUNT`.<br />-   **MDMEASURE_AGGR_MIN** (`3`) gibt an, dass das Measure aus aggregierten `MIN`.<br />-   **MDMEASURE_AGGR_MAX** (`4`) gibt an, dass das Measure aus aggregierten `MAX`.<br />-   `MDMEASURE_AGGR_AVG` (`5`) gibt an, dass das Measure aus aggregierten `AVG`.<br />-   `MDMEASURE_AGGR_VAR` (`6`) gibt an, dass das Measure aus aggregierten `VAR`.<br />-   `MDMEASURE_AGGR_STD` (`7`) gibt an, dass das Measure aus aggregierten `STDEV`.<br />-   `MDMEASURE_AGGR_DST` (`8`) gibt an, dass das Measure aus aggregierten `DISTINCT COUNT`.<br />-   `MDMEASURE_AGGR_NONE` (`9`) gibt an, dass das Measure aus aggregierten `NONE`.<br />-   `MDMEASURE_AGGR_AVGCHILDREN` (`10`) gibt an, dass das Measure aus aggregierten `AVERAGEOFCHILDREN`.<br />-   `MDMEASURE_AGGR_FIRSTCHILD` (`11`) gibt an, dass das Measure aus aggregierten `FIRSTCHILD`.<br />-   `MDMEASURE_AGGR_LASTCHILD` (`12`) gibt an, dass das Measure aus aggregierten `LASTCHILD`.<br />-   `MDMEASURE_AGGR_FIRSTNONEMPTY` (`13`) gibt an, dass das Measure aus aggregierten `FIRSTNONEMPTY`,<br />-   `MDMEASURE_AGGR_LASTNONEMPTY` (`14`) gibt an, dass das Measure aus aggregierten `LASTNONEMPTY`.<br />-   `MDMEASURE_AGGR_BYACCOUNT` (`15`) gibt an, dass das Measure aus aggregierten `BYACCOUNT`.<br />-   `MDMEASURE_AGGR_CALCULATED` (`127`) gibt an, dass das Measure aus einer Formel abgeleitet wurde, die nicht die oben genannten Einzelfunktionen war.<br />-   `MDMEASURE_AGGR_UNKNOWN` (`0`) gibt an, dass das Measure aus einer unbekannten Aggregatfunktion oder Formel abgeleitet wurde.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Der Datentyp des Measures.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Die maximale Genauigkeit der Eigenschaft, wenn der Datentyp des Measureobjekts genau numerisch ist. `NULL` für alle anderen Eigenschaftentypen.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Die Anzahl der Stellen rechts neben dem Dezimalzeichen, wenn der Typindikator des Measureobjekts `DBTYPE_NUMERIC` oder `DBTYPE_DECIMAL` ist. Andernfalls wird dieser Wert `NULL`.|  
|`MEASURE_UNITS`|`DBTYPE_WSTR`||Nicht unterstützt|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung des Measures. `NULL`, wenn keine Beschreibung vorhanden ist.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Ein Ausdruck für das Element.|  
|`MEASURE_IS_VISIBLE`|`DBTYPE_BOOL`||Ein boolescher Wert zurückgegeben, die immer "true". Wenn das Measure nicht sichtbar ist, wird es nicht im Schemarowset angezeigt.|  
|`LEVELS_LIST`|`DBTYPE_WSTR`||Eine Zeichenfolge, die immer`NULL` zurückgibt.|  
|`MEASURE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Der Name der Spalte in der SQL-Abfrage, die dem Namen des Measures entspricht.|  
|`MEASURE_UNQUALIFIED_CAPTION`|`DBTYPE_WSTR`||Der Name des Measures, der nicht mit dem Namen der Measuregruppe qualifiziert ist.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Der Name der Measuregruppe, zu der dieses Measure gehört.|  
|`MEASURE_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Der zu verwendende Pfad beim Anzeigen des Measures in der Benutzeroberfläche. Ordnernamen werden durch ein Semikolon voneinander getrennt. Geschachtelte Ordner werden durch einen umgekehrten Schrägstrich angegeben (\\).|  
|`DEFAULT_FORMAT_STRING`|`DBTYPE_WSTR`||Die Standardformatzeichenfolge für das Measure.|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `MEASURE_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_MEASURES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MEASURE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-CUBE<br />-2-DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
|`MEASURE_VISIBILITY`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -Visible 1<br />-2 nicht sichtbar<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  