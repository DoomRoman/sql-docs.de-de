---
title: 'Schritt 4: Server gibt das Recordset (RDS-Lernprogramm) | Microsoft Docs'
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
- RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dec3b614f0401160df1310d80265d4a10798eb08
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274489"
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>Schritt 4: Server gibt das Recordset (RDS-Lernprogramm)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in Windows-Betriebssystems enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) detailliertere). RDS-Clientkomponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden sollten migrieren [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS konvertiert der abgerufene **Recordset** Objekt, das ein Formular, das an den Client gesendet werden kann (d. h. es *marshallt* der **Recordset**). Die genaue Form der konvertieren und wie sie gesendet wird, hängt davon ab, ob der Server im Internet oder Intranet, ein lokales Netzwerk, oder ist eine Dynamic Link Library. Dieses Detail ist jedoch nicht von Bedeutung; entscheidend ist, dass RDS sendet die **Recordset** an den Client zurück.  
  
 Auf der Clientseite eine **Recordset** -Objekt zurückgegeben und einer lokalen Variablen zugewiesen ist.  
  
```  
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schritt 5: Verwendbarmachen (RDS-Lernprogramm)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
