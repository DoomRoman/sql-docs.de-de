---
title: Verwenden von sicheren Webdienstmethoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server-web-service
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 0595f9df191bb1a4ad53c6934d85c701a80520bd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="using-secure-web-service-methods"></a>Verwenden von sicheren Webdienstmethoden
  Es kann sein, dass für bestimmte Berichtsserver-Webdienstmethoden eine sichere Verbindung erforderlich ist, wenn Sie diese aufrufen. Die Methoden, die eine sichere Verbindung benötigen, werden von der Einstellung **SecureConnectionLevel**(sichere Verbindungsebene) in der Datei „RSReportServer.config“ bestimmt. Der Wert der Einstellung ist ein ganzzahliger Wert im gültigen Bereich von 0 und höher. In der folgenden Tabelle werden diese Werte beschrieben.  
  
|Ebene|Description|  
|-----------|-----------------|  
|**0**|Nicht sicher. Aufrufe an die Reporting Services-SOAP-API benötigen keine sichere Verbindung.|  
|Größer als **0**|Sicher. Alle Aufrufe an die Reporting Services-SOAP-API benötigen eine sichere Verbindung.|  
  
 Sie können mithilfe der <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>-Methode des Webdiensts eine Liste der Webdienstmethoden zurückgeben, die entsprechend der aktuellen Konfiguration des Berichtsservers eine sichere Verbindung benötigen. In einem SSL-Szenario sollten Sie die Liste der von <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> zurückgegebenen Methoden überprüfen und den Schema-Namen der Webdienst-URI entsprechend der aufgerufenen Methode in "https" oder "http" ändern.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Report Server Web Service (Report Server-Webdienst)](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
