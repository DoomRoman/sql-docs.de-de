---
title: SetCurrentCertificate-Methode (ServerSettings-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetCurrentCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: f9c6e172-11be-42de-b19b-a5b3436e84da
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5b1b6089a04bf4ca8d67134ecad97de2c4a62538
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092800"
---
# <a name="setcurrentcertificate-method-serversettings-class"></a>SetCurrentCertificate-Methode (ServerSettings-Klasse)
  Legt das aktuelle Sicherheitszertifikat fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [ServerSettings-Klasse] Serversettings-class.md) Objekt, das die servereinstellungen in einer Instanz von darstellt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*SHA*|Ein Zeichenfolgenwert, der das aktuelle Sicherheitszertifikat angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32` -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert 1, wenn die Anforderung nicht unterstützt wird, wurde, und jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
