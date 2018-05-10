---
title: Meine Einstellungen für Power BI-Integration (Webportal) | Microsoft-Dokumentation
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- pbi
- power bi
- power bi integration
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7d878ea994865096aac36397e9c32c8cf55b359c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="my-settings-for-power-bi-integration-web-portal"></a>Meine Einstellungen für die Power BI-Integration (Webportal)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Die Seite **Meine Einstellungen** im [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] wird von einzelnen Benutzern verwendet, um ihre Anmeldung bei [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]zu verwalten. Wenn Sie die Schritte zum Anheften eines Berichtselements ausführen, werden Sie automatisch aufgefordert, sich anzumelden.  Sie können sich jedoch auf der Seite **Meine Einstellungen** manuell an- und abmelden.  Wenn die Menüoption **Meine Einstellungen** nicht angezeigt wird, ist der Berichtsserver nicht in [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] integriert.  Weitere Informationen finden Sie unter [Berichtsserverintegration für Power BI &#40;Configuration Manager&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)integrieren.  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## <a name="why-sign-in"></a>Warum anmelden

 Wenn Sie sich anmelden, erstellen Sie eine Beziehung zwischen Ihrem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Benutzerkonto und Ihrem [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] -Konto.  Die Anmeldung erstellt ein Sicherheitstoken, das 90 Tage gültig ist. Wenn das Token abläuft und Sie Elemente an Power BI angeheftet haben, erhalten Sie eine Benachrichtigung.  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
Kacheln innerhalb von [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] -Dashboards werden erst aktualisiert, nachdem Sie sich über **MySettings**angemeldet haben.  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
Nachdem Sie sich angemeldet haben, wird ein neues Sicherheitstoken erstellt.  Ihre Dashboardkacheln werden entsprechend den zuvor konfigurierten Zeitplänen aktualisiert.  

## <a name="next-steps"></a>Nächste Schritte

[Integration von Power BI-Berichtsserver](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
[Anheften von Reporting Services-Elementen an Power BI-Dashboards](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
[Dashboards in Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
[Web portal (Webportal)](../reporting-services/web-portal-ssrs-native-mode.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](http://go.microsoft.com/fwlink/?LinkId=620231)
