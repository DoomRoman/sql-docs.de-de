---
title: WMI-Anbieter für Serverereignisse Klassen und Eigenschaften | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ddfa4b5a540ad48f18bc4713ad68eeb2335ff1d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161977"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>Klassen und Eigenschaften für den WMI-Anbieter für Serverereignisse
  Die folgenden Serverereignisse bilden das Programmiermodell für den WMI-Anbieter für Serverereignisse. Es gibt zwei Hauptkategorien von Ereignissen, die durch Absetzen von WQL-Abfragen an den Anbieter abgefragt werden können: DDL-Ereignisse (Data Definition Language) und Ablaufverfolgungsereignisse. Auch die Service Broker-Ereignisse QUEUE_ACTIVATION und BROKER_QUEUE_DISABLED können abgefragt werden. Beachten Sie den inklusiven Charakter der folgenden Strukturdiagramme. Das DDL_ASSEMBLY_EVENTS-Ereignis schließt z. B. beliebige Ereignisse vom Typ ALTER_ASSEMBLY, CREATE_ASSEMBLY und DROP_ASSEMBLY ein. Analog dazu schließt das TRC_FULL_TEXT-Ereignis beliebige Ereignisse vom Typ FT_CRAWL_ABORTED, FT_CRAWL_STARTED und FT_CRAWL_STOPPED ein. ALL_EVENTS deckt alle DDL-Ereignisse, Ablaufverfolgungsereignisse, QUEUE_ACTIVATION und BROKER_QUEUE_DISABLED ab.  
  
 Um zu ermitteln, welche Eigenschaften aus einem Ereignis oder einer Ereignisgruppe abgefragt werden können, konsultieren Sie das Ereignisschema. Standardmäßig wird das Ereignisschema im folgenden Verzeichnis installiert: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] Tools\Binn\schemas\sqlserver\2006\11\events\events .xsd.  
  
 Sie können alternativ finden Sie in auf veröffentlichte Ereignisschema [ http://schemas.microsoft.com/sqlserver ](http://go.microsoft.com/fwlink/?linkid=43100).  
  
 Zum ALTER_DATABASE-Ereignis erfahren Sie beispielsweise, dass DDL_SERVER_LEVEL_EVENTS das übergeordnete Ereignis ist und seine Eigenschaften `TSQLCommand` und `DatabaseName` sind. Das Ereignis erbt auch die Eigenschaften `SQLInstance`, `PostTime`, `ComputerName`, `SPID` und `LoginName`. Das Ereignis verfügt über keinen untergeordneten Ereignisse.  
  
> [!NOTE]  
>  Gespeicherte Systemprozeduren, die DDL-ähnliche Vorgänge ausführen, können auch Ereignisbenachrichtigungen auslösen. Testen Sie die Ereignisbenachrichtigungen, um ihre Reaktion auf gespeicherte Systemprozeduren, die ausgeführt werden, zu bestimmen. Beispielsweise die CREATE TYPE-Anweisung und **Sp_addtype** gespeicherten Prozedur werden beide auslösen eine ereignisbenachrichtigung, die für ein CREATE_TYPE-Ereignis erstellt wird. Weitere Informationen finden Sie unter[DDL-Ereignisse](../../relational-databases/triggers/ddl-events.md).  
  
 **Data Definition Language-Ereignisse und Ereignisgruppen**  
  
 ![WMI-Anbieter für Serverereignisse-Ereignisstruktur](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "WMI-Anbieter für Serverereignisse-Ereignisstruktur")  
  
 **Ablaufverfolgungsereignisse und Ereignisgruppen**  
  
 ![Verfolgen Sie Ereignisse und Ereignisgruppen](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "Ablaufverfolgungsinformationen Ereignisse und Ereignisgruppen")  
  
## <a name="see-also"></a>Siehe auch  
 [WMI-Anbieter für Server-Ereignisse-Konzepte](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  