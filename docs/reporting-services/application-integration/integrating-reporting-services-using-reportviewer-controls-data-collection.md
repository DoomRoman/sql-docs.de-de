---
title: Datensammlung im ReportViewer-Steuerelement 2016 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: application-integration
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
caps.latest.revision: 2
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5d41ac350e03dfbecc53041b2bbfa2570ede717c
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926851"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Integrieren von Reporting Services mit den ReportViewer-Steuerelementen: Datensammlung
Standardmäßig erfasst das ReportViewer-Steuerelement anonyme Nutzungsinformationen, damit Microsoft besser nachvollziehen kann, wie die Steuerelemente von den Kunden verwendet werden. Durch ein besseres Verständnis darüber, wie die Kunden Bereitstellungen durchführen und das Viewer-Steuerelement verwenden, können zukünftige Entwicklungen so verbessert werden, dass für den Kunden der größtmögliche Nutzen erzielt wird.

Eine Erklärung der Datensammlungs- und Datennutzungsverfahren der Microsoft SQL Server 2016-Releases sowie anderer Produkte und Dienste finden Sie in diesen [Datenschutzbestimmungen]((http://go.microsoft.com/fwlink/?LinkID=868444)).

## <a name="opting-out-of-telemetry"></a>Deaktivieren der Telemetrie

Die Telemetrie kann programmgesteuert über „EnableTelemetry“ deaktiviert werden. Dies kann durch Bearbeiten der ASPX-Seite erfolgen, die das Steuerelement hostet,

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

oder bevor das Steuerelement gerendert wird, z.B. durch einen Aufruf der Page_Load-Methode der Hostingseite.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Siehe auch

[Verwenden des ReportViewer-Steuerelements in WebForms](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Integrieren von Reporting Services mithilfe der ReportViewer-Steuerelemente](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



