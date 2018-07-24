---
title: 'Lektion 3: Datenbanksicherung über URLs | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: aa6da6086cd5c1a0ebfd56394e5c79b2078ef82e
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978932"
---
# <a name="lesson-3-database-backup-to-url"></a>Lektion 3: Datenbanksicherung über URLs
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In dieser Lektion werden Sie die AdventureWorks2014-Datenbank in Ihrer lokalen SQL Server 2016-Instanz in dem Azure-Container sichern, den Sie in [Lektion 1: Erstellen einer Richtlinie und einer Shared Access Signature (SAS) in einem Azure-Container](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)erstellt haben.  
  
> [!NOTE]  
> Wenn Sie eine SQL Server 2012 SP1 CU2 oder höher Datenbank oder eine SQL Server 2014-Datenbank in diesem Azure-Container sichern möchten, können Sie die [hier](https://technet.microsoft.com/library/dn435916(v=sql.120).aspx) dokumentierte veraltete Syntax verwenden, um die URL mit der WITH CREDENTIAL-Syntax zu sichern.  
  
So sichern Sie eine Datenbank in Blob Storage:  
  
1.  Stellen Sie eine Verbindung mit SQL Server Management Studio her.  
  
2.  Öffnen Sie ein neues Abfragefenster und stellen Sie eine Verbindung mit der SQL Server 2016-Instanz der Datenbank-Engine auf Ihrem virtuellen Azure-Computer her.  
  
3.  Kopieren Sie das folgende Transact-SQL-Skript in das Abfragefenster. Ändern Sie die URL gemäß Ihres Speicherkontonamens und des Containers, den Sie in Lektion 1 angegeben haben, und führen Sie dieses Skript anschließend aus.  
  
    ```  
  
    -- To permit log backups, before the full database backup, modify the database to use the full recovery model.  
    USE master;  
    ALTER DATABASE AdventureWorks2014  
       SET RECOVERY FULL;  
  
    -- Back up the full AdventureWorks2014 database to the container that you created in Lesson 1  
    BACKUP DATABASE AdventureWorks2014   
       TO URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_onprem.bak'  
  
    ```  
  
4.  Öffnen Sie den Objekt-Explorer öffnen und stellen Sie eine Verbindung mit dem Azure-Speicher mit Ihrem Speicherkonto und Schlüssel her.  
  
5.  Erweitern Sie die Container, erweitern Sie den Container, den Sie in Lektion 1 erstellt haben und überprüfen Sie, ob die Sicherung aus Schritt 3 oben in diesem Container angezeigt wird.  
  
    ![Lokale Sicherungsdatei erscheint als Blob in Azure-Container](../relational-databases/media/0d060e51-012f-4c61-ab8d-16d461d0ffad.JPG "On-premises backup file appears as blob in Azure container")  
  
**Nächste Lektion:**  
  
[Lektion 4: Wiederherstellen einer Datenbank auf einem virtuellen Computer über URLs](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
