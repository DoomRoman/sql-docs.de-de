---
title: Erweiterungen für Reporting Services | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7fa7479ddfe9e5bbb124a4cff948bf67ddce4116
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737073"
---
# <a name="reporting-services-extensions"></a>Erweiterungen für Reporting Services
  Die modulare Architektur von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ermöglicht Erweiterungen. Eine verwaltete Code-API steht zur Verfügung, sodass Sie problemlos Erweiterungen entwickeln, installieren und verwalten können, die von vielen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Komponenten benötigt werden. Sie können private oder freigegebene Assemblys erstellen, indem Sie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] verwenden und neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Funktionen hinzufügen, um den wachsenden Geschäftsanforderungen Ihres Unternehmens gerecht zu werden.  
  
 Durch die besondere Architektur für Erweiterungen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] können spezielle Erweiterungsfunktionen des Produkts und seiner Komponenten entwickelt werden. Momentan wird die Erweiterung der Datenverarbeitungsmöglichkeiten von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in großem Umfang unterstützt. Die Datenverarbeitungs-API enthält bekannte [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Datenanbieter-Konstrukte und Konventionen, die den Entwicklern die Integration zusätzlicher Datenverarbeitungsmöglichkeiten in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bieten. Diese Datenverarbeitungserweiterungen fügen sowohl dem Berichtsserver als auch dem Berichts-Designer weitere Funktionen hinzu, sodass eine nahtlose Integration der benutzerdefinierten Daten in die bestehenden Berichte ermöglicht wird.  
  
 Eine weitere unterstützte Erweiterung ist die Übermittlungserweiterung. Die Übermittlungs-API ist komplett in die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Architektur integriert und ermöglicht eine Vielzahl von Übermittlungsmechanismen für den Versand von Berichtsbenachrichtigungen an die Benutzer. Sie können den Berichtsserver so erweitern, dass er eine benutzerdefinierte Übermittlung an Benutzer zulässt. Und Sie können die Abonnementverwaltungsseiten des Berichts-Managers so erweitern, dass Abonnements möglich sind, die benutzerdefinierte Übermittlungserweiterungen verwenden.  
  
 Über eine weitere Berichtsservererweiterung, die RDCE-Erweiterung (Report Definition Customization Extension), kann eine Berichtsdefinition dynamisch angepasst werden, bevor Sie an die Verarbeitungs-Engine geleitet wird. Sie können Berichte an verschiedene Faktoren, z. B. an andere Benutzer oder Sprachen, anpassen. Beispielsweise möchten Sie verschiedene Ansichten für verschiedene Benutzer (z. B. Manager oder Mitarbeiter einer Abteilung) implementieren. Oder Sie möchten einen Bericht so anpassen, dass er ein anderes Layout hat, wenn er auf Französisch oder Arabisch ausgegeben wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Security Considerations for Extensions (Überlegungen zur Sicherheit von Erweiterungen)](../../reporting-services/extensions/security-considerations-for-extensions.md)  
 Beschreibt Sicherheitsprobleme, die beim Entwickeln und Bereitstellen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Erweiterungen auftreten können.  
  
 [Implementing a Data Processing Extension (Implementieren von Datenverarbeitungserweiterungen)](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)  
 Beschreibt die Anforderungen und Schritte für die Implementierung von Datenverarbeitungserweiterungen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implementing a Delivery Extension (Implementieren von Übermittlungserweiterungen)](../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)  
 Beschreibt die Anforderungen und Schritte für die Implementierung von Übermittlungserweiterungen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implementing a Rendering Extension (Implementieren von Renderingerweiterungen)](../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)  
 Enthält eine Einführung zur Entwicklung von Renderingerweiterungen.  
  
 [Implementieren von Sicherheitserweiterungen](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)  
 Beschreibt die Anforderungen und Schritte für die Implementierung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Sicherheitserweiterungen.  
  
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../reporting-services/extensions/reporting-services-extension-library.md)  
 Enthält die Programmierreferenz für die Erweiterungs-API-Bibliothek für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Erweiterbarkeitsfunktionen.  
  
  
