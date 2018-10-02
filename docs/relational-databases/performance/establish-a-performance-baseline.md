---
title: Festlegen einer Leistungsbasislinie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1aa423e541eab4f863ab35a67cc352be09b8fc30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595498"
---
# <a name="establish-a-performance-baseline"></a>Festlegen einer Leistungsbasislinie
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn Sie ermitteln möchten, ob das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System einwandfrei arbeitet, sollten Sie die Leistung in regelmäßigen Abständen messen, selbst wenn keine Probleme auftreten, um eine Basislinie für die Serverleistung zu erstellen. Vergleichen Sie jede neue Messreihe mit den zuvor erfassten Messungen.  
  
 Die folgenden Bereiche wirken sich auf die Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aus:  
  
-   Systemressourcen (Hardware)  
  
-   Netzwerkarchitektur  
  
-   Das Betriebssystem  
  
-   Datenbankanwendungen  
  
-   Clientanwendungen  
  
 Es sollten mindestens die folgenden Basislinienmessungen vorgenommen werden:  
  
-   Leistung bei Spitzen- und Normalbetrieb.  
  
-   Antwortzeiten für Produktionsabfragen oder Batchbefehle.  
  
-   Zeiten für das Sichern und Wiederherstellen von Datenbanken.  
  
 Nach dem Erstellen einer Basislinie für die Serverleistung sollten Sie die Basislinienstatistik mit der aktuellen Serverleistung vergleichen. Zahlen, die deutlich über oder unter der Basislinie liegen, sollten näher untersucht werden. Sie können ein Hinweis auf Bereiche, die optimiert oder neu konfiguriert werden müssen, sein. Wenn beispielsweise die Zeitdauer zum Ausführen einer Reihe von Abfragen steigt, sollten Sie die Abfragen untersuchen, um festzustellen, ob sie neu geschrieben werden können oder ob Spaltenstatistiken oder neue Indizes hinzugefügt werden müssen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
