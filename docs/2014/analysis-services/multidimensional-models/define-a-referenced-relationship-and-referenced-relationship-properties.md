---
title: Definieren eine referenzierte Beziehung und auf die Beziehungseigenschaften verwiesen wird. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- referenced dimension relationship
- relationships [Analysis Services], referenced dimensions
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 131479d064f911f7574de3a7dc113d0ed313601c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191252"
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a>Definieren einer Beziehung, auf die verwiesen wird, und deren Eigenschaften
  Eine Bezugsdimensionsbeziehung wird im Cube-Designer auf der Registerkarte **Dimensionsverwendung** definiert. Die Bezugsdimensionsbeziehung wird definiert, indem Folgendes angegeben wird:  
  
-   Die Zwischendimension, mit der ein Join hergestellt werden soll. Hierbei kann es sich um eine reguläre Dimension oder eine andere Bezugsdimension handeln.  
  
-   Ein Bezugsdimensionsattribut, das die niedrigste verfügbare Stufe für die Aggregation der Dimension im Hinblick auf die Measuregruppe definiert.  
  
-   Das (Fremdschlüssel-)Attribut in der Zwischendimension, das dem Bezugsdimensionsattribut entspricht.  
  
 Beachten Sie, dass die Spalte, die die Bezugsdimension mit der Faktentabelle verknüpft und bei der es sich im Allgemeinen um das Schlüsselattribut in der Bezugsdimension handelt, auch als ein Attribut in der Zwischendimension definiert sein muss. Wenn Sie eine Kette von Bezugsdimensionen erstellen, beginnen Sie mit dem Erstellen der regulären Beziehung zwischen der ersten Dimension in der Kette und der Measuregruppe. Erstellen Sie anschließend jede weitere referenzierte Beziehung in der entsprechenden Reihenfolge. Eine referenzierte Beziehung kann nur zu einer Dimension mit einer vorhandenen Beziehung zu der Measuregruppe erstellt werden.  
  
 Wenn Sie eine Bezugsdimensionsbeziehung erstellen, wird der Dimensionsattributlink standardmäßig materialisiert. Durch das Materialisieren eines Dimensionsattributlinks wird bewirkt, dass der Wert des Links zwischen der Faktentabelle und der Bezugsdimension für jede Zeile während der Verarbeitung in der MOLAP-Struktur für die Dimension materialisiert, d. h. gespeichert, wird. Dies hat eine geringe Auswirkung auf die Verarbeitungsleistung und die Speicheranforderungen, verbessert jedoch die Abfrageleistung.  
  
 In einer Bezugsdimension wird die Granularität durch Identifizieren des Attributs angegeben, das die Beziehung zwischen einer Bezugsdimension und der Measuregruppe, die der Haupttabelle der Dimension entspricht, definiert. Wenn mehrere Bezugsdimensionen miteinander verkettet werden, definieren die Verweise die Beziehung von der äußersten Dimension bis zur Measuregruppe.  
  
  
