---
title: SP:CacheRemove (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
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
- SP:CacheRemove event class
ms.assetid: aaa3c5c4-2d3a-4832-a473-ce9bd4fb1c17
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db6b0933af52271698622b86b848de16ecbd7cb2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050543"
---
# <a name="spcacheremove-event-class"></a>SP:CacheRemove-Ereignisklasse
  Die SP:CacheRemove-Ereignisklasse zeigt an, dass die gespeicherte Prozedur aus dem Plancache entfernt wurde.  
  
## <a name="spcacheremove-event-class-data-columns"></a>Datenspalten der SP:CacheRemove-Ereignisklasse  
  
|Datenspaltenname|`Data type`|Description|Column ID|Filterbar|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|ja|  
|DatabaseID|`int`|ID der Datenbank, in der die gespeicherte Prozedur ausgeführt wird. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die gespeicherte Prozedur ausgeführt wird.|35|ja|  
|EventClass|`int`|Ereignistyp = 36.|27|nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|EventSubClass|`int`|Der Typ der Ereignisunterklasse:<br /><br /> 1 = Compplan Remove. Ein kompilierter Abfrageplan wurde aus dem Cache entfernt.<br /><br /> 2 = Proc Cache Flush. Alle Einträge wurden aus dem Prozedurcache entfernt.|21|ja|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|ja|  
|LoginName|`nvarchar`|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|ja|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|ja|  
|ObjectID|`int`|Vom System zugewiesene ID der gespeicherten Prozedur.|22|ja|  
|ObjectType|`int`|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Dieser Wert entspricht der type-Spalte in der sys.objects-Katalogsicht. Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](objecttype-trace-event-column.md).|28|ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|ja|  
|TextData|`ntext`|Der Text der SQL-Anweisung, die aus dem Cache entfernt wird.|1|ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|ja|  
|XactSequence|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
