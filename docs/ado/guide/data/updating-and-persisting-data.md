---
title: Aktualisieren und Beibehalten von Daten | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data [ADO]
- data updates [ADO]
- ADO, updating data
ms.assetid: 8dc27274-4f96-43d1-913c-4ff7d01b9a27
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2c4d7fd046631814e263c8bd6a413fb9ef2f00c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273159"
---
# <a name="updating-and-persisting-data"></a>Aktualisieren und Beibehalten von Daten
Die vorhergehenden Kapitel wurde erläutert, wie ADO verwenden, um Daten in einer Datenquelle abzurufen, wie in den Daten navigieren und auch zum Bearbeiten der Daten. Wenn das Ziel der Anwendung besteht darin, Benutzern, um die Daten zu ändern, müssen Sie natürlich zu verstehen, wie die Änderungen zu speichern. Sie können entweder beibehalten der **Recordset** ändert sich in einer Datei mit der **speichern** -Methode, oder Sie können die Änderungen werden wieder an die Datenquelle für die Verwendung von Storage senden die **Update** oder  **UpdateBatch** Methoden.  
  
 In den vorangegangenen Kapiteln geändert Sie die Daten in mehreren Zeilen von der **Recordset**. ADO unterstützt zwei grundlegende Konzepte im Zusammenhang mit der hinzufügen, löschen und Ändern von Zeilen mit Daten.  
  
 Die erste Idee ist, dass die Änderungen werden nicht sofort an die **Recordset**; stattdessen sie vorgenommen wurden, eine interne *Kopierpuffer*. Wenn Sie sich, dass Sie nicht möchten, dass die Änderungen entscheiden, werden die Änderungen in den Kopierpuffer verworfen. Wenn Sie die Änderungen beibehalten möchten, die in den Kopierpuffer vorgenommenen Änderungen werden auf die **Recordset**.  
  
 Der zweiten Begriff ist, dass die Änderungen entweder an die Datenquelle weitergegeben werden, sobald Sie die Arbeit in einer Zeile abgeschlossen deklarieren (d. h. *sofortige* Modus), oder alle Änderungen an einer Reihe von Zeilen werden gesammelt, bis Sie die Arbeit für den Satz deklarieren abgeschlossen (d. h. *Batch* Modus). Die **LockType** Eigenschaft bestimmt, wenn die Änderungen an der zugrunde liegenden Datenquelle vorgenommen werden. **AdLockOptimistic** oder **AdLockPessimistic** unmittelbaren Modus gibt während **AdLockBatchOptimistic** Batchmodus angibt. Die **CursorLocation** -Eigenschaft kann die Auswirkungen **LockType** Einstellungen stehen zur Verfügung. Für die Instanz, die **AdLockPessimistic** Einstellung wird nicht unterstützt, wenn die **CursorLocation** -Eigenschaftensatz auf **AdUseClient**.  
  
 In unmittelbarer Modus, jeden Aufruf des der **Update** Methode gibt die Änderungen an die Datenquelle weiter. Im Batchmodus ausgeführt, jeden Aufruf des **Update** oder Verschiebung von der aktuellen Zeilenposition speichert die Änderungen in den Kopierpuffer, jedoch nur die **UpdateBatch** Methode gibt die Änderungen an die Datenquelle weiter.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Aktualisieren von Daten](../../../ado/guide/data/updating-data.md)  
  
-   [Beibehalten von Daten](../../../ado/guide/data/persisting-data.md)
