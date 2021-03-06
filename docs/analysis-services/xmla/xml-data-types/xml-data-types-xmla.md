---
title: XML-Datentypen (XMLA) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c52717a6f061f4708b2d3e46c6d34f837b2039af
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37981132"
---
# <a name="xml-data-types-xmla"></a>XML-Datentypen (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Zusätzlich zu den von der XML 1.0-Empfehlung definierten standardmäßigen Grundtypen und abgeleiteten Typen definiert die XMLA 1.1-Spezifikation (XML for Analysis) zusätzliche Datentypen, um die Darstellung von mehrdimensionalen und tabellarischen Daten zu unterstützen.  
  
 XMLA verwendet die in der folgenden Tabelle aufgelisteten Datentypen.  
  
|Datentypen|Description|  
|----------------|-----------------|  
|Boolean|Der **boolean** -XML-Standarddatentyp.|  
|Decimal|Der **decimal** -XML-Standarddatentyp.|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|Ein Namespace auf dem **root** -Element. Dieser Namespace wird zurückgegeben, wenn ein XMLA-Befehl kein Ergebnis zurückgibt, weil der XMLA-Befehl nicht normalerweise kein Ergebnis zurückgibt oder auf der Analysis Services-Instanz beim Ausführen des XMLA-Befehls Fehler.|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|Ein Satz genannter Zeichenfolgenkonstanten für einen gegebenen Enumerator.|  
|Integer|Der **int** -XML-Standarddatentyp.|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|Mehrdimensionale Daten, die zurückgegeben werden, indem die *Ergebnis* Parameter der [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methode.|  
|[Resultset](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|Ein selbstbeschreibendes XML-Resultset, das von der **Execute** -Methode zurückgegeben wird.|  
|[Rowset](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|Zeilen aus einer Datenquelle, die von einem eingebetteten XML-Schema strukturiert wurden zurückgegeben, indem die [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) Methode.|  
|Zeichenfolge|Der **string** -XML-Standarddatentyp.|  
|UnsignedInt|Der **unsignedInt** -XML-Schematyp.|  
  
 Vollständige Beschreibungen der XML-Standarddatentypen finden Sie in den Kandidatenempfehlungen des World Wide Web Consortium (WC3).  
  
## <a name="see-also"></a>Siehe auch
 [XML-Elemente &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML for Analysis &#40;XMLA&#41; Verweis](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
