---
title: SQL Server, Speicherbrokerclerks (Objekt) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
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
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
caps.latest.revision: 4
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: abc1812029cdf51d829b6e15a4049d05a7ae5383
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950435"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQLServer, Speicherbrokerclerks (Objekt)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Das Leistungsobjekt **SQLServer: Speicherbrokerclerks** enthält Leistungsindikatoren für Statistiken zu Speicherbrokerclerks.

In der folgenden Tabelle werden die SQL Server-Leistungsobjekte für **Speicherbrokerclerks** beschrieben.

|**SQL Server-Speicherbrokerclerks (Leistungsindikatoren)**|Description|  
|-------------|-----------------|  
|**Interner Nutzen**|Der interne Wert des Arbeitsspeichers für eine unzureichende Eintragsanzahl (in ms pro Seite pro ms) multipliziert mit 10 Milliarden und auf eine ganze Zahl gekürzt.|
|**Größe des Speicherbrokerclerks**|Die Clerkgröße in Seiten.|
|**Periodische Entfernungsvorgänge (Seiten)**|Die Anzahl der durch den letzten periodischen Entfernungsvorgang aus dem Brokerclerk entfernten Seiten.|
|**Überlastungsentfernungsvorgänge (Seiten/Sekunde)**|Die Anzahl der Seiten pro Sekunde, die aufgrund unzureichenden Arbeitsspeichers aus dem Brokerclerk entfernt wurden.|
|**Simulationsnutzen**|Der Wert des Arbeitsspeichers für den Clerk (in ms pro Seite pro ms) multipliziert mit 10 Milliarden und auf eine ganze Zahl gekürzt.|
|**Simulationsgröße**|Die aktuelle Größe der Clerksimulation in Seiten.|

Es gibt eine Instanz des Indikators für den Pufferpool und für den Objektpool des Spaltenspeichers.

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Überwachen der Ressourcenverwendung (Systemmonitor)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
