---
title: MSSQLSERVER_7916 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fa235c72a0b0333a64b35f481c516de14a5b0eef
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410499"
---
# <a name="mssqlserver7916"></a>MSSQLSERVER_7916
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7916|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_RECORD_DELETED|  
|Meldungstext|Reparaturvorgang: Der Datensatz für Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (TYPE-Typ) auf der Seite P_ID, Slot S_ID wurde gelöscht. Die Indizes werden neu erstellt.|  
  
## <a name="explanation"></a>Erklärung  
 Dies ist eine Informationsmeldung von REPAIR, die angibt, dass der angegebene Datensatz aus der Seite gelöscht wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
 InclusionThresholdSetting  
  
  
