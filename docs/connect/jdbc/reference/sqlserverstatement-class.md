---
title: SQLServerStatement-Klasse | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14add0b451947092946129c9388366eb10186dce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32846275"
---
# <a name="sqlserverstatement-class"></a>SQLServerStatement-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt die grundlegende Implementierung der JDBC-Anweisungsfunktion dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Implementiert:** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>Hinweise  
 SQLServerStatement-Klasse bietet auch eine Anzahl von basisklassenimplementierungsmethoden für die JDBC-vorbereitete Anweisung und aufrufbare Anweisungen. Standardmäßig werden von der SQLServerStatement-Klasse wird zum Ausführen von SQL-Anweisungen, und geben Sie updatezählungen und Resultsets an die benutzeranwendung legt.  
  
 Diese Klasse unterstützt das Entpacken in die SQLServerStatement-Klasse, die ISQLServerStatement-Schnittstelle und der java.sql.Statement-Schnittstelle. Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [API-Referenz für JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
