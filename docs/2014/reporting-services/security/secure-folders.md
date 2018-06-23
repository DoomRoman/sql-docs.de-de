---
title: Sichere Ordner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high-security folders [Reporting Services]
- low-security folders
- folders [Reporting Services], security
- security [Reporting Services], folders
ms.assetid: 0fd91f77-0143-476b-9af0-87293be78e44
caps.latest.revision: 33
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: fb5806011f24d6853962b54b172d874829cb65f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059760"
---
# <a name="secure-folders"></a>Sichere Ordner
  Die Ordnersicherheit ist die Grundlage für das Sichern des gesamten Inhalts auf einem Berichtsserver. Da die Sicherheit in der Ordnerstruktur weitervererbt wird, können Sie für große oder kleine Abschnitte der Ordnerhierarchie eine bestimmte Zugriffsart zulassen.  
  
 Ordner mit einer hohen Sicherheit können zum Speichern vertraulicher Berichte oder als Stagingbereiche verwendet werden. Beispielsweise können Sie mit einem Ordner Berichte testen, bevor Sie sie an den endgültigen Speicherort verschieben. Um den Zugriff auf diesen Bereich zu steuern, können Sie eine Rollenzuweisung definieren, die nur Berichterstellern das Hinzufügen und Löschen von Elementen ermöglicht, und eine zweite Rollenzuweisung, die Testern das Ausführen von Berichten, aber nicht das Hinzufügen oder Entfernen von Elementen ermöglicht. Die Rollenzuweisungen werden explizit für Tester und Berichtsautoren definiert, weshalb keine anderen Benutzer (außer lokalen Systemadministratoren) über Zugriff auf den Ordner verfügen.  
  
 Ordner mit niedriger Sicherheit können zum Speichern von Berichten verwendet werden, auf die der Zugriff problemlos möglich sein soll.  
  
 Die Ordnersicherheit stellt die Basis der Sicherheit auf Elementebene dar, ausgehend vom Stammknoten der Ordnerhierarchie des Berichtsservers. Dabei handelt es sich um den Ordner Stamm. Da die Sicherheit vererbt wird, sollte eine relativ restriktive Sicherheitsrichtlinie für den Ordner Stamm festgelegt werden. Das Verwenden der **Browser** -Rolle in den Rollenzuweisungen im Basisordner erfüllt genau diesen Zweck, indem sie einen schreibgeschützten Zugriff bereitstellt.  
  
## <a name="tasks-and-folder-access"></a>Aufgaben und Ordnerzugriff  
 Beachten Sie beim Erstellen von Rollenzuweisungen für Ordner die in der folgenden Tabelle aufgeführten Aufgaben.  
  
|Verwendete Aufgabe|Erteilte Berechtigungen|  
|----------------------|---------------------------|  
|Ordner anzeigen|Anzeigen der Ordnerhierarchie und der schreibgeschützten Eigenschaften, die anzeigen, wann der Ordner erstellt und geändert wurde.<br /><br /> Benutzer können Elemente im Ordner nur anzeigen, wenn ihnen Rollen zugewiesen wurden, die auch die folgenden Aufgaben einschließen: "Berichte anzeigen", "Modelle anzeigen", "Ressourcen anzeigen" und "Datenquellen anzeigen".|  
|Ordner verwalten|Anzeigen von Ordnereigenschaften, Ändern des Namens oder der Beschreibung oder Verschieben des Ordners an einen anderen Speicherort. Diese Aufgabe ermöglicht Benutzern das Erstellen von Ordnern.|  
|Berichte verwalten|Hinzufügen von Berichten vom Dateisystem zu einem Ordner und Veröffentlichen von Berichten vom Berichts-Designer auf dem Berichtsserver.|  
|Datenquellen verwalten|Hinzufügen von neuen freigegebenen Datenquellenelementen zu einem Ordner und Ändern von vorhandenen freigegebenen Datenquellen.|  
|Die Sicherheit für einzelne Elemente festlegen|Erstellen und Ändern von Rollenzuweisungen, die den Zugriff auf den Ordner steuern. Diese Aufgabe muss zusammen mit Ordner anzeigen oder Ordner verwalten verwendet werden. Andernfalls hat sie keine Auswirkung, weil der Benutzer das Element nicht auswählen kann.|  
  
## <a name="see-also"></a>Siehe auch  
 [Sichere Berichte und Ressourcen](secure-reports-and-resources.md)   
 [Sichern freigegebener Datenquellenelemente](secure-shared-data-source-items.md)   
 [Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](granting-permissions-on-a-native-mode-report-server.md)  
  
  