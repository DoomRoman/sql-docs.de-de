---
title: Verschieben einer FILESTREAM-aktivierten Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9343cbe31b5d77cf9a91a513d61c6aca2d21408a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47693458"
---
# <a name="move-a-filestream-enabled-database"></a>Verschieben einer FILESTREAM-aktivierten Datenbank
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird das Verschieben einer FILESTREAM-aktivierten Datenbank veranschaulicht.  
  
> [!NOTE]  
>  Für die Beispiele in diesem Thema benötigen Sie die Datenbank „Archive“, die unter [Erstellen einer FILESTREAM-aktivierten Datenbank](../../relational-databases/blob/create-a-filestream-enabled-database.md)erstellt wird.  
  
### <a name="to-move-a-filestream-enabled-database"></a>So verschieben Sie eine FILESTREAM-aktivierte Datenbank  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]auf **Neue Abfrage** , um den Abfrage-Editor zu öffnen.  
  
2.  Kopieren Sie das folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript in den Abfrage-Editor, und klicken Sie dann auf **Ausführen**. Mit diesem Skript wird der Speicherort der physischen Datenbankdateien angezeigt, die von der FILESTREAM-Datenbank verwendet werden.  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  Kopieren Sie das folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript in den Abfrage-Editor, und klicken Sie dann auf **Ausführen**. Mit diesem Code wird die `Archive` -Datenbank offline geschaltet.  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  Erstellen Sie den Ordner `C:\moved_location`, und verschieben Sie dann die in Schritt 2 aufgeführten Dateien und Ordner in diesen Ordner.  
  
5.  Kopieren Sie das folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript in den Abfrage-Editor, und klicken Sie dann auf **Ausführen**. Mit diesem Skript wird die `Archive` -Datenbank online geschaltet.  
  
    ```sql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
