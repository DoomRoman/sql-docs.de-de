---
title: 'DatabaseLogonType-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- DatabaseLogonType
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
caps.latest.revision: 24
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2b8886f70f7422052467990135783c48b198ead2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33031067"
---
# <a name="configurationsetting-property---databaselogontype"></a>ConfigurationSetting-Eigenschaft: DatabaseLogonType
  Gibt an, ob der Berichtsserver für den Zugriff auf die Berichtsserver-Datenbank ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Dienstkonto, ein Windows-Benutzerkonto oder eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung verwendet. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Eigenschaftswerte  
 Ein **integer** -Objekt, das den Anmeldetyp darstellt  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Remarks  
 Die Werte sind:  
  
-   0 für Windows-Anmeldung  
  
-   1 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung  
  
-   2 für Anmeldung als Dienst  
  
 Wenn 0 (Windows) angegeben wird, muss der Wert in der [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) -Eigenschaft auf ein entsprechendes gültiges Windows-Benutzerkonto festgelegt werden.  
  
 Wenn Sie 1 (SQL Server) angeben, muss der Wert von [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) einer gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung entsprechen.  
  
 Wenn 2 (Windows-Dienst) angegeben wird, verwendet der Berichtsserver ein [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] -Konto und das Windows-Dienstkonto für den Zugriff auf die Berichtsserver-Datenbank. Die DatabaseLogonAccount-Eigenschaft wird ignoriert.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
