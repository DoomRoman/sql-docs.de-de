---
title: SetObject-Methode (java.lang.String, java.lang.Object) | Microsoft Docs
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
- SQLServerCallableStatement.setObject (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 14b84409-5510-4642-a83b-732d8511c5b1
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0867f75477cd4a66645fc34db9164c6c6e2d9e8c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845735"
---
# <a name="setobject-method-javalangstring-javalangobject"></a>setObject-Methode (java.lang.String, java.lang.Object)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Wert des angegebenen Parameters unter Verwendung des angegebenen Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setObject(java.lang.String sCol,  
                      java.lang.Object o)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **Zeichenfolge** , die den Namen des Parameters enthält.  
  
 *o*  
  
 Ein **Objekt** Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese SetObject-Methode wird von der SetObject-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Von dieser Methode wird der spezifische Parameter vor dem Senden an die Datenbank in einen CHAR-Wert konvertiert, wenn ein NULL-Wert vorhanden ist. Ist der Parameter ein binary-, varbinary- oder image SQL-Typ, wird beim Ausführen der Anweisung eine Ausnahme ausgelöst.  
  
 Beginnend mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0, das Verhalten dieser Methode geändert wird, indem die **SendTimeAsDatetime** Connection-Eigenschaft ([Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md)) und [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Weitere Informationen finden Sie unter [konfigurieren wie java.sql.Time-Werte werden an den Server gesendet](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SetObject-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
