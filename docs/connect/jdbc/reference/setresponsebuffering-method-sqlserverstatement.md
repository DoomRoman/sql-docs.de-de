---
title: SetResponseBuffering-Methode (SQLServerStatement) | Microsoft Docs
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
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 114bba1ad782a3cc14585267407386d30f4ac0b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845795"
---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>setResponseBuffering-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den antwortpuffermodus für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) -Objekt, Groß-/Kleinschreibung **vollständige Zeichenfolge** oder **adaptive**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *value*  
  
 Ein **Zeichenfolge** , die den antwortpuffermodus enthält. Gültige Modi kann eine der folgenden Zeichenfolgen Groß-/Kleinschreibung: **vollständige** oder **adaptive**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 **Adaptive** gibt die Pufferung der Daten wie möglichen bei Bedarf an.  
  
 **vollständige** gibt an, das gesamte Ergebnis vom Server gelesen, zur Laufzeit.  
  
 Adaptive ist der Standardwert in JDBC Driver, Version 2.0 und 3.0. voll belegt war der Standardwert in Versionen vor JDBC Driver, Version 2.0.  
  
 Die [SetResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) Methode können Sie überschreiben die **ResponseBuffering** Verbindung **Zeichenfolge** Eigenschaft für den aktuellen [ SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) Objekt. Weitere Informationen zur Verwendung der antwortpuffermodus finden Sie unter [mithilfe der adaptiven Pufferung](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 Wenn die Anwendung einen Ungültiger Parameterwert, gibt die [SetResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) -Methode, eine [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [Verwenden der adaptiven Pufferung](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  
