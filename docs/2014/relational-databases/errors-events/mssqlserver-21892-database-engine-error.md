---
title: MSSQLSERVER_21892 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a7504bdce4c01c379f7eb26a02668eada369b2f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060053"
---
# <a name="mssqlserver21892"></a>MSSQLSERVER_21892
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21892|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21892|  
|Meldungstext|„sys.availability_replicas“ kann beim primären Replikat der Verfügbarkeitsgruppe, das dem virtuellen Netzwerknamen '%s' für die Servernamen der Mitgliedsreplikate zugeordnet ist, nicht abgefragt werden: Fehler =%d, Fehlermeldung =% s.'|  
  
## <a name="explanation"></a>Erklärung  
 `sp_validate_replica_hosts_as_publishers` fragt das aktuelle Primäre der Verfügbarkeitsgruppe ab, das dem umgeleiteten Verleger zugeordnet ist, um die Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu bestimmen, welche die Mitgliedsreplikate hosten.  Wenn diese Abfrage fehlschlägt, wird Fehler 21892 zurückgegeben.  
  
 In dem `sp_validate_replica_hosts_as_publishers`Aufruf wird der temporäre Verbindungsserver in der Regel zum ersten Mal verwendet. Wenn Verbindungsprobleme vorliegen, ist es daher wahrscheinlich, dass diese zuerst beim Aufruf von `sp_validate_replica_hosts_as_publishers` augenscheinlich werden. Im Gegensatz zu `sp_validate_redirected_publisher` verwendet der von `sp_validate_replica_hosts_as_publishers` verwendete Verbindungsserver beim Herstellen einer Verbindung mit Replikathost der Verfügbarkeitsgruppen immer die Anmeldeinformationen des Aufrufers.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie beim Ausführen dieser gespeicherten Prozedur sicher, dass Sie eine Anmeldung verwenden, die bei allen Replikaten gültig ist. Die Anmeldung muss dazu autorisiert sein, Verfügbarkeitsgruppenmetadatentabellen abzufragen sowie die Abonnementmetadatentabellen im Verlegerdatenbankreplikat abzufragen.  
  
 Überprüfen Sie ursprünglich angegebene Fehlermeldung, um die Fehlerursache zu bestimmen und entsprechende Korrekturmaßnahmen zu ergreifen.  
  
  