---
title: Globale Einstellungen (Dialogfelder) (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 360e01bb-6347-4e2b-acda-0daa161ed33b
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5ce168a2cfe2937195bffe20c39a9a2a4f3fbf3b
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34774816"
---
# <a name="global-settings-dialogs-db2tosql"></a>Globale Einstellungen (Dialogfelder) (DB2ToSQL)
Mithilfe der Dialogfelder Seite der **globale Einstellungen** (Dialogfeld), um die Standardaktion für Benutzer und die Warnung-Einstellungen für SSMA anzugeben.  
  
Die Einstellungen des Dialogfelds für den Zugriff auf die **Tools** klicken Sie im Menü **globale Einstellungen**, klicken Sie auf **GUI** am unteren Rand des linken Bereich, und klicken Sie dann wählen **Dialoge**.  
  
## <a name="options"></a>Tastatur  
**Warnhinweis anzeigen, vor dem Überschreiben von Objekten**  
Wenn SSMA Objekte in SQL Server konvertiert werden, eventuell einige Objekte in SQL Server-Metadaten für das Projekt bereits vorhanden. Diese Objekte möglicherweise bereits konvertiert wurden, oder die Objekte möglicherweise einfach denselben Namen in das Zielschema als Objekte, die Sie konvertieren möchten.  
  
Verwenden Sie diese Option, um anzugeben, ob SSMA Aufforderung zum Überschreiben von doppelten Objektdefinitionen sollten:  
  
-   Bei Auswahl des **"true"**, SSMA wird ein Warnungsdialogfeld angezeigt, wenn ein doppeltes Objekt gefunden wird. In diesem Dialogfeld können Sie einzelne Objekte oder alle doppelten Objekte überschrieben werden sollen, oder überspringen Sie einzelne Objekte oder alle doppelten Objekte angeben.  
  
-   Bei Auswahl des **"false"**, **-Objekt überschreiben Standardaktion** Option wird angezeigt, in dem Sie die Standardaktion anzugeben.  
  
**Standardaktion des Objekts überschreiben**  
Diese Option wird angezeigt, wenn Sie die Option **"false"** für die **warnen vor dem Überschreiben Objekte** Option.  
  
Verwenden Sie diese Option, um anzugeben, das Standardobjekt überschreiben Verhalten:  
  
-   Bei Auswahl des **"true"**, SSMA werden Objekte in den Metadaten der SQL Server-Projekt, die denselben Namen aufweisen und in das gleiche Zielschema das Objekt, das konvertiert werden automatisch überschrieben.  
  
-   Bei Auswahl des **"false"**, SSMA Objektmetadaten während der Konvertierung wird nicht überschrieben werden.  
  
