---
title: Anzeigen oder Ändern der Standardspeicherorte für Daten- und Protokolldateien (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d93161cb6601fbd0be7de5c6ab12dfeb58fa2060
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>Anzeigen oder Ändern der Standardspeicherorte für Datenbankdateien
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
 Als bewährte Methode zum Schutz der Datendateien und Protokolldateien sollten Sie sicherstellen, dass diese durch Zugriffssteuerungslisten (ACLs) geschützt sind. Einrichten der ACLs für den Verzeichnisstamm, unter dem die Dateien erstellt werden.  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>Anzeigen oder Ändern der Standardspeicherorte für Datenbankdateien  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf Ihren Server, und klicken Sie auf **Eigenschaften**.  
  
2.  Klicken Sie im linken Bedienfeld auf der betreffenden Eigenschaftenseite auf die Registerkarte **Datenbankeinstellungen** .  
  
3.  Im Bereich **Standardspeicherorte für Datenbank**können Sie die aktuellen Standardspeicherorte für neue Datendateien und neue Protokolldateien anzeigen. Um einen Standardspeicherort zu ändern, geben Sie einen neuen Standardpfadnamen in das Feld **Daten** oder **Protokoll** ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen, um einen Pfadnamen zu suchen und auszuwählen.  
  
>**HINWEIS:** Nach dem Ändern der Standardspeicherorte müssen Sie den SQL Server-Dienst beenden und wieder starten, um die Änderung abzuschließen.  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Erstellen einer Datenbank](../../relational-databases/databases/create-a-database.md)  
  
  
