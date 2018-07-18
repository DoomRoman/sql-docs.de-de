---
title: SetPacketSize-Methode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08f4f72aae10fc154b7362a83e870d85b9fb42e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844605"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>setPacketSize-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt die aktuelle Netzwerkpaketgröße verwendet, um die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], angegeben in Bytes.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Parameter  
 *packetSize*  
  
 Ein **Int** Wert, der die Netzwerkpaketgröße enthält.  
  
## <a name="remarks"></a>Hinweise  
 Der akzeptable Wertebereich dieser Eigenschaft lautet "[-1 | 0 | 512..32767]". Wenn diese Eigenschaft auf einen Wert außerhalb des zulässigen Bereichs festgelegt wird, wird eine Ausnahme ausgelöst.  
  
 Von der Anwendung wird unter Umständen versucht, die packetSize-Eigenschaft beim Herstellen einer Verbindung mit SSL (Secure Sockets Layer)-Verschlüsselung festzulegen. Die [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] die Paketgröße mit dem Server ausgehandelt. Wenn die Encrypt-Eigenschaft, um festgelegt wird "**" true "**" und die ausgehandelte Paketgröße ist größer als der Java Virtual Machine (JVM) Standardsicherheitsanbieters SSL-Datensatzgröße ist, wird der Treiber löst einen Fehler aus und trennt die Verbindung.  
  
 Darüber hinaus wird von der Anwendung unter Umständen versucht, die packetSize-Eigenschaft ohne Anforderung der SSL-Verschlüsselung festzulegen. In diesem Fall gilt Folgendes: Wird vom Server vorausgesetzt, dass der Clientcomputer die SSL-Verschlüsselung unterstützt, wird vom Treiber die SSL-Datensatzgröße des Standardsicherheitsanbieters der JVM überprüft. Übersteigt die packetSize-Eigenschaft die Datensatzgröße des Standardsicherheitsanbieters der Java Virtual Machine (JVM), wird vom Treiber ein Fehler ausgelöst, und die Verbindung wird getrennt.  
  
 Weitere Informationen zur Verwendung von SSL finden Sie unter [mithilfe von SSL-Verschlüsselung](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
