---
title: Entfernen Sie Aufrufe des veralteten DBCC CONCURRENCYVIOLATION-Befehls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 574b3de41498fa24d2cbd913899d4d071cca6053
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203550"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a>Entfernen von Aufrufen des veralteten DBCC CONCURRENCYVIOLATION-Befehls
  Der Upgrade Advisor hat die Verwendung des Befehls DBCC CONCURRENCYVIOLATION erkannt. Dieser Befehl ist nicht mehr verfügbar. Wenn Sie diesen Befehl ausführen, wird Fehler 2526 zurückgegeben.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Keine aktuelle Version der Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält eine Arbeitsauslastungskontrolle. Deshalb wurde der Befehl entfernt.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Aktualisieren Sie die Anwendungen und Skripts, um Verweise auf diesen veralteten Befehl zu entfernen.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
