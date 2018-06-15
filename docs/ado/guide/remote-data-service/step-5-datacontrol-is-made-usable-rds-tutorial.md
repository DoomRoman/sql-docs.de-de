---
title: 'Schritt 5: Verwendbarmachen (RDS-Lernprogramm) | Microsoft Docs'
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
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd2d73a97e8ba4b3e2c052bb5fa0e08fa7c2d941
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274569"
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Schritt 5: Verwendbarmachen (RDS-Lernprogramm)
Das zurückgegebene **Recordset** Objekt für die Verwendung verfügbar ist. Sie können überprüfen, navigieren oder bearbeiten Sie sie wie jede andere **Recordset**. Was Sie tun können die **Recordset** richtet sich nach Ihrer Umgebung. Visual Basic und Visual C++ besitzen visuelle Steuerelemente, mit denen eine **Recordset** direkt oder indirekt mit Hilfe eines Datensteuerelements aktivieren.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in Windows-Betriebssystems enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) detailliertere). RDS-Clientkomponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden sollten migrieren [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Z. B. Wenn Sie eine Webseite in Microsoft Internet Explorer anzeigen, Sie möchten Anzeigen der **Recordset** -Objektdaten in einem visuellen Steuerelement. Visuelle Steuerelemente auf einer Webseite können nicht zugegriffen werden. eine **Recordset** -Objekts direkt. Allerdings können Zugriff auf die **Recordset** -Objekt über die [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md). Die **RDS. DataControl** verwendet wird, indem Sie ein visuelles steuern, wann die [SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) -Eigenschaftensatz auf die **Recordset** Objekt.  
  
 Das Steuerelementobjekt visual benötigen seine **Typ** Parameter festgelegt wird, um die **RDS. DataControl**, und die zugehörige **DATAFLD** -Eigenschaftensatz auf eine **Recordset** Objekt-Feld (Spalte).  
  
 Legen Sie in diesem Lernprogramm die **SourceRecordset** Eigenschaft:  
  
```  
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schritt 6: Änderungen werden an den Server (RDS-Lernprogramm) gesendet.](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
