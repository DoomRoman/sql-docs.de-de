---
title: Debuggen von Skript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 55e6df8e55d0805f6ac33accc427ed7734d4eb97
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049242"
---
# <a name="debugging-script"></a>Debuggen von Skript
  Sie erstellen die Skripts, die vom Skripttask und der Skriptkomponente verwendet werden, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
 Sie legen Breakpoints in VSTA fest und erstellen sie. Breakpoints können in VSTA sowie im Dialogfeld **Breakpoints festlegen** des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designers verwaltet werden. Weitere Informationen finden Sie unter [Debugging Control Flow](debugging-control-flow.md).  
  
 Das Dialogfeld **Breakpoints festlegen** schließt die Skriptbreakpoints ein. Diese Breakpoints werden am Ende der Breakpointliste angezeigt und enthalten die Zeilennummer und den Namen der Funktion, in der der Breakpoint vorkommt. Skriptbreakpoints können Sie im Dialogfeld **Breakpoints festlegen** löschen.  
  
 Zur Laufzeit werden die Breakpoints, die in Codezeilen im Skript festgelegt sind, in die Breakpoints integriert, die für das Paket oder die Tasks und Container im Paket festgelegt sind. Der Debugger kann ab einem Breakpoint im Skript bis zu einem für das Paket, den Task oder den Container festgelegten Breakpoint ausgeführt werden, oder umgekehrt. Beispielsweise können für ein Paket Breakpoints für die Unterbrechungsbedingungen festgelegt sein, die auftreten, wenn das Paket die Ereignisse **OnPreExecute** und **OnPostExecute** empfängt, und die auch einen Skripttask mit Breakpoints in den Skriptzeilen aufweisen. In diesem Szenario kann die Ausführung vom Paket an der Unterbrechungsbedingung angehalten werden, die dem **OnPreExecute** -Ereignis zugeordnet ist, bis zu den Breakpoints im Skript ausgeführt werden und schließlich bis zur Unterbrechungsbedingung ausgeführt werden, die dem **OnPostExecute** -Ereignis zugeordnet ist.  
  
 Weitere Informationen zum Debuggen des Skripttasks und der Skriptkomponente finden Sie unter [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) und [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a>So legen Sie in Visual Studio für Applikationen einen Breakpoint fest  
  
-   [Debuggen eines Skripts durch Festlegen von Breakpoints in einem Skripttask und einer Skriptkomponente](../extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Tools zur Problembehandlung für die Paketentwicklung](troubleshooting-tools-for-package-development.md)  
  
  