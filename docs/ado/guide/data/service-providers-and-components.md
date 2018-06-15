---
title: Service-Anbieter und -Komponenten | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc5f0b18568e7056d4456ed8209fc931f7233fcd
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272559"
---
# <a name="service-providers-and-components"></a>Dienstanbieter und Komponenten
Dienstanbieter sind Komponenten, die die Funktionalität von Datenanbietern erweitern, indem implementieren die erweiterten Schnittstellen, die vom Datenspeicher nicht systemeigen unterstützt werden.  
  
 Universal Data Access enthält ein *Komponentenarchitektur* einzelne, spezielle Komponenten zum Implementieren der separate Sätze von Datenbankfunktionen oder "Dienste", über weniger leistungsfähige speichert ermöglicht. Daher geben Sie Dienstkomponenten anstatt das Erzwingen eines jeden Datenspeicher, um eine eigene Implementierung der erweiterten Funktionen bereitzustellen, oder durch das Erzwingen des allgemeiner Anwendungen, die intern zu implementieren, eine verbreitete Implementierung, die jede Anwendung kann Verwenden Sie, wenn Sie einen beliebigen Datenspeicher zugreifen. Die Tatsache, dass einige Funktionen systemintern durch den Datenspeicher und durch allgemeine Komponenten implementiert wird, ist für die Anwendung transparent.  
  
 Angenommen, ein Cursor Modul, wie z. B. [des Cursordiensts für OLE DB-](http://msdn.microsoft.com/en-us/57638feb-4ecd-4051-becb-8f828d21cf44), ist eine Dienstkomponente, die Daten aus einem sequenziellen, Vorwärtscursor Datenspeicher bildlauffähige Daten erstellt nutzen kann. Andere häufig verwendete ADO Dienstanbieter umfassen die [Microsoft OLE DB-Anbieter für Persistenz (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (zum Speichern von Daten in eine Datei), die [Microsoft-Datenstrukturierungsdiensts für OLE DB (ADO-Dienstanbieter) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (für hierarchische **Recordsets**), und die [Microsoft OLE DB-Anbieter für Remoting (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (zum Aufrufen von Datenanbieter auf einem Remotecomputer befindet).  
  
 Weitere Informationen zum Dienst und Datenanbieter finden Sie unter [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md).
