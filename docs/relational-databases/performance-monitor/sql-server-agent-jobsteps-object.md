---
title: SQL Server-Agent, Auftragsschritte-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 21835671518515b1efe02698a0f01f4dcd051179
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32951815"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server-Agent, Auftragsschritte-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent: **Auftragsschritte** -Leistungsobjekt enthält Leistungsindikatoren, die Informationen zu den Auftragsschritten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents angeben. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
 Die folgende Tabelle enthält die Leistungsindikatoren von **SQLAgent:Auftragsschritte** .  
  
|Name|Description|  
|----------|-----------------|  
|**Aktive Schritte**|Dieser Indikator gibt die Anzahl der aktuell ausgeführten Auftragsschritte an.|  
|**Schritte in Warteschlange**|Dieser Indikator gibt die Anzahl der Auftragsschritte an, die für das Ausführen durch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent bereitstehen, deren Ausführung jedoch noch nicht gestartet wurde.|  
|**Wiederholungen von Schritten gesamt**|Dieser Indikator gibt an, wie oft [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seit dem letzten Serverneustart insgesamt versucht hat, einen Auftragsschritt neu zu starten.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Instanz|Description|  
|--------------|-----------------|  
|**_Total**|Informationen für alle Auftragsschritte.|  
|**ActiveScripting**|Informationen für Auftragsschritte, die das **ActiveScripting** -Subsystem verwenden.|  
|**ANALYSISCOMMAND**|Informationen für Auftragsschritte, die das ANALYSISCOMMAND-Subsystem verwenden.|  
|**ANALYSISQUERY**|Informationen für Auftragsschritte, die das ANALYSISQUERY-Subsystem verwenden.|  
|**CmdExec**|Informationen für Auftragsschritte, die das **CmdExec** -Subsystem verwenden.|  
|**Distribution**|Informationen für Auftragsschritte, die das **Distribution** -Subsystem verwenden.|  
|**Dts**|Informationen für Auftragsschritte, die das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Subsystem verwenden.|  
|**LogReader**|Informationen für Auftragsschritte, die das **LogReader** -Subsystem verwenden.|  
|**Merge**|Informationen für Auftragsschritte, die das **Merge** -Subsystem verwenden.|  
|**PowerShell**|Informationen für Auftragsschritte, die das **PowerShell** -Subsystem verwenden.|  
|**QueueReader**|Informationen für Auftragsschritte, die das **QueueReader** -Subsystem verwenden.|  
|**Momentaufnahme**|Informationen für Auftragsschritte, die das **Momentaufnahme** -Subsystem verwenden.|  
|**TSQL**|Informationen für Auftragsschritte, die [!INCLUDE[tsql](../../includes/tsql-md.md)]ausführen.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwalten von Auftragsschritten](http://msdn.microsoft.com/library/51352afc-a0a4-428b-8985-f9e58bb57c31)   
 [Verwenden von Leistungsobjekten](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
