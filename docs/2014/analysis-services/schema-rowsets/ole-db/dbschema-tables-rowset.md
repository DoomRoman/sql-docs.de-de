---
title: DBSCHEMA_TABLES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DBSCHEMA_TABLES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 66780a650e3187f3ec62831fd2badf331a1fca4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153160"
---
# <a name="dbschematables-rowset"></a>DBSCHEMA_TABLES-Rowset
  Gibt die Measuregruppen und Dimensionen, die verfügbar gemacht werden, als Tabellen in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DBSCHEMA_TABLES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|255|Der Name des Katalogs, zu dem dieses Objekt gehört.|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|255|Der Name des Cubes, zu dem dieses Objekt gehört.|  
|`TABLE_NAME`|`DBTYPE_WSTR`|255|Der Name des Objekts, wenn `TABLE_TYPE` `TABLE` lautet.|  
|`TABLE_TYPE`|`DBTYPE_WSTR`||Der Typ der Tabelle.<br /><br /> `TABLE` gibt an, dass das Objekt eine Measuregruppe ist.<br /><br /> `SYSTEM TABLE` Gibt an, dass das Objekt eine Dimension ist.|  
|`TABLE_GUID`|`DBTYPE_GUID`||Wird nicht unterstützt.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung des Objekts.|  
|`TABLE_PROPID`|`DBTYPE_UI4`||Wird nicht unterstützt.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Wird nicht unterstützt.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem das Objekt zuletzt geändert wurde.|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`||Den OLAP-Typ des Objekts.<br /><br /> **MEASURE_GROUP** gibt an, dass das Objekt eine Measuregruppe ist.<br /><br /> `CUBE_DIMENSION` gibt an, dass das Objekt eine Dimension ist.|  
  
 Das Rowset wird sortiert nach `TABLE_TYPE`, `TABLE_CATALOG`, `TABLE_SCHEMA`, und `TABLE_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DBSCHEMA_TABLES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|Optional|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|Optional|  
|`TABLE_NAME`|`DBTYPE_WSTR`|Optional|  
|`TABLE_TYPE`|`DBTYPE_WSTR`|Optional|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`|Optional|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Schemarowsets](ole-db-schema-rowsets.md)  
  
  
