---
title: Entfernen einer Übermittlungserweiterung | Microsoft-Dokumentation
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 24036ae33b6b6a8da46b988189a055f5b17cca46
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43274942"
---
# <a name="removing-a-delivery-extension"></a>Entfernen einer Übermittlungserweiterung
  Sie entfernen eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung, indem Sie einfach das **Erweiterungselement** für die Übermittlungserweiterung aus der Konfigurationsdatei entfernen. Nachdem Sie die Konfigurationsinformationen entfernt haben, steht die Übermittlungserweiterung nicht mehr auf dem Berichtsserver zur Verfügung.  
  
 Wenn das entsprechende **Erweiterungselement** für die Übermittlungserweiterung aus der Konfigurationsdatei entfernt wurde, ist die Übermittlungserweiterung nicht mehr auf dem Berichtsserver registriert. Der Berichtsserver entfernt den Eintrag aus der Liste der Übermittlungserweiterungen und deaktiviert alle Abonnements, die diese Übermittlungserweiterung verwenden. Nachdem Sie eine Übermittlungserweiterung entfernt haben, können Benutzer sie nicht mehr als Benachrichtigungsmethode auswählen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Implementieren von Übermittlungserweiterungen](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
