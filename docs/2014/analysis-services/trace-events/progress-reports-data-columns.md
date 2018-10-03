---
title: Fortschrittsberichte – Datenspalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Progress Reports event category
ms.assetid: d34a6322-e26b-4454-b98f-32307d6956b5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8569f18f3838116ea5a1ed045f418602f85032c6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171170"
---
# <a name="progress-reports-data-columns"></a>Datenspalten für Fortschrittsbericht
  Die Fortschrittsbericht-Ereigniskategorie enthält die folgenden Ereignisklassen:  
  
|**Ereignis-ID**|**Ereignisname**|**Ereignisbeschreibung**|  
|------------------|--------------------|---------------------------|  
|5|Progress Report Begin|Beginn des Fortschrittsberichts.|  
|6|Progress Report End|Der Statusbericht wurde beendet.|  
|7|Progress Report Current|Der Statusbericht wird ausgeführt.|  
|8|Progress Report Error|Es ist ein Statusberichtfehler aufgetreten.|  
  
 In den folgenden Tabellen sind die Datenspalten für jede dieser Ereignisklassen aufgeführt.  
  
## <a name="progress-report-begindata-columns"></a>Progress Report Begin-Datenspalten  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|EventSubclass|1|1|Die Ereignisunterklasse enthält zusätzliche Informationen zu jeder Ereignisklasse.<br /><br /> 1: Prozess<br /><br /> 2: Zusammenführen<br /><br /> 3: Löschen<br /><br /> 4: DeleteOldAggregations<br /><br /> 5: neu erstellen<br /><br /> 6: Commit ausführen<br /><br /> 7: Zurücksetzen<br /><br /> 8: CreateIndexes<br /><br /> 9: CreateTable<br /><br /> 10: InsertInto<br /><br /> 11: Transaktion<br /><br /> 12: Initialisieren<br /><br /> 13: Diskretisieren<br /><br /> 14: Abfrage<br /><br /> 15: CreateView<br /><br /> 16: Daten schreiben<br /><br /> 17: ReadData<br /><br /> 18: GroupData<br /><br /> 19: GroupDataRecord<br /><br /> 20: BuildIndex<br /><br /> 21: aggregieren<br /><br /> 22: BuildDecode<br /><br /> 23: WriteDecode<br /><br /> 24: BuildDMDecode<br /><br /> 25: ExecuteSQL<br /><br /> 26: ExecuteModifiedSQL<br /><br /> 27: Herstellen einer Verbindung<br /><br /> 28: BuildAggsAndIndexes<br /><br /> 29: MergeAggsOnDisk<br /><br /> 30: BuildIndexForRigidAggs<br /><br /> 31: BuildIndexForFlexibleAggs<br /><br /> 32: WriteAggsAndIndexes<br /><br /> 33: WriteSegment<br /><br /> 34: DataMiningProgress<br /><br /> 35: ReadBufferFullReport<br /><br /> 36: ProactiveCacheConversion<br /><br /> 37: Sicherung<br /><br /> 38: Wiederherstellen<br /><br /> 39: Synchronisieren<br /><br /> 40: Erstellen des Verarbeitungszeitplans<br /><br /> 41: Trennen<br /><br /> 42: Anfügen<br /><br /> 43: Analyze\Encode-Daten<br /><br /> 44: Segment komprimieren<br /><br /> 45: Tabellenspalte schreiben<br /><br /> 46: Vorbereiten der Beziehung erstellen<br /><br /> 47: Erstellen der Beziehung-Segment<br /><br /> 48: Laden<br /><br /> 49: Laden von Metadaten<br /><br /> 50: Laden von Daten<br /><br /> 51: postload-Vorgang<br /><br /> 52: Metadaten durchlaufen, während der Sicherung<br /><br /> 53: VertiPaq<br /><br /> 54: hierarchieverarbeitung<br /><br /> 55: durch den Wechsel des Wörterbuchs.|  
|CurrentTime|2|5|Enthält die aktuelle Zeit des gemeldeten Ereignisses (wenn verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|StartTime|3|5|Enthält den Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|JobID|7|1|Enthält die Auftrags-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|SessionType|8|8|Enthält den Sitzungstyp (die Entität, die das Ereignis bewirkt hat), der dem gemeldeten Ereignis zugeordnet ist. Für Verarbeitungsereignisse lauten die Werte folgendermaßen:<br /><br /> 1 = Benutzer<br /><br /> 2= Proaktives Zwischenspeichern<br /><br /> 3= Verzögertes Verarbeiten|  
|ObjectID|11|8|Enthält die Objekt-ID (eine Zeichenfolge), die dem gemeldeten Ereignis zugeordnet ist.|  
|ObjectType|12|1|Enthält den Objekttyp.|  
|ObjectName|13|8|Enthält den Namen des Objekts, das dem gemeldeten Ereignis zugeordnet ist.|  
|ObjectPath|14|8|Enthält den Objektpfad für das Objekt, das dem gemeldeten Ereignis zugeordnet ist, als durch Trennzeichen getrennte Liste der übergeordneten Elemente, beginnend mit den übergeordneten Elementen des Objekts.|  
|ObjectReference|15|8|Enthält den Objektverweis für das gemeldete Ereignis, als XML für alle übergeordneten Elemente codiert. Zum Beschreiben des Objekts werden Tags verwendet.|  
|ConnectionID|25|1|Enthält die eindeutige Verbindungs-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|DatabaseName|28|8|Enthält den Namen der Datenbank, in der das gemeldete Ereignis aufgetreten ist.|  
|NTUserName|32|8|Enthält das Windows-Benutzerkonto, das dem gemeldeten Ereignis zugeordnet ist.|  
|NTDomainName|33|8|Enthält das Windows-Domänenkonto, das dem gemeldeten Ereignis zugeordnet ist.|  
|SessionID|39|8|Enthält die Sitzungs-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|NTCanonicalUserName|40|8|Benutzername in kanonischer Form. Zum Beispiel "engineering.microsoft.com/software/someone".|  
|SPID|41|1|Enthält die Serverprozess-ID (SPID), die die dem gemeldeten Ereignis zugeordnete Benutzersitzung eindeutig identifiziert. Die SPID entspricht direkt der Sitzungs-GUID, die von XMLA (XML for Analysis) verwendet wird.|  
|TextData|42|9|Enthält die Textdaten, die dem gemeldeten Ereignis zugeordnet sind.|  
|ServerName|43|8|Enthält den Namen der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , für die das gemeldete Ereignis eingetreten ist.|  
  
## <a name="progress-report-enddata-columns"></a>Progress Report End-Datenspalten  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|EventSubclass|1|1|Die Ereignisunterklasse enthält zusätzliche Informationen zu jeder Ereignisklasse.<br /><br /> 1: Prozess<br /><br /> 2: Zusammenführen<br /><br /> 3: Löschen<br /><br /> 4: DeleteOldAggregations<br /><br /> 5: neu erstellen<br /><br /> 6: Commit ausführen<br /><br /> 7: Zurücksetzen<br /><br /> 8: CreateIndexes<br /><br /> 9: CreateTable<br /><br /> 10: InsertInto<br /><br /> 11: Transaktion<br /><br /> 12: Initialisieren<br /><br /> 13: Diskretisieren<br /><br /> 14: Abfrage<br /><br /> 15: CreateView<br /><br /> 16: Daten schreiben<br /><br /> 17: ReadData<br /><br /> 18: GroupData<br /><br /> 19: GroupDataRecord<br /><br /> 20: BuildIndex<br /><br /> 21: aggregieren<br /><br /> 22: BuildDecode<br /><br /> 23: WriteDecode<br /><br /> 24: BuildDMDecode<br /><br /> 25: ExecuteSQL<br /><br /> 26: ExecuteModifiedSQL<br /><br /> 27: Herstellen einer Verbindung<br /><br /> 28: BuildAggsAndIndexes<br /><br /> 29: MergeAggsOnDisk<br /><br /> 30: BuildIndexForRigidAggs<br /><br /> 31: BuildIndexForFlexibleAggs<br /><br /> 32: WriteAggsAndIndexes<br /><br /> 33: WriteSegment<br /><br /> 34: DataMiningProgress<br /><br /> 35: ReadBufferFullReport<br /><br /> 36: ProactiveCacheConversion<br /><br /> 37: Sicherung<br /><br /> 38: Wiederherstellen<br /><br /> 39: Synchronisieren<br /><br /> 40: Erstellen des Verarbeitungszeitplans<br /><br /> 41: Trennen<br /><br /> 42: Anfügen<br /><br /> 43: Analyze\Encode-Daten<br /><br /> 44: Segment komprimieren<br /><br /> 45: Tabellenspalte schreiben<br /><br /> 46: Vorbereiten der Beziehung erstellen<br /><br /> 47: Erstellen der Beziehung-Segment<br /><br /> 48: Laden<br /><br /> 49: Laden von Metadaten<br /><br /> 50: Laden von Daten<br /><br /> 51: postload-Vorgang<br /><br /> 52: Metadaten durchlaufen, während der Sicherung<br /><br /> 53: VertiPaq<br /><br /> 54: hierarchieverarbeitung<br /><br /> 55: durch den Wechsel des Wörterbuchs.|  
|CurrentTime|2|5|Enthält die aktuelle Zeit des gemeldeten Ereignisses (wenn verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|StartTime|3|5|Enthält den Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|EndTime|4|5|Enthält die Uhrzeit, zu der das Ereignis beendet wurde. Diese Spalte wird für Startereignisklassen (z. B. SQL:BatchStarting oder SP:Starting) nicht aufgefüllt. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|Duration|5|2|Enthält die abgelaufene Zeit (in Millisekunden), die für das Ereignis benötigt wurde.|  
|CPUTime|6|2|Enthält die CPU-Zeit (in Millisekunden), die vom Ereignis verwendet wurde.|  
|JobID|7|1|Enthält die Auftrags-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|SessionType|8|8|Enthält den Sitzungstyp (die Entität, die das Ereignis bewirkt hat), der dem gemeldeten Ereignis zugeordnet ist. Für Verarbeitungsereignisse lauten die Werte folgendermaßen:<br /><br /> 1 = Benutzer<br /><br /> 2= Proaktives Zwischenspeichern<br /><br /> 3= Verzögertes Verarbeiten|  
|ProgressTotal|9|1|Enthält den Gesamtfortschritt für das gemeldete Ereignis.|  
|IntegerData|10|1|Enthält die ganzzahligen Daten, die dem gemeldeten Ereignis zugeordnet sind, z. B. die aktuelle Anzahl der für ein Verarbeitungsereignis verarbeiteten Zeilen.|  
|ObjectID|11|8|Enthält die Objekt-ID (eine Zeichenfolge), die dem gemeldeten Ereignis zugeordnet ist.|  
|ObjectType|12|1|Enthält den Objekttyp.|  
|ObjectName|13|8|Enthält den Namen des Objekts, das dem gemeldeten Ereignis zugeordnet ist.|  
|ObjectPath|14|8|Enthält den Objektpfad für das Objekt, das dem gemeldeten Ereignis zugeordnet ist, als durch Trennzeichen getrennte Liste der übergeordneten Elemente, beginnend mit den übergeordneten Elementen des Objekts.|  
|ObjectReference|15|8|Enthält den Objektverweis für das gemeldete Ereignis, als XML für alle übergeordneten Elemente codiert. Zum Beschreiben des Objekts werden Tags verwendet.|  
|Schweregrad|22|1|Enthält den Schweregrad einer Ausnahme, die dem gemeldeten Ereignis zugeordnet ist. Die Werte sind:<br /><br /> 0 = Erfolg<br /><br /> 1 = Information<br /><br /> 2 = Warnung<br /><br /> 3 = Fehler|  
|Success|23|1|Enthält die Angabe zum Erfolg oder Fehlschlagen des vom Server gemeldeten Ereignisses. Die Werte sind:<br /><br /> 0 = Fehler<br /><br /> 1 = Erfolg|  
|Fehler|24|1|Enthält die Fehlernummer von einem angegebenen Ereignis.|  
|ConnectionID|25|1|Enthält die eindeutige Verbindungs-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|DatabaseName|28|8|Enthält den Namen der Datenbank, in der das gemeldete Ereignis aufgetreten ist.|  
|NTUserName|32|8|Enthält das Windows-Benutzerkonto, das dem gemeldeten Ereignis zugeordnet ist.|  
|NTDomainName|33|8|Enthält das Windows-Domänenkonto, das dem gemeldeten Ereignis zugeordnet ist.|  
|SessionID|39|8|Enthält die Sitzungs-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|NTCanonicalUserName|40|8|Enthält den Windows-Benutzernamen, der dem gemeldeten Ereignis zugeordnet ist. Der Benutzername liegt im kanonischen Format vor. Beispiel: engineering.microsoft.com/software/user.|  
|SPID|41|1|Enthält die Serverprozess-ID (SPID), die die dem gemeldeten Ereignis zugeordnete Benutzersitzung eindeutig identifiziert. Die SPID entspricht direkt der Sitzungs-GUID, die von XMLA (XML for Analysis) verwendet wird.|  
|TextData|42|9|Enthält die Textdaten, die dem gemeldeten Ereignis zugeordnet sind.|  
|ServerName|43|8|Enthält den Namen der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , für die das gemeldete Ereignis eingetreten ist.|  
  
## <a name="progress-report-currentdata-columns"></a>Progress Report Current-Datenspalten  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|EventSubclass|1|1|Die Ereignisunterklasse enthält zusätzliche Informationen zu jeder Ereignisklasse.<br /><br /> 1: Prozess<br /><br /> 2: Zusammenführen<br /><br /> 3: Löschen<br /><br /> 4: DeleteOldAggregations<br /><br /> 5: neu erstellen<br /><br /> 6: Commit ausführen<br /><br /> 7: Zurücksetzen<br /><br /> 8: CreateIndexes<br /><br /> 9: CreateTable<br /><br /> 10: InsertInto<br /><br /> 11: Transaktion<br /><br /> 12: Initialisieren<br /><br /> 13: Diskretisieren<br /><br /> 14: Abfrage<br /><br /> 15: CreateView<br /><br /> 16: Daten schreiben<br /><br /> 17: ReadData<br /><br /> 18: GroupData<br /><br /> 19: GroupDataRecord<br /><br /> 20: BuildIndex<br /><br /> 21: aggregieren<br /><br /> 22: BuildDecode<br /><br /> 23: WriteDecode<br /><br /> 24: BuildDMDecode<br /><br /> 25: ExecuteSQL<br /><br /> 26: ExecuteModifiedSQL<br /><br /> 27: Herstellen einer Verbindung<br /><br /> 28: BuildAggsAndIndexes<br /><br /> 29: MergeAggsOnDisk<br /><br /> 30: BuildIndexForRigidAggs<br /><br /> 31: BuildIndexForFlexibleAggs<br /><br /> 32: WriteAggsAndIndexes<br /><br /> 33: WriteSegment<br /><br /> 34: DataMiningProgress<br /><br /> 35: ReadBufferFullReport<br /><br /> 36: ProactiveCacheConversion<br /><br /> 37: Sicherung<br /><br /> 38: Wiederherstellen<br /><br /> 39: Synchronisieren<br /><br /> 40: Erstellen des Verarbeitungszeitplans<br /><br /> 41: Trennen<br /><br /> 42: Anfügen<br /><br /> 43: Analyze\Encode-Daten<br /><br /> 44: Segment komprimieren<br /><br /> 45: Tabellenspalte schreiben<br /><br /> 46: Vorbereiten der Beziehung erstellen<br /><br /> 47: Erstellen der Beziehung-Segment<br /><br /> 48: Laden<br /><br /> 49: Laden von Metadaten<br /><br /> 50: Laden von Daten<br /><br /> 51: postload-Vorgang<br /><br /> 52: Metadaten durchlaufen, während der Sicherung<br /><br /> 53: VertiPaq<br /><br /> 54: hierarchieverarbeitung<br /><br /> 55: durch den Wechsel des Wörterbuchs.|  
|CurrentTime|2|5|Enthält die aktuelle Zeit des gemeldeten Ereignisses (wenn verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|StartTime|3|5|Enthält den Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|JobID|7|1|Enthält die Auftrags-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|SessionType|8|8|Enthält den Sitzungstyp (die Entität, die das Ereignis bewirkt hat), der dem gemeldeten Ereignis zugeordnet ist. Für Verarbeitungsereignisse lauten die Werte folgendermaßen:<br /><br /> 1 = Benutzer<br /><br /> 2= Proaktives Zwischenspeichern<br /><br /> 3= Verzögertes Verarbeiten|  
|ProgressTotal|9|1|Enthält den Gesamtfortschritt für das gemeldete Ereignis.|  
|IntegerData|10|1|Enthält die ganzzahligen Daten, die dem gemeldeten Ereignis zugeordnet sind, z. B. die aktuelle Anzahl der für ein Verarbeitungsereignis verarbeiteten Zeilen.|  
|ObjectID|11|8|Enthält die Objekt-ID (eine Zeichenfolge), die dem gemeldeten Ereignis zugeordnet ist.|  
|ObjectType|12|1|Enthält den Objekttyp.|  
|ObjectName|13|8|Enthält den Namen des Objekts, das dem gemeldeten Ereignis zugeordnet ist.|  
|ObjectPath|14|8|Enthält den Objektpfad für das Objekt, das dem gemeldeten Ereignis zugeordnet ist, als durch Trennzeichen getrennte Liste der übergeordneten Elemente, beginnend mit den übergeordneten Elementen des Objekts.|  
|ObjectReference|15|8|Enthält den Objektverweis für das gemeldete Ereignis, als XML für alle übergeordneten Elemente codiert. Zum Beschreiben des Objekts werden Tags verwendet.|  
|ConnectionID|25|1|Enthält die eindeutige Verbindungs-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|DatabaseName|28|8|Enthält den Namen der Datenbank, in der das gemeldete Ereignis aufgetreten ist.|  
|SessionID|39|8|Enthält die Sitzungs-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|SPID|41|1|Enthält die Serverprozess-ID (SPID), die die dem gemeldeten Ereignis zugeordnete Benutzersitzung eindeutig identifiziert. Die SPID entspricht direkt der Sitzungs-GUID, die von XMLA (XML for Analysis) verwendet wird.|  
|TextData|42|9|Enthält die Textdaten, die dem gemeldeten Ereignis zugeordnet sind.|  
|ServerName|43|8|Enthält den Namen der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , für die das gemeldete Ereignis eingetreten ist.|  
  
## <a name="progress-report-errordata-columns"></a>Progress Report Error-Datenspalten  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|EventSubclass|1|1|Die Ereignisunterklasse enthält zusätzliche Informationen zu jeder Ereignisklasse.<br /><br /> 1: Prozess<br /><br /> 2: Zusammenführen<br /><br /> 3: Löschen<br /><br /> 4: DeleteOldAggregations<br /><br /> 5: neu erstellen<br /><br /> 6: Commit ausführen<br /><br /> 7: Zurücksetzen<br /><br /> 8: CreateIndexes<br /><br /> 9: CreateTable<br /><br /> 10: InsertInto<br /><br /> 11: Transaktion<br /><br /> 12: Initialisieren<br /><br /> 13: Diskretisieren<br /><br /> 14: Abfrage<br /><br /> 15: CreateView<br /><br /> 16: Daten schreiben<br /><br /> 17: ReadData<br /><br /> 18: GroupData<br /><br /> 19: GroupDataRecord<br /><br /> 20: BuildIndex<br /><br /> 21: aggregieren<br /><br /> 22: BuildDecode<br /><br /> 23: WriteDecode<br /><br /> 24: BuildDMDecode<br /><br /> 25: ExecuteSQL<br /><br /> 26: ExecuteModifiedSQL<br /><br /> 27: Herstellen einer Verbindung<br /><br /> 28: BuildAggsAndIndexes<br /><br /> 29: MergeAggsOnDisk<br /><br /> 30: BuildIndexForRigidAggs<br /><br /> 31: BuildIndexForFlexibleAggs<br /><br /> 32: WriteAggsAndIndexes<br /><br /> 33: WriteSegment<br /><br /> 34: DataMiningProgress<br /><br /> 35: ReadBufferFullReport<br /><br /> 36: ProactiveCacheConversion<br /><br /> 37: Sicherung<br /><br /> 38: Wiederherstellen<br /><br /> 39: Synchronisieren<br /><br /> 40: Erstellen des Verarbeitungszeitplans<br /><br /> 41: Trennen<br /><br /> 42: Anfügen<br /><br /> 43: Analyze\Encode-Daten<br /><br /> 44: Segment komprimieren<br /><br /> 45: Tabellenspalte schreiben<br /><br /> 46: Vorbereiten der Beziehung erstellen<br /><br /> 47: Erstellen der Beziehung-Segment<br /><br /> 48: Laden<br /><br /> 49: Laden von Metadaten<br /><br /> 50: Laden von Daten<br /><br /> 51: postload-Vorgang<br /><br /> 52: Metadaten durchlaufen, während der Sicherung<br /><br /> 53: VertiPaq<br /><br /> 54: hierarchieverarbeitung<br /><br /> 55: durch den Wechsel des Wörterbuchs.|  
|CurrentTime|2|5|Enthält die aktuelle Zeit des gemeldeten Ereignisses (wenn verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|StartTime|3|5|Enthält den Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|EndTime|4|5|Enthält die Uhrzeit, zu der das Ereignis beendet wurde. Diese Spalte wird für Startereignisklassen (z. B. SQL:BatchStarting oder SP:Starting) nicht aufgefüllt. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|Duration|5|2|Enthält die abgelaufene Zeit (in Millisekunden), die für das Ereignis benötigt wurde.|  
|JobID|7|1|Enthält die Auftrags-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|SessionType|8|8|Enthält den Sitzungstyp (die Entität, die das Ereignis bewirkt hat), der dem gemeldeten Ereignis zugeordnet ist. Für Verarbeitungsereignisse lauten die Werte folgendermaßen:<br /><br /> 1 = Benutzer<br /><br /> 2= Proaktives Zwischenspeichern<br /><br /> 3= Verzögertes Verarbeiten|  
|ProgressTotal|9|1|Enthält den Gesamtfortschritt für das gemeldete Ereignis.|  
|IntegerData|10|1|Enthält die ganzzahligen Daten, die dem gemeldeten Ereignis zugeordnet sind, z. B. die aktuelle Anzahl der für ein Verarbeitungsereignis verarbeiteten Zeilen.|  
|ObjectID|11|8|Enthält die Objekt-ID (eine Zeichenfolge), die dem gemeldeten Ereignis zugeordnet ist.|  
|ObjectType|12|1|Enthält den Objekttyp.|  
|ObjectName|13|8|Enthält den Namen des Objekts, das dem gemeldeten Ereignis zugeordnet ist.|  
|ObjectPath|14|8|Enthält den Objektpfad für das Objekt, das dem gemeldeten Ereignis zugeordnet ist, als durch Trennzeichen getrennte Liste der übergeordneten Elemente, beginnend mit den übergeordneten Elementen des Objekts.|  
|ObjectReference|15|8|Enthält den Objektverweis für das gemeldete Ereignis, als XML für alle übergeordneten Elemente codiert. Zum Beschreiben des Objekts werden Tags verwendet.|  
|Schweregrad|22|1|Enthält den Schweregrad einer Ausnahme, die dem gemeldeten Ereignis zugeordnet ist. Die Werte sind:<br /><br /> 0 = Erfolg<br /><br /> 1 = Information<br /><br /> 2 = Warnung<br /><br /> 3 = Fehler|  
|Fehler|24|1|Enthält die Fehlernummer von einem angegebenen Ereignis.|  
|ConnectionID|25|1|Enthält die eindeutige Verbindungs-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|DatabaseName|28|8|Enthält den Namen der Datenbank, in der das gemeldete Ereignis aufgetreten ist.|  
|SessionID|39|8|Enthält die Sitzungs-ID, die dem gemeldeten Ereignis zugeordnet ist.|  
|SPID|41|1|Enthält die Serverprozess-ID (SPID), die die dem gemeldeten Ereignis zugeordnete Benutzersitzung eindeutig identifiziert. Die SPID entspricht direkt der Sitzungs-GUID, die von XMLA (XML for Analysis) verwendet wird.|  
|TextData|42|9|Enthält die Textdaten, die dem gemeldeten Ereignis zugeordnet sind.|  
|ServerName|43|8|Enthält den Namen der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , für die das gemeldete Ereignis eingetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Fortschrittsberichte – Ereigniskategorie](progress-reports-event-category.md)  
  
  
