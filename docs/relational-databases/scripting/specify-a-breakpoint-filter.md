---
title: Angeben eines Breakpointfilters | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.contraints
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 561cf0e02e1cd536784f4bc98531599c374d0524
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708688"
---
# <a name="specify-a-breakpoint-filter"></a>Angeben eines Breakpointfilters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Bei Verwendung eines Breakpointfilters wird ein Breakpoint nur auf angegebene Computer, Betriebssystemprozesse und Threads angewendet. Breakpointfilter werden meist beim Debuggen paralleler Anwendungen verwendet.  
  
##  <a name="BKMK_ActionConsiderations"></a> Filteraspekte  
 Breakpointfilter werden selten mit dem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger verwendet, da es sich bei [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts und gespeicherte Prozeduren nicht um parallele Anwendungen handelt.  
  
#### <a name="to-specify-a-breakpoint-filter"></a>So geben Sie einen Breakpointfilter an  
  
1.  Klicken Sie im Editor-Fenster mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Filter** .  
  
     -oder-  
  
     Klicken Sie im Fenster **Breakpoint** mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Filter** .  
  
2.  Geben Sie im Dialogfeld **Haltepunktfilter** im Feld **Filter** Computer mit Namen oder Betriebssystemprozesse und Threads mit Namen oder ID-Nummer an:  
  
    -   **MachineName** gibt den Computer an, auf dem die Instanz der Datenbank-Engine ausgeführt wird.  
  
    -   **ProcessID**und **ProcessName** geben den Betriebssystemprozess an, von dem die Instanz der Datenbank-Engine ausgeführt wird.  
  
    -   **ThreadID** und **ThreadName** geben den Betriebssystemthread an, unter dem der Batch, die Prozedur oder die Funktion von [!INCLUDE[tsql](../../includes/tsql-md.md)] in der Instanz der Datenbank-Engine ausgeführt wird.  
  
3.  Klicken Sie auf **OK** , um die Änderungen zu implementieren, oder auf **Abbrechen** , um den Vorgang zu beenden, ohne die Änderungen zu übernehmen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Angeben einer Breakpointbedingung](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Angeben einer Trefferanzahl](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Angeben einer Breakpointaktion](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
  
  
