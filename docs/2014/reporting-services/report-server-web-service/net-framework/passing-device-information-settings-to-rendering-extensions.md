---
title: Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
caps.latest.revision: 46
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9fc300712ecac2eeb4e13257515e1300e704d21c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240220"
---
# <a name="passing-device-information-settings-to-rendering-extensions"></a>Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen
  In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]werden Geräteinformationseinstellungen zum Übergeben von Renderingparametern an eine Renderingerweiterung verwendet. Einstellungen im Berichtsserver-Webdienst werden als **DeviceInfo** -XML-Element übergeben und vom Berichtsserver verarbeitet. Da Geräteinformationseinstellungen Standardwerte besitzen, werden sie als optionale Argumente für das Rendern angesehen. Sie können jedoch Geräteinformationseinstellungen verwenden, um das Rendern anzupassen und die vom Server angegebenen Standardwerte zu überschreiben.  
  
 Die Geräteinformationseinstellungen können auf verschiedene Weisen eingestellt werden. Für eine programmgesteuerte Einstellung können Sie die Render-Methode verwenden. Wenn Sie über die URL eines Berichts auf den Bericht zugreifen, können Sie Geräteinformationen als URL-Parameter festlegen. Sie können die Geräteinformationseinstellungen auch in der Konfigurationsdatei von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] bearbeiten, um Renderingparameter global festzulegen. Weitere Informationen zum globalen Angeben von Renderingparametern finden Sie unter [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../../customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
## <a name="passing-device-information-using-the-render-method"></a>Übergeben von Geräteinformationen mit der Render-Methode  
 Um Einstellungen von Geräteinformationen an eine Renderingerweiterung übergeben, verwenden die <xref:ReportExecution2005.ReportExecutionService.Render%2A> Methode. Beispiel: Die folgende XML-Zeichenfolge kann an die <xref:ReportExecution2005.ReportExecutionService.Render%2A>-Methode übergeben werden, um beim Rendern in HTML ein HTML-Fragment zu erstellen.  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 Wenn ein Bericht als HTML-Fragment gerendert wird, befindet sich der Inhalt des Berichts in einem TABLE-Element, ohne ein HTML- oder ein BODY-Element zu verwenden. Verwenden Sie das HTML-Fragment, um den Bericht in ein bestehendes HTML-Dokument einzubinden. Weitere Informationen zu Geräteinformationseinstellungen für die HTML-Ausgabe finden Sie unter [HTML-Geräteinformationseinstellungen](../../html-device-information-settings.md).  
  
## <a name="passing-device-information-using-url-access"></a>Übergeben von Geräteinformationen mit URL-Zugriff  
 Die Geräteinformationen können auch mithilfe eines URL-Zugriffs übergeben werden. Dabei werden Geräteinformationseinstellungen als URL-Parameter übergeben. Die folgende URL-Zugriffszeichenfolge kann an den Berichtsserver übergeben werden, um einen gerenderten Bericht ohne die Symbolleiste des HTML-Viewers zu generieren.  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 Weitere Informationen finden Sie unter [Angeben von Geräteinformationseinstellungen in einer URL](../../specify-device-information-settings-in-a-url.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Geräteinformationseinstellungen für Renderingerweiterungen (Reporting Services)](../../device-information-settings-for-rendering-extensions-reporting-services.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../../customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Building Applications Using the Web Service and the .NET Framework (Erstellen von Anwendungen mit dem Webdienst und .NET Framework)](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
