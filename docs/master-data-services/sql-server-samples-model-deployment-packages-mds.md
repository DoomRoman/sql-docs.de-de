---
title: 'SQL Server-Beispiele: Modellbereitstellungspakete (MDS) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 07/28/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
keywords:
- Master Data Services
- Beispiel
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b5b07e836d2e1f23f89c6dc992a080b8ab0e85fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843158"
---
# <a name="sql-server-examples-model-deployment-packages-mds"></a>SQL Server-Beispiele: Modellbereitstellungspakete (MDS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Beispiele von Modellpaketen mit Daten sind in der Installation von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]enthalten. Der Standardspeicherort für die Pakete ist \<Laufwerk>\Programme\Microsoft SQL Server\130\Master Data Services\Samples\Packages.  
  
 Eine Anleitung zum Bereitstellen der Beispielmodellpakete finden Sie unter [Bereitstellen von Beispielmodelle und Daten](../master-data-services/master-data-services-installation-and-configuration.md#deploySample). Stellen Sie diese Beispielmodellpakete mit dem [MDSModelDeploy-Tool](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)bereit.  
  
> [!IMPORTANT]  
>  **Beispiel-Updates in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**  
>   
>  Die Beispielpakete wurden aktualisiert, um die folgenden neuen Funktionen zu unterstützen.  
>   
>  -   m:n-Beziehungen anzeigen  
>   
>      Weitere Informationen finden Sie unter [Eine m:n-Beziehung in einem Beispielmodell](../master-data-services/show-many-to-many-relationships-in-derived-hierarchies-master-data-services.md#M2MSample).  

> -   Schränken Sie zulässige Werte für domänenbasierte Attribute ein.  
>   
>      Weitere Informationen finden Sie unter [Erstellen eines domänenbasierten Attributs &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md).  
> -   Genehmigung für Änderungen an Entitäten anfordern  
>   
>      Weitere Informationen finden Sie unter [Genehmigung erforderlich &#40;Master Data Services&#41;](../master-data-services/approval-required-master-data-services.md).  
> -   Geschäftsregeln mit Not- und Else-Operatoren verwenden  
>   
>      Weitere Informationen finden Sie unter [Beispiele für Geschäftsregeln](../master-data-services/business-rule-examples-master-data-services.md).  
> -   Benutzerdefinierten Index implementieren  
>   
>      Weitere Informationen finden Sie unter [Benutzerdefinierter Index &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md).  
 

 
 In Master Data Services ist ein Paket eine XML-Datei, die eine zur Bereitstellung geeignete Modellstruktur enthält und optional Daten vom Modell. Verschieben Sie Kopien von Modellen mithilfe von Modellpaketen von einer MDS-Umgebung in eine andere, oder erstellen Sie neue Modelle in Ihrer vorhandenen [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Umgebung.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Bereitstellen eines Modellbereitstellungspakets mit MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
