---
title: Festlegen der maximalen Tabellengröße für eine Ablaufverfolgungstabelle (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25a852c52c0041d69bb73e5b7b8ec3ea48c89eb8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087050"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>Festlegen der maximalen Tabellengröße für eine Ablaufverfolgungstabelle (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]die maximale Tabellengröße für Ablaufverfolgungstabellen festlegen.  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>So legen Sie die maximale Tabellengröße für eine Ablaufverfolgungstabelle fest  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung zu einer Instanz von SQL Server her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Geben Sie im Feld **Ablaufverfolgungsname** einen Namen für die Ablaufverfolgung ein.  
  
3.  Geben Sie im Feld **Vorlagenname**eine Ablaufverfolgungsvorlage aus.  
  
4.  Aktivieren Sie das Kontrollkästchen **In Tabelle speichern**.  
  
5.  Stellen Sie eine Verbindung mit dem Server her, auf dem Sie die Ablaufverfolgung speichern möchten.  
  
     Das Dialogfeld **Zieltabelle** wird geöffnet.  
  
6.  Wählen Sie aus der Liste **Datenbank** eine Datenbank für die Ablaufverfolgung aus.  
  
7.  Geben Sie im Feld **Tabelle** einen Tabellennamen ein, oder wählen Sie ihn aus.  
  
8.  Aktivieren Sie das Kontrollkästchen **Maximale Zeilenanzahl festlegen** , und geben Sie die maximale Zeilenanzahl für die Ablaufverfolgungstabelle an.  
  
    > [!NOTE]  
    >  Überschreiten die Zeilen in der Tabelle die maximale Anzahl, die Sie angegeben haben, werden keine Ablaufverfolgungsereignisse mehr aufgezeichnet. Die Ablaufverfolgung wird jedoch fortgesetzt.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Profiler](sql-server-profiler.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
