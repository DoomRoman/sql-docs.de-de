---
title: Neue Systemrolle (Management Studio) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: tools
ms.suite: pro-bi
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d8b7c6d284f238c1b6f9724eca2c8d9ec3dd2c9f
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43275357"
---
# <a name="new-system-role-management-studio"></a>Neue Systemrolle (Management Studio)
  Verwenden Sie diese Seite, um eine Rollendefinition auf Systemebene zu erstellen. Eine Systemrollendefinition gibt eine Gruppe von Aufgaben auf Systemebene an, die für den gesamten Berichtsserver gültig sind.  
  
> [!NOTE]  
>  Rollendefinitionen werden nur auf einem Berichtsserver verwendet, der im einheitlichen Modus ausgeführt wird. Ist der Berichtsserver für den integrierten SharePoint-Modus konfiguriert, ist diese Seite nicht verfügbar.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen der Rollendefinition ein. Ein Rollendefinitionsname muss innerhalb des Berichtsserver-Namespaces eindeutig sein. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten. Folgende Zeichen können beim Angeben eines Namens nicht verwendet werden:  
  
 ; ? : \@ & = + , $ / * < >  
  
 " /  
  
 **Beschreibung**  
 Stellen Sie eine Beschreibung bereit, in der die Verwendung der Rolle erläutert wird, und die Art der Unterstützung durch die Rolle aufgeführt ist.  
  
 **Task**  
 Wählen Sie die Tasks auf Systemebene aus, die über diese Rolle ausgeführt werden können. Sie können keine neuen, von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]unterstützten Tasks erstellen oder solche vorhandenen Tasks ändern. Außerdem können Sie keine Tasks auf Elementebene für eine Systemrollendefinition auswählen.  
  
 **Taskbeschreibung**  
 Zeigt eine Beschreibung des Tasks an, in der die durch den Task unterstützten Vorgänge bzw. Berechtigungen aufgeführt sind.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Berichtsserver im Management Studio (F1-Hilfe)](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Rollendefinitionen](../../reporting-services/security/role-definitions.md)  
  
  
