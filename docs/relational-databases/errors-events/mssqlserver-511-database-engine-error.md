---
title: MSSQLSERVER_511 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 000c1bc15a0cbdba2c1614d085c9b083b872e917
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver511"></a>MSSQLSERVER_511
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|511|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|ROW_TOOBIG|  
|Meldungstext|Eine Zeile der Größe %d kann nicht erstellt werden, da sie länger als das zulässige Maximum von %d wäre.|  
  
## <a name="explanation"></a>Erklärung  
Der Vorgang hat die maximale Größe für eine Zeile überschritten. Die maximale Größe einer Zeile beträgt normalerweise 8060 Bytes. Einige Speicherformate verfügen über Overhead, mit dem die für Daten verfügbare Zeilengröße reduziert werden kann. Wenn Sie z. B. Sparsespalten verwenden, ist die maximale Größe einer Zeile 8018 Bytes. Bei einigen Vorgängen zum Hinzufügen und Entfernen von Zeilen sowie bei einigen Vorgängen, mit denen der Datentyp einer Spalte geändert wird, muss die Zeile erneut auf die Datenseite geschrieben werden. Danach wird die ursprüngliche Zeile entfernt. Bei diesen Vorgängen liegt die wirksame Grenze für die Größe der Zeile bei der Hälfte der maximalen Grenze. Die Ursache hierfür liegt darin, dass sich sowohl die ursprüngliche Zeile als auch die geänderte Zeile kurzfristig gemeinsam auf der Datenseite befinden müssen.  
  
## <a name="user-action"></a>Benutzeraktion  
Reduzieren Sie, sofern möglich, die Größe der Zeile.  
  
Wenn Sie vermuten, dass das Problem aufgrund eines Updates der Zeile entstanden ist, müssen Sie die Tabelle in mehreren Schritten ändern. Erstellen Sie eine neue Tabelle, und übertragen Sie die Daten in die neue Tabelle. Löschen Sie dann die ursprüngliche Tabelle, und benennen Sie die neue Tabelle um, oder schneiden Sie die ursprüngliche Tabelle ab, ändern Sie die Zeilen in der ursprünglichen Tabelle, und fügen Sie die Daten dann wieder ein.  
  
