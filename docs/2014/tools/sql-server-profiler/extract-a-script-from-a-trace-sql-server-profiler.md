---
title: Extrahieren eines Skripts aus einer Ablaufverfolgung (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 035df37fccf2507195e6576e062b7ce254dd1dba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050432"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>Extrahieren eines Skripts aus einer Ablaufverfolgung (SQL Server Profiler)
  In diesem Thema wird das Extrahieren von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ereignissen aus einer Ablaufverfolgungsdatei oder -tabelle sowie das Speichern in einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]beschrieben.  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>So extrahieren Sie ein Transact-SQL-Skript aus einer Ablaufverfolgungsdatei oder -tabelle  
  
1.  Öffnen Sie eine Ablaufverfolgungsdatei oder -tabelle, die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Ereignisse enthält, die Sie in einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skriptdatei speichern möchten. Weitere Informationen finden Sie unter [Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) oder unter [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).  
  
2.  Zeigen Sie im Menü **Datei** auf **Exportieren**, zeigen Sie auf **SQL Server-Ereignisse extrahieren**, und klicken Sie dann auf **Transact-SQL-Ereignisse extrahieren**.  
  
3.  Geben Sie im Dialogfeld **Speichern unter** einen Namen für die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Datei ein, und klicken Sie dann auf **Speichern**.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  