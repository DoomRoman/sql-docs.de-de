---
title: Assembly Load-Ereignisklasse | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- Assembly Load event class
ms.assetid: cfb0b69d-4ce0-4067-a3df-d82775e57886
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a84684a039ccd6276fa2be42e8fd59f5e845befa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048328"
---
# <a name="assembly-load-event-class"></a>Assembly Load-Ereignisklasse
  Die **Assembly Load** -Ereignisklasse tritt auf, wenn eine Anforderung zum Laden einer Assembly ausgeführt wird.  
  
 Schließen Sie die **Assembly Load** -Ereignisklasse in Ablaufverfolgungen ein, mit denen Sie Assemblyauslastungen überwachen möchten. Dies kann hilfreich sein für die Problembehandlung einer Abfrage, die CLR (Common Language Runtime) verwendet, bei der Problembehandlung eines langsamen Servers, der CLR-Abfragen ausführt, oder wenn ein Server überwacht wird, um Benutzer-, Datenbank- Erfolgs- oder sonstige Informationen zu Assemblyladevorgängen zu sammeln.  
  
## <a name="assembly-load-event-class-data-columns"></a>Datenspalten der Assembly Load-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Anwendung, die den Ladevorgang angefordert hat|10|ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE-Datenbankanweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE-Datenbankanweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|ja|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**GroupID**|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|ja|  
|**LoginName**|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|ja|  
|**LoginSID**|**image**|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|ja|  
|**ObjectID**|**int**|Assembly-ID|22|ja|  
|**ObjectName**|**nvarchar**|Der vollqualifizierte Name der Assembly|34|ja|  
|**RequestID**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|ja|  
|**Success**|**int**|Gibt an, ob der Assemblyladevorgang erfolgreich ausgeführt wurde (1) oder ob ein Fehler gemeldet wurde (0)|23|ja|  
|**TextData**|**ntext**|"Assembly Load Succeeded" bei erfolgreichem Laden, andernfalls "Assembly Load Failed".|1|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../relational-databases/extended-events/extended-events.md)   
 
  [Assemblys &amp;#40;Datenbank-Engine&amp;#41;](../relational-databases/clr-integration/assemblies-database-engine.md)  
  
  