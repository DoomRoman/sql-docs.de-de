---
title: FT:Crawl Started-Ereignisklasse | Microsoft-Dokumentation
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
- Crawl Started event class
ms.assetid: 2535b856-97e8-4fb2-8ba0-5d5446355fa6
caps.latest.revision: 27
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2f70a461848b979400b4538a606edb0595ff1400
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160665"
---
# <a name="ftcrawl-started-event-class"></a>FT:Crawl Started (Ereignisklasse)
  Die Ereignisklasse **FT:Crawl Started** zeigt an, dass ein Volltextdurchforsten (Auffüllung) gestartet wurde. Mit dieser Ereignisklasse können Sie überprüfen, ob eine Durchforstungsanforderung tatsächlich von Arbeitstasks abgerufen wird.  
  
## <a name="ft-crawl-started-event-class-data-columns"></a>FT:Crawl Started-Ereignisklasse (Datenspalten)  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID der Datenbank, in der das Volltextdurchforsten gestartet wurde. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|**EventClass**|**int**|Ereignistyp = 155.|27|nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|ja|  
|**ObjectID**|**int**|Vom System zugewiesene ID des Objekts. Das Volltextdurchforsten wurde für den Volltextindex des Objekts gestartet.|22|ja|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt die Windows-Anmeldenamen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[msCoName](../../includes/msconame-md.md)] an.|64|ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|ja|  
|**TextData**|**ntext**|Auffüllungstyp für Volltextdurchforsten. Als Wert kann Vollständig, Inkrementell, Manuell oder Automatisch angegeben werden.|1|ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
