---
title: 'SetServiceState-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 79b79cd7b7e179413cbf5338a98ffa832f6a6b6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600368"
---
# <a name="configurationsetting-method---setservicestate"></a>ConfigurationSetting-Methode: SetServiceState
  Aktiviert und deaktiviert den Berichtsserver-Windows-Dienst und den Berichtsserver-Webdienst.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetServiceState(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *EnableWindowsService*  
 Ein **Boolean** -Wert, der den Status des Windows-Diensts angibt. Bei dem Wert **true** wird der Windows-Dienst des Berichtsservers gestartet. Bei dem Wert **false** wird der Windows-Dienst beendet.  
  
 *EnableWebService*  
 Ein **Boolean** -Wert, der den Status des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Webdiensts angibt. Bei dem Wert **true** wird der Webdienst des Berichtsservers gestartet. Bei dem Wert **false** wird der Webdienst beendet.  
  
 *EnableReportManager*  
 Ein **Boolean** -Wert, der den gewünschten Status des Berichts-Managers angibt.
 
 > [!NOTE] 
 > Diese Einstellung wurde ab dem Kumulativen Update 2 von SQL Server 2016 Reporting Services als veraltet gekennzeichnet. Das Webportal bleibt weiterhin aktiviert. Der Wert wird ignoriert.
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
