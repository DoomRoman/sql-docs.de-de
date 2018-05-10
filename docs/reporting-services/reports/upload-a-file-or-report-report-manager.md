---
title: Hochladen einer Datei oder eines Berichts (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d5485f3c29c394655371ff42b690ccbacdcdd53d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="upload-a-file-or-report-report-manager"></a>Hochladen einer Datei oder eines Berichts (Berichts-Manager)
  Der Berichts-Manager umfasst eine Uploadfunktion, sodass Sie Berichte, Modelle und andere Dateien zu einem Berichtsserver hinzufügen können, ohne diese Elemente von einer Clientanwendung zu veröffentlichen. Dateien, die Sie über das Dateisystem hochladen, werden als Elemente auf dem Berichtsserver gespeichert. Die Speicherung erfolgt je nach Dateityp:  
  
-   RDL-Dateien werden als Berichte gespeichert.  
  
-   SMDL-Dateien werden als Berichtsmodelle gespeichert.  
  
-   Alle anderen Dateien, einschließlich freigegebener Datenquellendateien (RDS), werden als Ressourcen hochgeladen. Ressourcen werden nicht von einem Berichtsserver verarbeitet, können aber im Berichts-Manager angezeigt werden, wenn der Berichtsserver den MIME-Typ der Datei unterstützt.  
  
### <a name="to-upload-a-file-or-report"></a>So laden Sie eine Datei oder einen Bericht hoch  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** . Navigieren Sie zum Ordner, zu dem Sie ein Element hinzufügen möchten.  
  
3.  Klicken Sie auf **Datei hochladen**.  
  
4.  Klicken Sie auf **Durchsuchen** , um eine Datei zum Hochladen auszuwählen. Sie können eine Berichtsdefinitionsdatei, ein Bild, ein Dokument oder jede andere Datei hochladen, die Sie auf einem Berichtsserver zur Verfügung stellen möchten.  
  
5.  Geben Sie einen Namen für das neue Element ein. Ein Element darf Leerzeichen enthalten, jedoch nicht die folgenden reservierten Zeichen: ; ? : @ & = + , $ / * < > |.  
  
6.  Wenn Sie ein vorhandenes Element durch ein neues ersetzen möchten, wählen Sie **Vorhandenes Element überschreiben**aus.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Inhalt &#40;Seite, Berichts-Manager&#41;](http://msdn.microsoft.com/library/6b16869b-158a-4934-9c85-bee934b35378)   
 [Datei hochladen (Seite, Berichts-Manager)](http://msdn.microsoft.com/library/7bb3166f-9374-4449-b66a-ffb77298507d)   
 [Hochladen von Dateien in einen Ordner](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  
