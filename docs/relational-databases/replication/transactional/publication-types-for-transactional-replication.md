---
title: Veröffentlichungstypen der Transaktionsreplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e17764a7a2d47ccbf9d2f35575818eb2efdf8dce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47749358"
---
# <a name="publication-types-for-transactional-replication"></a>Veröffentlichungstypen der Transaktionsreplikation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Transaktionsreplikation stellt drei Veröffentlichungstypen bereit:  
  
|Veröffentlichungstyp|und Beschreibung|  
|----------------------|-----------------|  
|Standardmäßige Transaktionsveröffentlichung|Geeignet für Topologien, in denen alle Daten auf dem Abonnenten schreibgeschützt sind (von der Transaktionsreplikation wird dies auf dem Abonnenten nicht erzwungen).<br /><br /> Diese Transaktionsveröffentlichungen werden standardmäßig bei der Verwendung von Transact-SQL oder Replikationsverwaltungsobjekten (RMO) erstellt. Im Assistenten für neue Veröffentlichung werden sie erstellt, wenn auf der Seite **Veröffentlichungstyp** die Option **Transaktionsveröffentlichung** ausgewählt wird.<br /><br /> Weitere Informationen zum Erstellen von Veröffentlichungen finden Sie unter [Veröffentlichen von Daten und Datenbankobjekten](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).|  
|Transaktionsveröffentlichung in einer Peer-zu-Peer-Topologie|Dieser Veröffentlichungstyp weist die folgenden Merkmale auf:<br /><br /> – Jeder Server verfügt über identische Daten und fungiert gleichzeitig als Verleger und Abonnent.<br /><br /> – Dieselbe Zeile kann nur jeweils an einer Stelle geändert werden.<br /><br /> – Diese Topologie eignet sich für Serverumgebungen am besten, die Hochverfügbarkeit und Leseskalierbarkeit erfordern.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Transaktionsreplikation](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  
