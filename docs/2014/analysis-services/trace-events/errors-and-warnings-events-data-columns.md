---
title: Fehler und Warnungsereignisse – Datenspalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
ms.assetid: f375d303-7aab-4c51-a955-05a2762cc4d1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2352a70f3acdff7f938307efa817b22b15711abd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214671"
---
# <a name="errors-and-warnings-events-data-columns"></a>Fehler- und Warnungsereignis-Datenspalten
  Die Ereigniskategorie Sicherheitsüberwachung enthält die folgenden Ereignisklassen:  
  
-   Fehlerklasse  
  
 In der folgenden Tabelle sind die Datenspalten für diese Ereignisklasse aufgeführt.  
  
## <a name="error-event-classdata-columns"></a>Fehler-Ereignisklasse – Datenspalten  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|StartTime|3|5|Enthält den Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|SessionType|8|8|Enthält den Typ der Entität, die den Fehler verursachte.|  
|Schweregrad|22|1|Enthält den Schweregrad einer Ausnahme, die dem Fehlerereignis zugeordnet ist. Die Werte sind:<br /><br /> 0 = Erfolg<br /><br /> 1 = Information<br /><br /> 2 = Warnung<br /><br /> 3 = Fehler|  
|Success|23|1|Enthält die Angabe zum Erfolg oder Fehlschlagen des Fehlerereignisses. Die Werte sind:<br /><br /> 0 = Fehler<br /><br /> 1 = Erfolg|  
|Fehler|24|1|Enthält die Fehlernummer eines Fehlers, der ggf. dem Fehlerereignis zugeordnet ist.|  
|ConnectionID|25|1|Enthält die eindeutige Verbindungs-ID, die dem Fehlerereignis zugeordnet ist.|  
|DatabaseName|28|8|Enthält den Namen der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , für die das Fehlerereignis aufgetreten ist.|  
|NTUserName|32|8|Enthält den Windows-Benutzernamen, der dem Fehlerereignis zugeordnet ist.|  
|NTDomainName|33|8|Enthält das Windows-Domänenkonto, das dem Anmeldeereignis zugeordnet ist.|  
|ClientHostName|35|8|Enthält den Namen des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird.|  
|ClientProcessID|36|1|Enthält die Prozess-ID der Clientanwendung.|  
|ApplicationName|37|8|Enthält den Namen der Clientanwendung, die die Verbindung mit dem Server hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|  
|SessionID|39|8|Enthält die Serverprozess-ID (SPID), die die dem Fehlerereignis zugeordnete Benutzersitzung eindeutig identifiziert. Die SPID entspricht direkt der Sitzungs-GUID, die von XMLA (XML for Analysis) verwendet wird.|  
|SPID|41|1|Enthält die Serverprozess-ID (SPID), die die dem Fehlerereignis zugeordnete Benutzersitzung eindeutig identifiziert. Die SPID entspricht direkt der Sitzungs-GUID, die von XMLA (XML for Analysis) verwendet wird.|  
|TextData|42|9|Enthält die Textdaten, die dem Fehlerereignis zugeordnet sind.|  
|ServerName|43|8|Enthält den Namen des Servers, auf dem die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ausgeführt wird, auf der das Fehlerereignis aufgetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberwachung-Ereigniskategorie](security-audit-event-category.md)  
  
  
