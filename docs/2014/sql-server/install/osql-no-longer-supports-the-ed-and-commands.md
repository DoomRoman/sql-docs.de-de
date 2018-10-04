---
title: osql unterstützt nicht länger 'ED'- und '!!'- Befehle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a94c7dd28353a94da0b595183a75d239fa4c1aa2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112650"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a>osql unterstützt nicht länger 'ED'- und '!!'- Befehle
  Die **Osql** Hilfsprogramm bietet keine Unterstützung der **ED** und **!!** nicht.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie Verweise auf die **ED** und **!!** aus den Skripts.  
  
 Wenn Sie verwenden möchten. die **ED** und **!!** Befehle verwenden die **Sqlcmd** anstelle von Hilfsprogramm **Osql**.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
