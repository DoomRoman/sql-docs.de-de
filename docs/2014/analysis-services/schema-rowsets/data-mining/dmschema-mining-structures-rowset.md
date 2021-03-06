---
title: DMSCHEMA_MINING_STRUCTURES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_STRUCTURES
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURES rowset
ms.assetid: 6224556b-08a0-496e-bd7c-632c3e833e26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 252bd8e96d608314e8030c9bc9e2743df8e23e02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135980"
---
# <a name="dmschemaminingstructures-rowset"></a>DMSCHEMA_MINING_STRUCTURES-Rowset
  Listet Informationen über die Miningstrukturen im aktuellen Katalog auf.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_STRUCTURES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`||Der Katalogname.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`||Der nicht gekennzeichnete Schemaname. `NULL`, wenn vom Anbieter keine Schemas unterstützt werden.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`||Der Name der Struktur. Diese Spalte darf nicht enthalten `NULL`.|  
|`STRUCTURE_GUID`|`DBTYPE_GUID`||Eine GUID, die die Struktur eindeutig bezeichnet. `NULL` Wenn vom Anbieter nicht unterstützt wird.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine knappe Beschreibung der Struktur. `NULL` Wenn keine Beschreibung der Struktur zugeordnet ist.|  
|`STRUCTURE_PROPID`|`DBTYPE_UI4`||Die Eigenschaften-ID der Struktur. `NULL` Wenn vom Anbieter nicht unterstützt wird.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem die Struktur erstellt wurde. `NULL` Wenn vom Anbieter nicht verfügbar.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem die Struktur zuletzt geändert wurde. `NULL` Wenn vom Anbieter nicht verfügbar.|  
|`CREATION_STATEMENT`|`DBTYPE_WSTR`||(Optional) Die für die Erstellung des ursprünglichen Data Mining-Modells verwendete Anweisung.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Struktur aufgefüllt wurde.<br /><br /> `VARIANT_TRUE` Wenn die Struktur aufgefüllt wurde, `VARIANT_FALSE` andernfalls.|  
|`LAST_PROCESSED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem die Struktur zuletzt verarbeitet wurde. `NULL` Wenn vom Anbieter nicht verfügbar.|  
|`HOLDOUT_MAXPERCENT`|`DBTYPE_ UI1`||Benutzerdefinierter Wert, der den maximalen Prozentsatz der Eingabefälle angibt, die als Testsatz zurückgehalten werden.<br /><br /> 0 oder `NULL` gilt keine Begrenzung.|  
|`HOLDOUT_MAXCASES`|`DBTYPE_UI8`||Benutzerdefinierter Wert, der die maximale Anzahl der Eingabefälle angibt, die als Testsatz zurückgehalten werden.<br /><br /> 0 oder `NULL` gilt keine Begrenzung.|  
|`HOLDOUT_SEED`|`DBTYPE_UI8`||Benutzerdefinierter Wert, der als Ausgangswert für wiederholbare Partitionierungen verwendet wird.<br /><br /> 0 gibt an, dass ein Hash der Miningstruktur-ID als Ausgangswert verwendet wird.|  
|`HOLDOUT_ACTUAL_SIZE`|`DBTYPE_UI8`||Wenn die Miningstruktur verwendet wird, wird hier die tatsächliche Größe des Testdatensatzen angegeben, ausgedrückt in Anzahl von Fällen.<br /><br /> `NULL` gibt an, dass die Miningstruktur nicht verarbeitet wird.|  
  
 Das Rowset wird sortiert nach `STRUCTURE_CATALOG`, `STRUCTURE_SCHEMA`, `STRUCTURE_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DMSCHEMA_MINING_STRUCTURES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`|Optional.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`|Optional.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
