---
title: Sys. dm_os_loaded_modules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a899e715db89f00dc318ae15e11ca6ce44e6dae7
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt für jedes in den Serveradressbereich geladene Modul eine Zeile zurück.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_os_loaded_modules**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|Adresse des Moduls im Prozess.|  
|**file_version**|**varchar(23)**|Version der Datei. Hält das folgende Format ein:<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|Version des Produkts. Hält das folgende Format ein:<br /><br /> x.x:x.x|  
|**debug**|**bit**|1 = Modul ist eine Debugversion des geladenen Moduls.|  
|**gepatcht**|**bit**|1 = Modul wurde gepatcht.|  
|**prerelease**|**bit**|1 = Modul ist eine Vorabversion des geladenen Moduls.|  
|**private_build**|**bit**|1 = Modul ist ein privater Build des geladenen Moduls.|  
|**special_build**|**bit**|1 = Modul ist ein spezieller Build des geladenen Moduls.|  
|**Sprache**|**int**|Sprache der Versionsinformationen des Moduls.|  
|**Unternehmensportal**|**nvarchar(256)**|Name des Unternehmens, von dem das Modul erstellt wurde.|  
|**description**|**nvarchar(256)**|Beschreibung des Moduls.|  
|**name**|**nvarchar(255)**|Name des Moduls. Schließt den vollständigen Pfad des Moduls ein.|  
|**pdw_node_id**|**int**|**Gilt für:** [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server-Betriebssystem verbundene dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
