---
title: ISQLServerDataSource-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ba1d3242-19ca-4321-83fe-867a4f69f1d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6d0ecf55c23d693b03fc289db5b8c6f3e7dd3d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697387"
---
# <a name="isqlserverdatasource-interface"></a>ISQLServerDataSource-Schnittstelle
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Eine Factory zur Erstellung von Verbindungen zur von diesem Objekt dargestellten Datenquelle. Diese Schnittstelle wurde im JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** java.sql.CommonDataSource  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public interface ISQLServerDataSource  
```  
  
## <a name="remarks"></a>Remarks  
 Diese Schnittstelle wird implementiert von [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
 Diese Schnittstelle macht die folgenden [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifischen Methoden verfügbar:  
  
|Methode|Weitere Informationen finden Sie unter|  
|------------|-------------------------------|  
|öffentliche Zeichenkette getApplicationName()|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getDatabaseName()|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getDescription()|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|  
|öffentlicher boolescher Wert getEncrypt()|[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getFailoverPartner()|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getHostNameInCertificate()|[getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getInstanceName()|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|  
|öffentlicher boolescher Wert getLastUpdateCount()|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|  
|öffentliches int getLockTimeout()|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|  
|öffentlicher boolescher Wert getMultiSubnetFailover()|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|  
|öffentliches int getPacketSize()|[getPacketSize](../../../connect/jdbc/reference/getpacketsize-method-sqlserverdatasource.md)|  
|öffentliches int getPortNumber()|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|  
|öffentliche Zeichenfolge getResponseBuffering()|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getSelectMethod()|[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|  
|öffentlicher boolescher Wert getSendStringParametersAsUnicode()|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|  
|öffentlicher boolescher Wert getSendTimeAsDatetime()|[getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getServerName()|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|  
|öffentlicher boolescher Wert getTrustServerCertificate()|[getTrustServerCertificate](../../../connect/jdbc/reference/gettrustservercertificate-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getTrustStore()|[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getURL()|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getUser()|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|  
|öffentliche Zeichenkette getWorkstationID()|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|  
|öffentlicher boolescher Wert getXopenStates()|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|  
|öffentliches void setApplicationName(String)|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|  
|öffentliches void setAuthenticationSceme(String)|[setAuthenticationSceme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|  
|öffentliches void setDatabaseName(String)|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|  
|öffentliches void setDescription(String)|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|  
|öffentliches void setEncrypt(boolean)|[setEncrypt](../../../connect/jdbc/reference/setencrypt-method-sqlserverdatasource.md)|  
|öffentliches void setFailoverPartner(String)|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|  
|öffentliches void setHostNameInCertificate(String)|[setHostNameInCertificate](../../../connect/jdbc/reference/sethostnameincertificate-method-sqlserverdatasource.md)|  
|öffentliches void setInstanceName(String)|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|  
|öffentliches void setIntegratedSecurity(boolean)|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|  
|öffentliches void setLastUpdateCount(boolean)|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|  
|öffentliches void setLockTimeout(int)|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|  
|öffentliches setMultiSubnetFailover(boolesches multiSubnetFailover)|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|  
|öffentliches void setPacketSize(int)|[setPacketSize](../../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)|  
|öffentliches void setPassword(String)|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|  
|öffentliches void setPortNumber(int)|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|  
|öffentliches void setResponseBuffering(String)|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)|  
|öffentliches void setSelectMethod(String)|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|  
|öffentliches void setSendStringParametersAsUnicode(boolean)|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|  
|öffentliches void setSendTimeAsDatetime(boolean)|[setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)|  
|öffentliches void setServerName(String)|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|  
|öffentliches void setTrustServerCertificate(boolean)|[setTrustServerCertificate](../../../connect/jdbc/reference/settrustservercertificate-method-sqlserverdatasource.md)|  
|öffentliches void setTrustStore(String)|[setTrustStore](../../../connect/jdbc/reference/settruststore-method-sqlserverdatasource.md)|  
|öffentliches void setTrustStorePassword(String)|[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)|  
|öffentliches void setURL(String url)|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|  
|öffentliches void setUser(String)|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|  
|öffentliches void setWorkstationID(String)|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|  
|öffentliches void setXopenStates(boolean)|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
