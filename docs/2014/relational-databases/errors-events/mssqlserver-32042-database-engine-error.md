---
title: MSSQLSERVER_32042 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 32042 (Database Engine error)
ms.assetid: 53a51c7a-dcd4-4c15-b4d2-6aaa9dce76da
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b73bdc058ad71cd3b4c3144221f78f6446aa95da
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423439"
---
# <a name="mssqlserver32042"></a>MSSQLSERVER_32042
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|32042|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum32042|  
|Meldungstext|Die Warnung für 'Nicht gesendetes Protokoll' wurde ausgelöst. Der aktuelle Wert von '%d' überschreitet den Threshold '%d'.|  
  
## <a name="explanation"></a>Erklärung  
 Dieses Ereignis der Datenbankspiegelung wird für die Prinzipalserverinstanz ausgelöst, um anzugeben, dass der Umfang des nicht gesendeten Protokolls einen vom Benutzer angegebenen Schwellenwert erreicht hat. Normalerweise tritt dieses Ereignis auf, weil sich die Leistung des Systems geändert hat. Entweder hat sich die Bandbreite zwischen den beiden Systemen reduziert, oder die Last hat sich erhöht.  
  
 Der Umfang des nicht gesendeten Protokolls ist eine Leistungsmetrik, mit der Sie die Wahrscheinlichkeit eines Datenverlusts im Hinblick auf die Anzahl von Kilobyte (KB) des nicht gesendeten Protokolls ermitteln können. Diese Metrik ist insbesondere für Sitzungen im Modus für hohe Leistung relevant. Diese Metrik ist jedoch auch für Sitzungen im Modus für hohe Sicherheit relevant, wenn die Spiegelung angehalten oder ausgesetzt wird, weil die Partner getrennt werden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Prüfen Sie die Auslastung für die Instanzen des Prinzipalservers und des Spiegelservers sowie die entsprechenden Netzwerkverbindungen, um die Ursache zu ermitteln.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Verwenden von Warnungsschwellenwerten und Warnmeldungen für Spiegelungsleistungsmetriken &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
