---
title: Aktivieren eine DLL für die Ausführung auf DCOM | Microsoft Docs
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
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbd4e91f48c623c9afe769bb99913e1ed07918f3
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273959"
---
# <a name="enabling-a-dll-to-run-on-dcom"></a>Aktivieren einer DLL zur Ausführung auf DCOM
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in Windows-Betriebssystems enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) detailliertere). RDS-Clientkomponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden sollten migrieren [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Die folgenden Schritte beschreiben, wie eine Business Objekt DLL-Datei zu DCOM- und Microsoft Internet Informationen Services (HTTP) über Komponentendienste verwenden aktiviert wird.  
  
1.  Erstellen Sie ein neues, leeres Paket in das Komponentendienste-MMC-Snap-in.  
  
     Verwenden Sie das Komponentendienste-MMC-Snap-in zum Erstellen eines Pakets und die DLL in diesem Paket hinzufügen. Dadurch wird die DLL über DCOM verfügbar, sondern den Zugriff über IIS entfernt. (Wenn Sie in der Registrierung für die DLL-Datei, überprüfen Sie die **Inproc** Schlüssel jetzt leer ist; das Festlegen der Activation-Attributs, erläutert weiter unten in diesem Thema Fügt einen Wert in der **Inproc** Schlüssel.)  
  
2.  Installieren Sie das Paket ein Geschäftsobjekt.  
  
     -oder-  
  
     Importieren der [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt in das Paket.  
  
3.  Legen Sie das Attribut "Aktivierung" für das Paket, **im Prozess des Erstellers** (bibliotheksanwendung).  
  
     Um die DLL-Datei über DCOM und IIS auf demselben Computer zugänglich zu machen, müssen Sie die Komponente Aktivierungsattribut in das Komponentendienste-MMC-Snap-in festgelegt. Nachdem Sie das Attribut, um festlegen **im Prozess des Erstellers**, werden Sie feststellen, dass ein **Inproc** Serverschlüssel in der Registrierung wurde hinzugefügt, verweist auf eine Komponentendienste DLL Ersatzzeichen enthalten.  
  
 Weitere Informationen zu den Komponentendiensten (oder Microsoft Transaction-Dienst, bei Verwendung von Windows NT) und wie Sie diese Schritte ausführen, finden Sie auf der Website von Microsoft Transaction Server.


