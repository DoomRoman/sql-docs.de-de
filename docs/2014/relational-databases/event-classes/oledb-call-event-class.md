---
title: OLE DB Call-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB Call event class
ms.assetid: e1be1e90-98cc-47a3-addd-59d4aeca6547
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 954ba93ab5c32a9fa957133a6b8b10682ed7d019
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133403"
---
# <a name="oledb-call-event-class"></a>OLE DB Call-Ereignisklasse
  Die **OLEDB Call** -Ereignisklasse tritt auf, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen OLE DB-Anbieter für verteilte Abfragen und remote gespeicherte Prozeduren aufruft.  
  
 Schließen Sie die **OLEDB Call** -Ereignisklasse in Ablaufverfolgungen ein, um nur jene Aufrufe zu überwachen, die keine Daten anfordern, oder jene Aufrufe, die nicht für die **QueryInterface** -Methode ausgeführt werden. Wenn die **OLEDB Call** -Ereignisklasse in eine Ablaufverfolgung eingeschlossen wird, ist der Mehraufwand davon abhängig, wie häufig OLE DB-Aufrufe für die Datenbank während der Ablaufverfolgung auftreten. Wenn Aufrufe häufig auftreten, kann die Ablaufverfolgung die Leistung bedeutend beeinträchtigen.  
  
## <a name="oledb-call-event-class-data-columns"></a>OLEDB Call (Ereignisklassen-Datenspalten)  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|ClientProcessID|`Int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Benutzerkontensteuerung|  
|DatabaseID|`Int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|Duration|`Bigint`|Zeit, die zum Abschließen des OLE DB-Aufrufereignisses erforderlich ist|13|nein|  
|EndTime|`Datetime`|Zeitpunkt, zu dem das Ereignis beendet wurde|15|Benutzerkontensteuerung|  
|Fehler|`int`|Fehlernummer eines bestimmten Ereignisses. Dies ist häufig die in der sys.messages-Katalogsicht gespeicherte Fehlernummer.|31|Benutzerkontensteuerung|  
|EventClass|`Int`|Ereignistyp = 119.|27|nein|  
|EventSequence|`Int`|Sequenz der OLE DB-Ereignisklasse im Batch|51|nein|  
|EventSubClass|`Int`|0=Wird gestartet<br /><br /> 1 = Abgeschlossen|21|nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Benutzerkontensteuerung|  
|LinkedServerName|`nvarchar`|Name des Verbindungsservers|45|Benutzerkontensteuerung|  
|LoginName|`nvarchar`|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Benutzerkontensteuerung|  
|LoginSid|`Image`|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|MethodName|`nvarchar`|Der Name der OLE DB-Methode.|47|Benutzerkontensteuerung|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Benutzerkontensteuerung|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Benutzerkontensteuerung|  
|ProviderName|`nvarchar`|Name des OLE DB-Anbieters.|46|Benutzerkontensteuerung|  
|RequestID|`Int`|Die ID der Anforderung, die die Anweisung enthält.|49|Benutzerkontensteuerung|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Angenommen, Herstellen einer Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von Login1 herstellen und eine Anweisung als Login2 ausführen, `SessionLoginName` Login1 an und `LoginName` zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|SPID|`Int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|TextData|`nvarchar`|Während des OLE DB-Aufrufs gesendete und empfangene Parameter|1|nein|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [OLE-Automatisierungsobjekte in Transact-SQL](../stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  
