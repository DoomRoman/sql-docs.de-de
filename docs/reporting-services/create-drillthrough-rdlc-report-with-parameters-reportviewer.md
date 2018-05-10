---
title: Erstellen eines Drillthroughberichts (RDLC) mit Parametern mithilfe von ReportViewer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f90ac792fe849ca91735e5a9b22a399d7798cf23
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="create-drillthrough-rdlc-report-with-parameters---reportviewer"></a>Erstellen eines Drillthroughberichts (RDLC) mit Parametern mithilfe von ReportViewer
Ein [Drillthroughbericht](http://technet.microsoft.com/library/ff519554.aspx) ist ein Bericht, der geöffnet werden kann, indem der Benutzer auf einen Link in einem anderen Bericht klickt. Drillthroughberichte enthalten in der Regel Details zu einem Element im ursprünglichen Zusammenfassungsbericht. Dieses Tutorial führt Sie in den folgenden Lektionen durch die Schritte zum Erstellen eines Drillthroughberichts mit Parametern und einer Abfrage. Dabei wird die [Berichterstellung im lokalen Modus](http://msdn.microsoft.com/library/ff487969.aspx)verwendet.  
  
## <a name="requirements"></a>Anforderungen  
Zur Verwendung dieser exemplarischen Vorgehensweise benötigen Sie Zugriff auf die Beispieldatenbank **AdventureWorks2014** . Weitere Informationen zum Abrufen der **AdventureWorks2014**-Beispieldatenbank finden Sie in den [AdventureWorks-Beispieldatenbanken](https://github.com/Microsoft/sql-server-samples/releases).  
  
Bei dieser exemplarischen Vorgehensweise wird vorausgesetzt, dass Sie mit Transaction-SQL-Abfragen und den ADO.NET-Objekten [DataSet](https://msdn.microsoft.com/library/system.data.dataset.aspx) und [DataTable](http://msdn.microsoft.com/library/system.data.datatable.aspx) vertraut sind.  
  
Verwenden Sie Visual Studio 2015 und die ASP.NET-Webanwendung, um eine ASP.NET-Webseite mit einem ReportViewer-Steuerelement zu erstellen. Das Steuerelement wird für die Anzeige eines erstellten Berichts konfiguriert. Mithilfe dieser exemplarischen Vorgehensweise erstellen Sie die Anwendung in Microsoft Visual C#.  
  
## <a name="tasks"></a>Aufgaben  
[Lektion 1: Erstellen einer neuen Website](../reporting-services/lesson-1-create-a-new-web-site.md)  
[Lesson 2: Define a Data Connection and Data Table for Parent Report (Lektion 2: Definieren einer Datenverbindung und einer Datentabelle für den übergeordneten Bericht)](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)  
[Lesson 3: Design the Parent Report using the Report Wizard (Lektion 3: Entwerfen des übergeordneten Berichts mithilfe des Berichts-Assistenten)](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)  
[Lesson 4: Define a Data Connection and Data Table for Child Report (Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht)](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)  
[Lesson 5: Design the Child Report using the Report Wizard (Lektion 5: Entwerfen des untergeordneten Berichts mithilfe des Berichts-Assistenten)](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)  
[Lesson 6: Add a ReportViewer Control to the Application (Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung)](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)  
[Lesson 7: Add Drillthrough Action on Parent Report (Lektion 7: Hinzufügen einer Drillthroughaktion für den übergeordneten Bericht)](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)  
[Lesson 8: Create a Data Filter (Lektion 8: Erstellen eines Datenfilters)](../reporting-services/lesson-8-create-a-data-filter.md)  
[Lesson 9: Build and Run the Application](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Reporting Services-Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)  
[Entwerfen von Berichten mithilfe des Berichts-Designers &#40;SSRS&#41;](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  

