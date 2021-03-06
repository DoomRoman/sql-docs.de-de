---
title: Security Audit Data Columns | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06bb8b1c6906ebbced1ed7cf52d254564c77d084
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34045554"
---
# <a name="security-audit-data-columns"></a>Sicherheitsüberwachung-Datenspalten
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die Sicherheitsüberwachungs-Ereigniskategorie verfügt über die folgenden Ereignisklassen:  
  
||||  
|-|-|-|  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|1|Audit Login|Sammelt alle neuen Verbindungsereignisse seit dem Start der Ablaufverfolgung (z. B., wenn ein Client eine Verbindung mit einem Server anfordert, auf dem eine SQL Server-Instanz ausgeführt wird).|  
|2|Audit Logout|Sammelt alle neuen Ereignisse zum Trennen einer Verbindung, die seit dem Start der Ablaufverfolgung eingetreten sind, z. B. wenn ein Client einen Befehl zum Trennen der Verbindung ausgibt.|  
|4|Audit Server Starts and Stops|Erfasst das Herunterfahren von Diensten, startet Aktivitäten und hält sie an.|  
|18|Audit Object Permission Event|Erfasst Objektberechtigungsänderungen.|  
|19|Audit Admin Operations-Ereignis|Erfasst Serversicherung/-wiederherstellung/-synchronisierung/-anfügung/-trennung/Laden von Bildern (imageload)/Speichern von Bildern (imagesave).|  
  
 In den folgenden Tabellen sind die Datenspalten für jede dieser Ereignisklassen aufgeführt.  
  
## <a name="audit-login"></a>Audit Login  
  
|||||  
|-|-|-|-|  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|CurrentTime|2|5|Der Zeitpunkt, zu dem das Ereignis begonnen hat (falls verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|StartTime|3|5|Der Zeitpunkt, zu dem das Ereignis begonnen hat (falls verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|Severity|22|1|Schweregrad einer Ausnahme.|  
|Success|23|1|1 = Erfolg 0 = Fehler (z. B. gibt 1 den Erfolg einer Berechtigungsüberprüfung und 0 einen Fehler bei dieser Überprüfung an).|  
|Fehler|24|1|Fehlernummer eines bestimmten Ereignisses.|  
|ConnectionID|25|1|Eindeutige Verbindungs-ID.|  
|NTUserName|32|8|Windows-Benutzername.|  
|NTDomainName|33|8|Windows-Domäne, zu der der Benutzer gehört.|  
|ClientHostName|35|8|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird.|  
|ClientProcessID|36|1|Die Prozess-ID der Clientanwendung.|  
|ApplicationName|37|8|Der Name der Clientanwendung, die die Verbindung mit dem Server hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|  
|NTCanonicalUserName|40|8|Benutzername in kanonischer Form. Zum Beispiel "engineering.microsoft.com/software/someone".|  
|ServerName|43|8|Name des Servers, der das Ereignis erzeugt.|  
  
## <a name="audit-logout"></a>Audit Logout  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|CurrentTime|2|5|Der Zeitpunkt, zu dem das Ereignis begonnen hat (falls verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|EndTime|4|5|Der Zeitpunkt, zu dem das Ereignis beendet wurde. Diese Spalte wird für Startereignisklassen (z. B. SQL:BatchStarting oder SP:Starting) nicht aufgefüllt. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|Dauer|5|2|Die Zeit (in Millisekunden), die für das Ereignis benötigt wurde.|  
|CPUTime|6|2|Die CPU-Zeit (in Millisekunden), die vom Ereignis verwendet wurde.|  
|Success|23|1|1 = Erfolg 0 = Fehler (z. B. gibt 1 den Erfolg einer Berechtigungsüberprüfung und 0 einen Fehler bei dieser Überprüfung an).|  
|ConnectionID|25|1|Eindeutige Verbindungs-ID.|  
|NTUserName|32|8|Windows-Benutzername.|  
|NTDomainName|33|8|Windows-Domäne, zu der der Benutzer gehört.|  
|ClientHostName|35|8|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird.|  
|ClientProcessID|36|1|Die Prozess-ID der Clientanwendung.|  
|ApplicationName|37|8|Der Name der Clientanwendung, die die Verbindung mit dem Server hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|  
|NTCanonicalUserName|40|8|Benutzername in kanonischer Form. Zum Beispiel "engineering.microsoft.com/software/someone".|  
|ServerName|43|8|Name des Servers, der das Ereignis erzeugt.|  
  
## <a name="audit-server-starts-and-stops"></a>Audit Server Starts and Stops  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|EventSubclass|1|1|Die Ereignisunterklasse enthält zusätzliche Informationen zu jeder Ereignisklasse.<br /><br /> 1: Instanz heruntergefahren<br /><br /> 2: Instanz gestartet<br /><br /> 3: Instanz angehalten<br /><br /> 4: Instanz fortgesetzt|  
|CurrentTime|2|5|Der Zeitpunkt, zu dem das Ereignis begonnen hat (falls verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|Severity|22|1|Schweregrad einer Ausnahme.|  
|Success|23|1|1 = Erfolg 0 = Fehler (z. B. gibt 1 den Erfolg einer Berechtigungsüberprüfung und 0 einen Fehler bei dieser Überprüfung an).|  
|Fehler|24|1|Fehlernummer eines bestimmten Ereignisses.|  
|TextData|42|9|Dem Ereignis zugeordnete Textdaten.|  
|ServerName|43|8|Name des Servers, der das Ereignis erzeugt.|  
  
## <a name="audit-object-permission-event"></a>Audit Object Permission Event  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|ObjectID|11|8|Objekt-ID (beachten Sie, dass dies eine Zeichenfolge ist).|  
|ObjectType|12|1|Objekttyp.|  
|ObjectName|13|8|Objektname.|  
|ObjectPath|14|8|Objektpfad. Eine durch Trennzeichen getrennte Liste von übergeordneten Elementen, die beim übergeordneten Element des Objekts beginnt.|  
|ObjectReference|15|8|Objektverweis. Codiert als XML für alle übergeordneten Elemente, das Verwenden von Tags, um das Objekt zu beschreiben.|  
|Severity|22|1|Schweregrad einer Ausnahme.|  
|Success|23|1|1 = Erfolg 0 = Fehler (z. B. gibt 1 den Erfolg einer Berechtigungsüberprüfung und 0 einen Fehler bei dieser Überprüfung an).|  
|Fehler|24|1|Fehlernummer eines bestimmten Ereignisses.|  
|ConnectionID|25|1|Eindeutige Verbindungs-ID.|  
|DatabaseName|28|8|Name der Datenbank, in der die Anweisung des Benutzers ausgeführt wird.|  
|NTUserName|32|8|Windows-Benutzername.|  
|NTDomainName|33|8|Windows-Domäne, zu der der Benutzer gehört.|  
|ClientHostName|35|8|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird.|  
|ClientProcessID|36|1|Die Prozess-ID der Clientanwendung.|  
|ApplicationName|37|8|Der Name der Clientanwendung, die die Verbindung mit dem Server hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|  
|SessionID|39|8|Sitzungs-GUID.|  
|NTCanonicalUserName|40|8|Benutzername in kanonischer Form. Zum Beispiel "engineering.microsoft.com/software/someone".|  
|SPID|41|1|Serverprozess-ID. Hierdurch wird eine Benutzersitzung eindeutig gekennzeichnet. Dies entspricht direkt dem von XML/A verwendeten Sitzungs-GUID.|  
|TextData|42|9|Dem Ereignis zugeordnete Textdaten.|  
|ServerName|43|8|Name des Servers, der das Ereignis erzeugt.|  
  
## <a name="audit-admin-operations-event"></a>Audit Admin Operations-Ereignis  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventSubclass|1|1|Die Ereignisunterklasse enthält zusätzliche Informationen zu jeder Ereignisklasse.<br /><br /> 1: **Backup**<br /><br /> 2: **Restore**<br /><br /> 3: **Synchronize**<br /><br /> 4: **Detach**<br /><br /> 5: **Attach**<br /><br /> 6: **ImageLoad**<br /><br /> 7: **ImageSave**|  
|Severity|22|1|Schweregrad einer Ausnahme.|  
|Success|23|1|1 = Erfolg 0 = Fehler (z. B. gibt 1 den Erfolg einer Berechtigungsüberprüfung und 0 einen Fehler bei dieser Überprüfung an).|  
|Fehler|24|1|Fehlernummer eines bestimmten Ereignisses.|  
|ConnectionID|25|1|Eindeutige Verbindungs-ID.|  
|DatabaseName|28|8|Name der Datenbank, in der die Anweisung des Benutzers ausgeführt wird.|  
|NTUserName|32|8|Windows-Benutzername.|  
|NTDomainName|33|8|Windows-Domäne, zu der der Benutzer gehört.|  
|ClientHostName|35|8|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird.|  
|ClientProcessID|36|1|Die Prozess-ID der Clientanwendung.|  
|ApplicationName|37|8|Der Name der Clientanwendung, die die Verbindung mit dem Server hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|  
|SessionID|39|8|Sitzungs-GUID.|  
|NTCanonicalUserName|40|8|Benutzername in kanonischer Form. Zum Beispiel "engineering.microsoft.com/software/someone".|  
|SPID|41|1|Serverprozess-ID. Hierdurch wird eine Benutzersitzung eindeutig gekennzeichnet. Dies entspricht direkt dem von XML/A verwendeten Sitzungs-GUID.|  
|TextData|42|9|Dem Ereignis zugeordnete Textdaten.|  
|ServerName|43|8|Name des Servers, der das Ereignis erzeugt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberwachung-Ereigniskategorie](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
