---
title: MSSQLSERVER_17194 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eae4dd4577eea1fdbee1f9a23471cb7d94943ebe
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415969"
---
# <a name="mssqlserver17194"></a>MSSQLSERVER_17194
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17194|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Der Server konnte die für das Anmelden erforderliche SSL-Anbieterbibliothek nicht laden. Die Verbindung wurde geschlossen. SSL wird zum Verschlüsseln der Anmeldesequenz oder der gesamten Kommunikation verwendet, je nach der vom Administrator festgelegten Serverkonfiguration. Suchen Sie in der Onlinedokumentation nach Informationen zur folgenden Fehlermeldung: 0xXXXX. [CLIENT: 11.11.11.11]|  
  
## <a name="explanation"></a>Erklärung  
 Mit diesem Fehler wird angegeben, dass die Verbindung vom Client geschlossen wurde. Dieser Fehler ist möglicherweise darauf zurückzuführen, dass das Verbindungstimeout abgelaufen ist. In der Fehlermeldung wird ein Wert des Betriebssystems angezeigt, mit dem das zugrunde liegende Problem beschrieben wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn der Fehlercode in der Meldung 0x2746 lautet (Dezimalwert 10054), bedeutet dies, dass die Verbindung durch den Client zurückgesetzt wurde. Dies ist normalerweise auf ein Timeout zurückzuführen. Wenn Sie den Fehler beheben möchten, erhöhen Sie das Verbindungstimeout für den Client bzw. das aufrufende Programm.  
  
 Verwenden Sie zum Bestimmen einer möglichen Lösung für weitere Fehlermeldungswerte den Betriebssystembefehl **net helpmsg**, und geben Sie den Dezimalwert des Fehlercodes an.  
  
 Weitere Informationen zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Server-Netzwerkkonfiguration](../../database-engine/configure-windows/server-network-configuration.md) und [Client-Netzwerkkonfiguration](../../database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="internal-only"></a>Nur intern  
  
