---
title: Sys. tcp_endpoints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.tcp_endpoints
- sys.tcp_endpoints_TSQL
- tcp_endpoints
- tcp_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.tcp_endpoints catalog view
ms.assetid: 43cc3afa-cced-4463-8e97-fbfdaf2e4fa8
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1c04be5f76337422601486d08ff41316c7c98192
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "33221291"
---
# <a name="systcpendpoints-transact-sql"></a>sys.tcp_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden TCP-Endpunkt im System. Die durch **sys.tcp_endpoints** beschriebenen Endpunkte stellen ein Objekt für das Erteilen und Widerrufen des Verbindungsprivilegs bereit. Die zu Ports und IP-Adressen angezeigten Informationen werden nicht zum Konfigurieren der Protokolle verwendet und stimmen möglicherweise nicht mit der tatsächlichen Protokollkonfiguration überein. Verwenden Sie zum Anzeigen und Konfigurieren von Protokollen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.  
  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**< geerbte Spalten >**||Erbt Spalten von [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**port**|ssNoversion|Die Nummer des Ports, den der Endpunkt überwacht. Lässt keine NULL-Werte zu.|  
|**is_dynamic_port**|bit|1 = Portnummer wurde dynamisch zugewiesen.<br /><br /> Lässt keine NULL-Werte zu.|  
|**ip_address**|**nvarchar(45)**|Von der LISTENER_IP-Klausel angegebene Überwachungs-IP-Adresse. Lässt NULL-Werte zu.|  
  
## <a name="remarks"></a>Hinweise  
 Führen Sie die folgende Abfrage aus, um Informationen über Endpunkte und Verbindungen zu sammeln. Endpunkte ohne aktuelle oder TCP-Verbindungen werden als NULL-Werte angezeigt. Fügen Sie die **WHERE** -Klausel `WHERE des.session_id = @@SPID` hinzu, um Informationen zur aktuellen Verbindung zurückzugeben.  
  
```  
SELECT des.login_name, des.host_name, program_name,  dec.net_transport, des.login_time,   
e.name AS endpoint_name, e.protocol_desc, e.state_desc, e.is_admin_endpoint,   
t.port, t.is_dynamic_port, dec.local_net_address, dec.local_tcp_port   
FROM sys.endpoints AS e  
LEFT JOIN sys.tcp_endpoints AS t  
   ON e.endpoint_id = t.endpoint_id  
LEFT JOIN sys.dm_exec_sessions AS des  
   ON e.endpoint_id = des.endpoint_id  
LEFT JOIN sys.dm_exec_connections AS dec  
   ON des.session_id = dec.session_id;  
```  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Endpunkte-Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
