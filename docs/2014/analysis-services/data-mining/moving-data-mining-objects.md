---
title: Verschieben von Datamining-Objekten | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], models
- data mining editor [Analysis Services]
- mining models [Analysis Services], managing
- Data Mining Designer
- mining models [Analysis Services], modifying
ms.assetid: bc108407-2603-4387-b930-b5bb9df78069
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dff20b2b3e273ec0aac653346084f6c2854a8330
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046301"
---
# <a name="moving-data-mining-objects"></a>Verschieben von Data Mining-Objekten
  Die häufigsten Szenarien beim Verschieben von Data Mining-Objekten sind das Bereitstellen eines Modells aus einer Test- oder Analyseumgebung in einer Produktionsumgebung oder die Freigabe von Modellen an andere Benutzer.  
  
 In diesem Thema wird beschrieben, wie Sie die Tools und Skripterstellungssprachen aus [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zum Verschieben von Data Mining-Objekten verwenden können.  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a>Verschieben von Data Mining-Objekten zwischen Datenbanken oder Servern  
 Sie können Data Mining-Objekte zwischen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbanken oder Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf folgende Weise verschieben:  
  
-   Erneutes Bereitstellen der Lösung an eine andere Datenbank.  
  
-   Skripterstellung einzelne Objekte.  
  
-   Sichern und anschließendes Wiederherstellen einer Kopie der Datenbank.  
  
-   Exportieren und Importieren von Strukturen und Modellen.  
  
 Im folgenden Abschnitt werden diese Optionen ausführlich erläutert.  
  
### <a name="deploying"></a>Bereitstellen  
 Für die Bereitstellung der Projektmappe auf einem anderen Server bzw. einer anderen Datenbank benötigen Sie die Projektmappendatei, die mit [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt wurde.  
  
 Weitere Informationen zur Bereitstellung von Analysis Services-Projektmappen finden Sie unter [Bereitstellen von Analysis Services-Projekten &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md).  
  
### <a name="scripting"></a>Skripterstellung  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stellt mehrere Sprachen bereit, mit denen Sie Skripte für Objekte erstellen können.  
  
-   **XMLA:** Sie können Objekte mit XMLA schreiben, indem Sie mit der rechten Maustaste auf Objekte in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]klicken. Um das Skript auszuführen, öffnen Sie es in einem **XMLA-Abfrage** -Fenster auf dem Zielserver.  
  
-   **DMX**: Sie können Skripte anhand von Vorlagen oder einem der Abfrage-Generatoren erstellen, die in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bereitgestellt werden.  
  
 Beachten Sie jedoch, dass es Unterschiede in den Aufgaben gibt, die Sie mit den einzelnen Skripterstellungssprachen ausführen können:  
  
-   Eigenschaften wie Objektbeschreibung und Datenbindungen können nur mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL-Sprachen erstellt oder geändert werden, nicht mit DMX.  
  
-   Nur DMX unterstützt den Import und den Export von Miningobjekten.  
  
-   Nur DMX unterstützt das Generieren von PMML oder Importieren von Modelldefinitionen aus PMML.  
  
-   Nur DMX unterstützt das Trainieren eines Modells mit Anwendungsdaten. Darüber hinaus unterstützt die DMX-Anweisung INSERT INTO das Trainieren eines Modells ohne Bereitstellung von Werten für eine Schlüsselspalte.  
  
 Weitere Informationen finden Sie unter [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
### <a name="backup-and-restore"></a>Sichern und Wiederherstellen  
 Sichern und Wiederherstellen einer gesamten Analysis Services-Datenbank bietet sich an, wenn Ihre Data Mining-Projektmappe auf OLAP-Objekten aufbaut. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] stellt die Sicherungs- und Wiederherstellungsfunktionalität bereit, mit der Datenbanksicherungen schneller und leichter erstellt werden können.  
  
 Weitere Informationen zur Sicherung finden Sie unter [Sichern und Wiederherstellen von Analysis Services-Datenbanken](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).  
  
### <a name="exporting-and-importing"></a>Exportieren und Importieren  
 Das Exportieren und anschließende erneute Importieren von Miningmodellen und -Strukturen mit DMX-Anweisungen ist die einfachste Möglichkeit, einzelne relationale Data Mining-Objekte zu verschieben oder zu sichern. Weitere Informationen zur DMX-Syntax für diese Vorgänge finden Sie unter den folgenden Themen:  
  
-   [EXPORTIEREN SIE &AMP;#40;DMX&AMP;#41;](/sql/dmx/export-dmx)  
  
-   [IMPORT &AMP;#40;DMX&AMP;#41;](/sql/dmx/import-dmx)  
  
 Wenn Sie die INCLUDE DEPENDENCIES-Option festlegen, exportiert [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auch die Definition erforderlicher Datenquellensichten. Beim Importieren des Modells oder der Struktur wird die Datenquellensicht auf dem Zielserver erneut erstellt. Stellen Sie nach dem Importieren des Modells sicher, dass die notwendigen Miningberechtigungen für das Objekt festgelegt werden.  
  
> [!NOTE]  
>  Sie können OLAP-Modelle nicht mit DMX exportieren und importieren. Wenn das Miningmodell auf einem OLAP-Cube basiert, müssen Sie die Funktionalität verwenden, die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zum Sichern und Wiederherstellen einer ganzen Datenbank bereitgestellt wird, oder den Cube und seine Modelle erneut bereitstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung von Data Mining-Lösungen und -Objekten](management-of-data-mining-solutions-and-objects.md)  
  
  
