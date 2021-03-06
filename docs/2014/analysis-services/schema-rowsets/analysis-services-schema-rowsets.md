---
title: Analysis Services-Schemarowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- SSAS, data access interfaces
- Analysis Services data access interfaces, schema rowsets
- data access interfaces [Analysis Services]
- XML for Analysis, schema rowsets
- rowsets [Analysis Services], retrieving schema rowsets
- retrieving schema rowsets
- XMLA, schema rowsets
- rowsets [Analysis Services]
- schema rowsets [Analysis Services], retrieving
ms.assetid: 820d4b59-d428-4616-b792-c848e5da407e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 474de14a40b24fe113cebf1c933f7e28a351d5bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227900"
---
# <a name="analysis-services-schema-rowsets"></a>Analysis Services-Schemarowsets
  Schemarowsets sind vordefinierte Tabellen, die Informationen zu Analysis Services-Objekten und zum Serverstatus enthalten, einschließlich Datenbankschema, aktive Sitzungen, Verbindungen, Befehle und Aufträge, die auf dem Server ausgeführt werden. Sie können Schemarowsettabellen in einem XML/A-Skriptfenster in SQL Server Management Studio abfragen, eine DMV-Abfrage für ein Schemarowset ausführen oder eine benutzerdefinierte Anwendung erstellen, die Schemarowsetinformationen enthält (z. B. eine Berichterstellungsanwendung, durch die die Liste der verfügbaren Dimensionen abgerufen wird, die zum Erstellen eines Berichts verwendet werden können).  
  
> [!NOTE]  
>  Bei Verwendung von Schemarowsets im XML/A-Skripts, die Informationen, die in zurückgegeben wird die *Ergebnis* Parameter, der die [Discover](../xmla/xml-elements-methods-discover.md) -Methode ist entsprechend der in diesem beschriebenen rowsetspaltenlayouts strukturiert Abschnitt. Vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) werden die Rowsets unterstützt, die von der XML for Analysis-Spezifikation benötigt werden. Einige der standardmäßigen Schemarowsets für OLE DB, OLE DB für OLAP und OLE DB für Data Mining-Datenquellenanbieter werden vom XMLA-Anbieter ebenfalls unterstützt. Die unterstützten Rowsets werden in den folgenden Themen beschrieben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[XML for Analysis – Schemarowsets](xml/xml-for-analysis-schema-rowsets.md)|Beschreibt die vom XMLA-Anbieter unterstützten XMLA-Rowsets.|  
|[OLE DB-Schemarowsets](ole-db/ole-db-schema-rowsets.md)|Beschreibt die vom XMLA-Anbieter unterstützten OLE DB-Schemarowsets.|  
|[OLE DB für OLAP-Schemarowsets](ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Beschreibt die vom XMLA-Anbieter unterstützten OLE DB für OLAP-Schemarowsets.|  
|[Data Mining Schema Rowsets](data-mining/data-mining-schema-rowsets.md)|Beschreibt die vom XMLA-Anbieter unterstützten Data Mining-Schemarowsets.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zugriff auf mehrdimensionale Modelldaten &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Verwenden von dynamischen Verwaltungssichten &#40;DMVs&#41; zum Überwachen von Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
