---
title: MSSQLSERVER_905 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 76429f207f2b233827c77ed983025852a85adf77
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver905"></a>MSSQLSERVER_905
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|905|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBSTARTUP_EE_PARTITIONING|  
|Meldungstext|Die '%.*ls'-Datenbank kann in dieser Edition von SQL Server nicht gestartet werden, weil sie eine '%.\*ls'-Partitionsfunktion enthält. Das Partitionieren wird nur von SQL Server Enterprise Edition unterstützt.|  
  
## <a name="explanation"></a>Erklärung  
Die Datenbank enthält mindestens eine partitionierte Tabelle bzw. mindestens einen partitionierten Index. In dieser Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann keine Partitionierung verwendet werden. Deshalb kann die Datenbank nicht ordnungsgemäß gestartet werden. Partitionierte Tabellen und Indizes sind nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="user-action"></a>Benutzeraktion  
Trennen Sie die Datenbank mithilfe der gespeicherten Prozedur sp_detach_db. Verschieben Sie die Dateien bei Bedarf, und fügen Sie dann die Datenbank an eine Instanz der unterstützen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Edition an. Verwenden Sie dazu CREATE DATABASE mit der FOR ATTACH-Option oder der FOR ATTACH_REBUILD_LOG-Option. Deaktivieren Sie die Partitionierung für alle Tabellen, und entfernen Sie die Partitionierungsfunktionen. Trennen Sie die Datenbank wieder, und fügen Sie sie an den aktuellen Server an.  
  
