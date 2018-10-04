---
title: Abrufen von Metadaten aus einer analytischen Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- metadata [ADOMD.NET]
- retrieving metadata
ms.assetid: 00043ebd-7164-4ceb-b945-6e44378ea00a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 654ea55f3b285409dab5e3f1cf178b8ff7818bcd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153050"
---
# <a name="retrieving-metadata-from-an-analytical-data-source"></a>Abrufen von Metadaten aus einer analytischen Datenquelle
  Metadaten sind wichtig für Anwendungen, die analytische Daten abrufen und damit arbeiten. Beim Abrufen von Daten aus einer relationalen Datenquelle ist die Dimensionalität dieser Daten selbst bei geschachtelten Datasets vorhersehbar. Resultsets aus einer relationalen Datenbank haben meist eine zweidimensionale oder skalare Struktur. Aus analytischen Datenquellen abgerufene Daten können jedoch eine variable Dimensionalität aufweisen und möglicherweise entlang tiefer Hierarchien organisiert sein.  
  
 Um der Komplexität des Metadatenabrufs aus analytischen Datenquellen zu begegnen, bietet ADOMD.NET zwei Arten des Metadatenabrufs:  
  
 **Das Objektmodell**  
 Das ADOMD.NET-Objektmodell ist im Allgemeinen leichter zu verwenden als Schemarowsets. Bei den meisten Szenarien können Sie auf die Metadaten verschiedener Datenbankobjekte zugreifen, indem Sie einfach das Objektmodell verwenden. ADOMD.NET macht das Objektmodell durch die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Weitere Informationen: [arbeiten mit dem ADOMD.NET-Objektmodell](retrieving-metadata-working-with-adomd-net-object-model.md)  
  
 **Schemarowsets**  
 Ein vollständiger, aber schwierigerer Ansatz für das Abrufen von Metadaten besteht in der Verwendung von Schemarowsets. Ein Schemarowset ist ein OLE DB-Rowset, das die Beschreibung für alle Objekte einer bestimmten Art in der Datenbank einschließt. Zu den Schemainformationen in einer analytischen Datenquelle gehören die über die analytische Datenquelle verfügbaren Datenbanken und Kataloge, Cubes und Miningmodelle in einer Datenbank, für Cubes in der Datenbank bestehende Rollen usw. Diese Metadaten können mit der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>-Methode abgerufen werden, wobei entweder `GUID` oder ein XML for Analysis (XMLA)-Name übergeben wird.  
  
 Weitere Informationen: [arbeiten mit Schemarowsets in ADOMD.NET](retrieving-metadata-working-with-schema-rowsets.md))  
  
 Jede dieser Methoden zum Abrufen von Metadaten greift auf andere Arten von Metadaten zu. In der folgenden Tabelle werden die bei den einzelnen Methoden verfügbaren, verschiedenen Metadaten und die Methoden für den Zugriff darauf beschrieben.  
  
|GUID (in Schemarowsets verwendet)|XMLA-Name (in Schemarowsets verwendet)|ADOMD.NET-Objektmodell|  
|-------------------------------------|------------------------------------------|----------------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Actions>|[MDSCHEMA_ACTIONS-Rowset](../schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Catalogs>|[DBSCHEMA_CATALOGS-Rowset](../schema-rowsets/ole-db/dbschema-catalogs-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Columns>|[DBSCHEMA_COLUMNS-Rowset](../schema-rowsets/ole-db/dbschema-columns-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Connections>|`DISCOVER_CONNECTIONS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Cubes>|[MDSCHEMA_CUBES-Rowset](../schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|AdomdConnection.Cubes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DataSources>|[DISCOVER_DATASOURCES-Rowset](../schema-rowsets/xml/discover-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DBConnections>|`DISCOVER_DB_CONNECTIONS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Dimensions>|[MDSCHEMA_DIMENSIONS-Rowset](../schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|AdomdConnection.Cubes[].Dimensionen|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DimensionStat>|`DISCOVER_DIMENSION_STAT`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Enumerators>|[DISCOVER_ENUMERATORS-Rowset](../schema-rowsets/xml/discover-enumerators-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Functions>|[MDSCHEMA_FUNCTIONS-Rowset](../schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Hierarchies>|[MDSCHEMA_HIERARCHIES-Rowset](../schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|AdomdConnection.Cubes[].Dimensionen[].Hierarchien|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.InputDataSources>|[MDSCHEMA_INPUT_DATASOURCES-Rowset](../schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Instances>|[DISCOVER_INSTANCES-Rowset](../schema-rowsets/ole-db-olap/discover-instances-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Jobs>|`DISCOVER_JOBS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Keywords>|[DISCOVER_KEYWORDS-Rowset &#40;OLE DB für OLAP&#41;](../schema-rowsets/ole-db-olap/discover-keywords-rowset-ole-db-for-olap.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Kpis>|[MDSCHEMA_KPIS-Rowset](../schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|AdomdConnection.Cubes[].KPIs|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Levels>|[MDSCHEMA_LEVELS-Rowset](../schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|AdomdConnection.Cubes[].Dimensionen[].Hierarchien[].Ebenen|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Literals>|[DISCOVER_LITERALS-Rowset](../schema-rowsets/xml/discover-literals-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locations>|`DISCOVER_LOCATIONS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locks>|`DISCOVER_LOCKS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MasterKey>|`DISCOVER_MASTER_KEY`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroupDimensions>|[MDSCHEMA_MEASUREGROUP_DIMENSIONS-Rowset](../schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroups>|[MDSCHEMA_MEASUREGROUPS-Rowset](../schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Measures>|[MDSCHEMA_MEASURES-Rowset](../schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|AdomdConnection.Cubes[].Measures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemberProperties>|[MDSCHEMA_PROPERTIES-Rowset](../schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|PropertyCollection verfügbar aus den meisten ADOMD.NET-Hauptobjekten.|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Members>|[MDSCHEMA_MEMBERS-Rowset](../schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|AdomdConnection.Cubes[].Dimensionen[].Hierarchien[].Ebenen[].GetMembers()|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryGrant>|`DISCOVER_MEMORYGRANT`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryUsage>|`DISCOVER_MEMORYUSAGE`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningColumns>|[DMSCHEMA_MINING_COLUMNS-Rowset](../schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|AdomdConnection.MiningModels[].MiningModelColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningFunctions>|[DMSCHEMA_MINING_FUNCTIONS-Rowset](../schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContent>|[DMSCHEMA_MINING_MODEL_CONTENT-Rowset](../schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|AdomdConnection.MiningModels[].MiningContentNodes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContentPmml>|[DMSCHEMA_MINING_MODEL_CONTENT_PMML-Rowset](../schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModels>|[DMSCHEMA_MINING_MODELS-Rowset](../schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|AdomdConnection.MiningModels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelXml>|[DMSCHEMA_MINING_MODEL_XML-Rowset](../schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServiceParameters>|[DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset](../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|AdomdConnection.MiningServices[].MiningServiceParameters|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServices>|[DMSCHEMA_MINING_SERVICES-Rowset](../schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|AdomdConnection.MiningServices|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructureColumns>|[DMSCHEMA_MINING_STRUCTURE_COLUMNS-Rowset](../schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|AdomdConnection.MiningStructures[].MiningStructureColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructures>|[DMSCHEMA_MINING_STRUCTURES-Rowset](../schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|AdomdConnection.MiningStructures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionDimensionStat>|`DISCOVER_PARTITION_DIMENSION_STAT`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionStat>|`DISCOVER_PARTITION_STAT`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PerformanceCounters>|`DISCOVER_PERFORMANCE_COUNTERS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.ProviderTypes>|[DBSCHEMA_PROVIDER_TYPES-Rowset](../schema-rowsets/ole-db/dbschema-provider-types-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.SchemaRowsets>|[DISCOVER_SCHEMA_ROWSETS-Rowsets](../schema-rowsets/xml/discover-schema-rowsets-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sessions>|`DISCOVER_SESSIONS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sets>|[MDSCHEMA_SETS-Rowset](../schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|AdomdConnection.Cubes[].NamedSets|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Tables>|[DBSCHEMA_TABLES-Rowset](../schema-rowsets/ole-db/dbschema-tables-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TablesInfo>|`DBSCHEMA_TABLES_INFO`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceColumns>|`DISCOVER_TRACE_COLUMNS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceDefinitionProviderInfo>|`DISCOVER_TRACE_DEFINITION_PROVIDERINFO`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceEventCategories>|`DISCOVER_TRACE_EVENT_CATEGORIES`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Traces>|`DISCOVER_TRACES`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Transactions>|`DISCOVER_TRANSACTIONS`||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlaProperties>|[DISCOVER_PROPERTIES-Rowset](../schema-rowsets/xml/discover-properties-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlMetadata>|[DISCOVER_XML_METADATA-Rowset](../schema-rowsets/xml/discover-xml-metadata-rowset.md)||  
  
## <a name="see-also"></a>Siehe auch  
 [ADOMD.NET-Clientprogrammierung](adomd-net-client-programming.md)   
 [ADOMD.NET-Clientprogrammierung](adomd-net-client-programming.md)   
 [Analysis Services-Schemarowsets](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
