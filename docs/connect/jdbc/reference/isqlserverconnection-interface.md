---
title: ISQLServerConnection-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 031c01e2-2c65-4fe4-9700-fdbcc7a39f30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a7087b01ed04d176faa1d2863813fcb9bcf0de0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759224"
---
# <a name="isqlserverconnection-interface"></a>ISQLServerConnection-Schnittstelle
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine JDBC-Verbindung mit einer [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank dar. Diese Schnittstelle wurde im JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** java.sql.Connection  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public interface ISQLServerConnection  
```  
  
## <a name="remarks"></a>Remarks  
 Diese Schnittstelle wird implementiert von [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Diese Schnittstelle macht das folgende [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifische Feld verfügbar:  
  
|Feld|Weitere Informationen finden Sie unter|  
|-----------|-------------------------------|  
|öffentliches final static int TRANSACTION_SNAPSHOT|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|  
|öffentliche UUID getClientConnectionId()|[getClientConnectionID()](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
