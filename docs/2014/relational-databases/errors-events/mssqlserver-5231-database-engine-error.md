---
title: MSSQLSERVER_5231 | Microsoft-Dokumentation
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
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 100e7bd0b818ae4aed757845a769cf413c5ae7a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150375"
---
# <a name="mssqlserver5231"></a>MSSQLSERVER_5231
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|5231|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Meldungstext|Objekt-ID O_ID (Objekt 'NAME'): Deadlock beim Versuch, dieses Objekt für die Überprüfung zu sperren. Das Objekt wurde ausgelassen und wird nicht verarbeitet.|  
  
## <a name="explanation"></a>Erklärung  
 Es kam zu einem Deadlock, als von DBCC versucht wurde, das Objekt zu sperren. DBCC wurde als Deadlockopfer ausgewählt. Das Objekt wird nicht verarbeitet.  
  
## <a name="user-action"></a>Benutzeraktion  
 InclusionThresholdSetting  
  
  