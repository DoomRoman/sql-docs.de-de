---
title: MSSQLSERVER_2593 | Microsoft-Dokumentation
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
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 09d12991e0e440f9be3ef8ba37da6decc94aa47d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149678"
---
# <a name="mssqlserver2593"></a>MSSQLSERVER_2593
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2593|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_OBJECT_ROW_PAGE_SUMMARY|  
|Meldungstext|Es sind ROWCOUNT Zeilen auf PAGECOUNT Seiten für das Objekt 'OBJECT' vorhanden.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Meldung ist Teil der Informationsausgabe, die von allen DBCC-Überprüfungen außer von DBCC CHECKALLOC zurückgegeben wird. Sie gibt die Zeilen- und Seitenanzahl für ein bestimmtes Objekt an.  
  
## <a name="user-action"></a>Benutzeraktion  
 InclusionThresholdSetting  
  
  