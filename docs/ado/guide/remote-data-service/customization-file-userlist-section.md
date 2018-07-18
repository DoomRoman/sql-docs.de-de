---
title: Anpassung der Datei UserList Abschnitt | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UserList section in rds [ADO]
- customization file in RDS [ADO]
ms.assetid: 42e8ec20-eaac-4a95-8cb8-4bba93a75bcb
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcf8649af2695fa354659f13e891521eb14f39cb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273829"
---
# <a name="customization-file-userlist-section"></a>Anpassung UserList Dateiabschnitt
Die **Userlist** Abschnitt bezieht sich auf die **verbinden** Abschnitt mit dem gleichen *Bezeichner* Parameter.  
  
 Kann in diesem Abschnitt enthalten eine *Benutzereintrag für den Zugriff*, gibt den Zugriff, Rechte für den angegebenen Benutzer und überschreibt die *Standard* *Eintrag zugreifen* in den entsprechenden **verbinden** Abschnitt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in Windows-Betriebssystems enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) detailliertere). RDS-Clientkomponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden sollten migrieren [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
 Ein Benutzer Zugriffseintrag weist das Format:  
  
 *Benutzername* **=**   
 ***accessRights***  
  
|Teil|Description|  
|----------|-----------------|  
|*userName*|Die *Benutzernamen* der Person, die diese Verbindung. Gültige Benutzernamen sind mit IIS hergestellt **Service Manager** Dialogfeld.|  
|***accessRights***|Einer der folgenden Zugriffsrechte:<br /><br /> -   **NoAccess** – Benutzer kann nicht auf die Datenquelle zugreifen.<br />-   **ReadOnly** – der Benutzer kann die Datenquelle lesen.<br />-   **ReadWrite** – Benutzer Lese- oder Schreibzugriff auf die Datenquelle.|  
  
## <a name="see-also"></a>Siehe auch  
 [Connect-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Anpassung Dateiabschnitt-Protokolle](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassung](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderlichen Clienteinstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zu der Anpassungsdatei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


