---
title: ParentObject-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ParentObject Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ParentObject
- http://schemas.microsoft.com/analysisservices/2003/engine#ParentObject
- microsoft.xml.analysis.parentobject
helpviewer_keywords:
- ParentObject element
ms.assetid: f821f8f1-554a-4f16-bf09-262a9448e304
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04feffe81c9f42344748713161a81310ddf65e11
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089120"
---
# <a name="parentobject-element-xmla"></a>ParentObject-Element (XMLA)
  Enthält den Bezeichner des übergeordneten Objekts, unter dem die vom übergeordneten Element definierten Objekte erstellt [erstellen](../xml-elements-commands/create-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Create>  
   ...  
   <ParentObject>  
      <!-- Object reference -->  
   </ParentObject>  
   ...  
</Create>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Erstellen](../xml-elements-commands/create-element-xmla.md)|  
|Untergeordnete Elemente|Benötigt Analysis Services Scripting Language-XML-Elemente (ASSL). Werden durch Auflisten der ID-Elemente des Objekts und seiner Vorgänger (ohne das `Server`-Objekt.) angegeben Beispielsweise die folgenden `ParentObject` Element identifiziert eine Partition:<br /><br /> `<ParentObject>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</ParentObject>`|  
  
## <a name="remarks"></a>Hinweise  
 Die Reihenfolge, in der Bezeichner angezeigt werden, ist nicht wichtig.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt die `Market Basket` Miningstruktur enthalten, die der [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] Beispiel [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank.  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>database</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningStructure xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Market Basket</ID>  
            <Name>Market Basket</Name>  
            <Source xsi:type="DataSourceViewBinding">  
                <DataSourceViewID>Adventure Works DW</DataSourceViewID>  
            </Source>  
            <Language>1033</Language>  
            <Collation>Latin1_General_CI_AS</Collation>  
            <Columns>  
                <Column xsi:type="ScalarMiningStructureColumn">  
                    <ID>Order Number</ID>  
                    <Name>Order Number</Name>  
                    <IsKey>true</IsKey>  
                    <Type>Text</Type>  
                    <Content>Key</Content>  
                    <KeyColumns>  
                        <KeyColumn>  
                            <NullProcessing>Error</NullProcessing>  
                            <DataType>WChar</DataType>  
                            <DataSize>20</DataSize>  
                            <Source xsi:type="ColumnBinding">  
                                <TableID>dbo_vAssocSeqOrders</TableID>  
                                <ColumnID>OrderNumber</ColumnID>  
                            </Source>  
                        </KeyColumn>  
                    </KeyColumns>  
                </Column>  
                <Column xsi:type="TableMiningStructureColumn">  
                    <Annotations>  
                        <Annotation>  
                            <Name>MDXFilterComponent</Name>  
                            <Value />  
                        </Annotation>  
                    </Annotations>  
                    <ID>v Assoc Seq Line Items</ID>  
                    <Name>v Assoc Seq Line Items</Name>  
                    <ForeignKeyColumns>  
                        <ForeignKeyColumn>  
                            <NullProcessing>Error</NullProcessing>  
                            <DataType>WChar</DataType>  
                            <DataSize>20</DataSize>  
                            <Source xsi:type="ColumnBinding">  
                                <TableID>dbo_vAssocSeqLineItems</TableID>  
                                <ColumnID>OrderNumber</ColumnID>  
                            </Source>  
                        </ForeignKeyColumn>  
                    </ForeignKeyColumns>  
                    <Columns>  
                        <Column xsi:type="ScalarMiningStructureColumn">  
                            <ID>Model</ID>  
                            <Name>Model</Name>  
                            <IsKey>true</IsKey>  
                            <Type>Text</Type>  
                            <Content>Key</Content>  
                            <KeyColumns>  
                                <KeyColumn>  
                                    <DataType>WChar</DataType>  
                                    <DataSize>50</DataSize>  
                                    <Source xsi:type="ColumnBinding">  
                                        <TableID>dbo_vAssocSeqLineItems</TableID>  
                                        <ColumnID>Model</ColumnID>  
                                    </Source>  
                                </KeyColumn>  
                            </KeyColumns>  
                        </Column>  
                    </Columns>  
                </Column>  
            </Columns>  
            <MiningModels>  
                <MiningModel>  
                    <ID>Market Basket</ID>  
                    <Name>Association</Name>  
                    <Algorithm>Microsoft_Association_Rules</Algorithm>  
                    <AlgorithmParameters>  
                        <AlgorithmParameter>  
                            <Name>MINIMUM_PROBABILITY</Name>  
                            <Value xsi:type="xsd:double">0.1</Value>  
                        </AlgorithmParameter>  
                        <AlgorithmParameter>  
                            <Name>MINIMUM_SUPPORT</Name>  
                            <Value xsi:type="xsd:double">0.01</Value>  
                        </AlgorithmParameter>  
                    </AlgorithmParameters>  
                    <Columns>  
                        <Column>  
                            <ID>Order Number</ID>  
                            <Name>Order Number</Name>  
                            <SourceColumnID>Order Number</SourceColumnID>  
                            <Usage>Key</Usage>  
                        </Column>  
                        <Column>  
                            <ID>v Assoc Seq Line Items</ID>  
                            <Name>v Assoc Seq Line Items</Name>  
                            <SourceColumnID>v Assoc Seq Line Items</SourceColumnID>  
                            <Usage>Predict</Usage>  
                            <Columns>  
                                <Column>  
                                    <ID>Model</ID>  
                                    <Name>Model</Name>  
                                    <SourceColumnID>Model</SourceColumnID>  
                                    <Usage>Key</Usage>  
                                </Column>  
                            </Columns>  
                        </Column>  
                    </Columns>  
                    <Language>1033</Language>  
                    <Collation>Latin1_General_CI_AS</Collation>  
                </MiningModel>  
            </MiningModels>  
        </MiningStructure>  
    </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
