---
title: DISCOVER_COMMANDS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ba32ff2992e02b8b9e3fe452544f3a9b978d34f6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028781"
---
# <a name="discovercommands-rowset"></a>DISCOVER_COMMANDS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Stellt Ressourcenverwendungs- und Aktivitätsinformationen über die zurzeit ausgeführten oder zuletzt ausgeführten Befehle auf den offenen Verbindungen auf dem Server bereit.  
  
 **Gilt für:** tabellarische und mehrdimensionale Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_COMMANDS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Einschränkung|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|ja|Die Sitzungs-ID.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Die Anzahl der seit dem Start der Sitzung ausgeführten Befehle.|  
|**COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Das Datum und die Uhrzeit, zu denen der letzte Befehl gestartet wurde, ausgedrückt als UTC-Zeit auf dem Server.|  
|**COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**||Die seit dem Start des Befehls verstrichene Zeit in Millisekunden.|  
|**COMMAND_CPU_TIME_MS**|**DBTYPE_I8**||Die CPU-Zeit in Millisekunden, die seit dem Start der Befehlsausführung von dem Befehl beansprucht wurde.|  
|**COMMAND_READS**|**DBTYPE_I8**||Die akkumulierte Anzahl der seit dem Start des Befehls erfolgten Lesevorgänge auf dem Datenträger.|  
|**COMMAND_READ_KB**|**DBTYPE_I8**||Der akkumulierte Wert der seit dem Start des Befehls vom Datenträger gelesenen Daten in KB.|  
|**COMMAND_WRITES**|**DBTYPE_I8**||Die akkumulierte Anzahl der seit dem Start des Befehls erfolgten Schreibvorgänge auf dem Datenträger.|  
|**COMMAND_WRITE_KB**|**DBTYPE_I8**||Der akkumulierte Wert der seit dem Start des Befehls auf den Datenträger geschriebenen Daten in KB.|  
|**COMMAND_TEXT**|**DBTYPE_WSTR**||Der Befehlstext.|  
|**COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||UTC-Datum und -Zeit des Servers, zu denen der Befehl seine Ausführung beendet.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|Wert|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Befehle|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
