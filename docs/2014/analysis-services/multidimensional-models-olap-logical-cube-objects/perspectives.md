---
title: Perspektiven | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0e77942ff650cc428e957bacc92921cb2b669a04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159657"
---
# <a name="perspectives"></a>Perspektiven
  Eine Perspektive ist eine Definition, die es Benutzern ermöglicht, einen Cube auf einfachere Weise anzuzeigen. Eine Perspektive ist eine Teilmenge der Funktion eines Cubes. Mithilfe von Perspektiven können Administratoren Sichten eines Cubes erstellen, die Benutzer dabei unterstützen, die für sie wichtigsten Daten hervorzuheben. Eine Perspektive enthält Teilmengen aller Objekte eines Cubes. Eine Perspektive kann keine Elemente einschließen, die nicht im übergeordneten Cube definiert sind.  
  
 Eine einfache <xref:Microsoft.AnalysisServices.Perspective> Objekt besteht aus: grundlegenden Informationen, Dimensionen, Measuregruppen, Berechnungen, KPIs und Aktionen. Grundlegende Informationen beinhalten den Namen und das Standardmeasure der Perspektive. Die Dimensionen sind eine Teilmenge der Cubedimensionen. Measuregruppen sind eine Teilmenge der Measuregruppen des Cubes. Die Berechnungen sind eine Teilmenge der Cubeberechnungen. Die KPIs sind eine Teilmenge der KPIs des Cubes. Die Aktionen sind eine Teilmenge der Cubeaktionen.  
  
 Ein Cube muss aktualisiert und verarbeitet werden, bevor die Perspektive verwendet werden kann.  
  
 Cubes kann sehr komplexe Objekte für Benutzer zum Durchsuchen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ein einzelner Cube kann den Inhalt eines gesamten Data Warehouse darstellen, wobei mehrere Measuregruppen in einem Cube mehrere Faktentabellen und mehrere Dimensionen basierend auf mehreren Dimensionstabellen darstellen. Ein solcher Cube kann sehr komplex und leistungsstark, aber entmutigend für Benutzer sein, die oft nur mit einem kleinen Teil eines Cubes interagieren müssen, um ihre Business Intelligence- und Berichterstellungsanforderungen zu erfüllen.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], können Sie eine Perspektive verringern Sie die wahrgenommene Komplexität eines Cubes in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Eine Perspektive definiert eine sichtbare Teilmenge eines Cubes, die fokussierte, unternehmensspezifische oder anwendungsspezifische Sichten für einen Cube bereitstellt. Über die Perspektive wird die Sichtbarkeit der in einem Cube enthaltenen Objekte gesteuert. Die folgenden Objekte können in einer Perspektive angezeigt oder ausgeblendet werden:  
  
-   Dimensionen  
  
-   Attribute  
  
-   Hierarchien  
  
-   Measuregruppen  
  
-   Measures  
  
-   Key Performance Indicators (KPIs)  
  
-   Berechnungen (berechnete Elemente, benannte Mengen und Skriptbefehle)  
  
-   Aktionen  
  
 Z. B. die **Adventure Works** Cubes in der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Beispiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank enthält elf Measuregruppen und einundzwanzig verschiedene Cubedimensionen darstellt, Verkäufe, Verkaufsprognosen und Finanzdaten. Eine Clientanwendung kann direkt auf den gesamten Cube verweisen. Diese Sicht kann allerdings für einen Benutzer zu umfangreich sein, der versucht, allgemeine Informationen zur Umsatzprognose zu extrahieren. Stattdessen kann dieser Benutzer die Perspektive **Verkaufsziele** verwenden, um die Sicht des **Adventure Works** -Cubes auf die Objekte zu beschränken, die für Umsatzprognosen relevant sind.  
  
 Für Objekte in einem Cube, die für den Benutzer durch eine Perspektive nicht sichtbar sind, ist ein direktes Verweisen und Abrufen trotzdem mithilfe von XMLA- (XML for Analysis), MDX- (Multidimensional Expressions) oder DMX-Anweisungen (Data Mining Extensions) möglich. Perspektiven begrenzen nicht den Zugriff auf Objekte in einem Cube und sollten hierfür auch nicht verwendet werden. Stattdessen können Perspektiven verwendet werden, um Endbenutzern den Zugriff auf einen Cube zu erleichtern.  
  
 Bei einer Perspektive handelt es sich um eine schreibgeschützte Sicht des Cubes. Objekte im Cube können mithilfe einer Perspektive nicht umbenannt oder geändert werden. Außerdem können das Verhalten oder die Funktionen eines Cubes, wie die Verwendung sichtbarer Gesamtwerte, nicht mithilfe einer Perspektive geändert werden.  
  
## <a name="security"></a>Security  
 Perspektiven sollen nicht als Sicherheitsmechanismus verwendet werden, sondern werden als Tool zur Vereinfachung der Nutzung von Business Intelligence-Anwendungen für Endbenutzer verwendet. Die gesamte Sicherheit einer bestimmten Perspektive wird vom zugrunde liegenden Cube geerbt. So können z. B. Perspektiven keinen Zugriff auf Objekte in einem Cube ermöglichen, auf die ein Benutzer nicht bereits Zugriff hat. - Die Sicherheit des Cubes muss geklärt werden, damit der Zugriff auf Objekte im Cube durch eine Perspektive ermöglicht werden kann.  
  
  