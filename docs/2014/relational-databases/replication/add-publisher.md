---
title: Verleger hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.addpublisher.f1
helpviewer_keywords:
- Add Publisher dialog box
ms.assetid: 4b57e298-655f-42c2-82bc-25cdad94a194
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df8cd5e81352bbf0389e56de741f383a4f40d477
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215380"
---
# <a name="add-publisher"></a>Verleger hinzufügen
  Mithilfe des Dialogfelds **Verleger hinzufügen** können Sie dem linken Bereich des Replikationsmonitors einen oder mehrere Verleger hinzufügen. Nach dem Hinzufügen eines Verlegers werden durch das Auswählen des Verlegers im linken Bereich Informationen zu diesem Verleger im rechten Bereich anzeigt.  
  
## <a name="options"></a>Tastatur  
 **Hinzufügen**  
 Klicken Sie auf diese Option, um den Typ des hinzuzufügenden Verlegers auszuwählen. Dadurch wird das Dialogfeld **Verbindung mit Server herstellen** gestartet. Folgende Optionen sind verfügbar:  
  
-   **SQL Server-Verleger hinzufügen...**  
  
     Stellen Sie mithilfe des Dialogfelds **Verbindung mit Server herstellen** eine Verbindung mit dem Verleger her.  
  
-   **Oracle-Verleger hinzufügen...**  
  
     Stellen Sie mithilfe des Dialogfelds [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor associated with the Oracle Publisher using the **Connect to Server** dialog box.  
  
-   **Geben Sie einen Verteiler an, und fügen Sie seine Verleger hinzu…**  
  
     Stellt mithilfe des Dialogfelds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung mit Server herstellen **eine Verbindung mit dem** -Verteiler her, der einem oder mehreren Verlegern zugeordnet ist.  
  
 Nach einer erfolgreichen Verbindungsherstellung mit dem Verleger oder Verteiler werden die Namen aller Verleger und ihrer Verteiler in dem Raster im oberen Bereich des Dialogfelds angezeigt.  
  
> [!NOTE]  
>  Verteiler und Verleger werden oft auf derselben Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt, aber der Verteiler kann auch auf einer anderen Instanz ausgeführt werden (diese Konfiguration wird als Remoteverteiler bezeichnet).  
  
 **Entfernen**  
 Wählen Sie einen Verleger in dem Raster im oberen Bereich des Dialogfelds aus, und klicken Sie auf **Entfernen** , um den Verleger aus der Liste der hinzuzufügenden Verleger zu entfernen.  
  
> [!NOTE]  
>  Diese Schaltfläche kann nicht verwendet werden, um einen Verleger zu entfernen, der bereits im Replikationsmonitor angezeigt wird. Klicken Sie zum Entfernen eines Verteilers, der bereits im linken Bereich des Replikationsmonitors angezeigt wird, mit der rechten Maustaste auf den Verleger, und klicken Sie dann auf **Entfernen**.  
  
 **Beim Starten des Replikationsmonitors automatisch Verbindung herstellen**  
 Wählen Sie diese Option aus, damit der Replikationsmonitor automatisch eine Verbindung mit dem Verteiler herstellt und Statusinformationen für den Verleger abruft, der im Raster im oberen Bereich des Dialogfelds ausgewählt ist. Wenn dieses Kontrollkästchen deaktiviert ist, müssen Sie nach dem Starten des Replikationsmonitors manuell eine Verbindung herstellen: Klicken Sie dazu mit der rechten Maustaste auf den Verleger im linken Bereich des Replikationsmonitors, und klicken Sie dann auf **Verbinden**.  
  
 **Status dieses Verlegers und seiner Veröffentlichungen automatisch aktualisieren**  
 Wählen Sie diese Option aus, damit der Replikationsmonitor automatisch den Status für den Verleger aktualisiert, der im Raster im oberen Bereich des Dialogfelds ausgewählt ist. Wenn diese Option ausgewählt ist, ruft der Replikationsmonitor die Statusinformationen für den Verleger und seine Veröffentlichungen über den Verteiler ab. Das Abrufintervall wird durch die Option **Aktualisierungsrate** festgelegt. Weitere Informationen zum Aktualisieren im Replikationsmonitor finden Sie unter [Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors](monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Aktualisierungsrate**  
 Geben Sie einen Wert (in Sekunden) ein, um anzugeben, wie oft der Replikationsmonitor Statusinformationen über den Verteiler abrufen soll. Geringere Werte führen zu einem häufigeren Abruf, was die Leistung des Verteilers beeinträchtigen kann, wenn eine große Anzahl von Verlegern überwacht wird. Es wird empfohlen, das eigene System zu testen, um einen angemessenen Wert zu bestimmen. Die Einstellung **Aktualisierungsrate** wird ebenfalls verwendet, wenn Sie in einem der Detailfenster des Replikationsmonitors die Option **Automatisch aktualisieren** ausgewählt haben.  
  
 **Diese(n) Verleger in der folgenden Gruppe anzeigen**  
 Wählen Sie eine Verlegergruppe aus der Liste aus. Der Verleger wird unter dieser Gruppe im linken Bereich angezeigt. Gruppen stellen eine Möglichkeit zum Organisieren von Verlegern dar und haben keinen Einfluss auf die Funktion der Replikation. Wenn keine Gruppen definiert wurden oder Sie eine neue Gruppe erstellen möchten, dann klicken Sie auf **Neue Gruppe**.  
  
 **Neue Gruppe**  
 Klicken Sie auf diese Option, um eine neue Verlegergruppe zu erstellen. Eine Verlegergruppe stellt eine einfache Möglichkeit dar, um die Verleger innerhalb des Replikationsmonitors zu organisieren. Gruppen haben keinen Einfluss auf die Replikation der Daten oder die Beziehungen zwischen den Servern in der Replikationstopologie.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
