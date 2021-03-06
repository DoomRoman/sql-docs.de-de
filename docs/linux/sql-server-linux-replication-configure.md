---
title: Konfigurieren von SQL Server-Replikation unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie Sie SQL Server-Replikation unter Linux konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 58cbcb648d6318b1b013082fc621c48e278f9186
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793578"
---
# <a name="configure-sql-server-replication-on-linux"></a>Konfigurieren von SQL Server-Replikation unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] führt SQL Server-Replikation für Instanzen von SQL Server unter Linux.

Ausführliche Informationen zur Replikation finden Sie unter [Dokumentation zu SQL Server-Replikation](../relational-databases/replication/sql-server-replication.md).

Konfigurieren der Replikation unter Linux mit SQL Server Management Studio (SSMS) oder gespeicherte Transact-SQL-Prozeduren.

* Zur Verwendung von SSMS können befolgen Sie die Anweisungen in diesem Artikel.

  Verwenden Sie SSMS auf einem Windows-Betriebssystem zur Verbindung mit Instanzen von SQL Server. Hintergrundinformationen und Anleitungen finden Sie [SSMS verwenden, um die Verwaltung von SQL Server unter Linux](./sql-server-linux-manage-ssms.md).
  
* Ein Beispiel mit gespeicherten Prozeduren führen Sie die [Konfigurieren von SQL Server-Replikation unter Linux](sql-server-linux-replication-tutorial-tsql.md) Tutorial.

## <a name="prerequisites"></a>Erforderliche Komponenten

Vor dem Konfigurieren von Verlegern, Verteilern und Abonnenten, müssen Sie einige Konfigurationsschritte für die SQL Server-Instanz.

1. Aktivieren Sie SQL Server-Agent für die Replikations-Agents verwenden. Führen Sie auf allen Linux-Servern die folgenden Befehle im Terminal aus.

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
  sudo systemctl restart mssql-server
  ```

1. Konfigurieren Sie SQL Server-Instanz für die Replikation. Führen Sie zum Konfigurieren der SQL Server-Instanz für die Replikation `sys.sp_MSrepl_createdatatypemappings` für alle Instanzen, die bei der Replikation beteiligt.

  ```sql
  USE msdb
  GO
  exec sys.sp_MSrepl_createdatatypemappings;
  GO
  ```

1. Erstellen Sie einen Standardordner für momentaufnahmeordner an. Die SQL Server-Agents erfordern einen Standardordner für momentaufnahmeordner auf Lese-/Schreibzugriff auf. Erstellen Sie den momentaufnahmeordner auf dem Verteiler.

  Erstellen den momentaufnahmeordner und gewähren des Zugriffs auf `mssql` Benutzer, die den folgenden Befehl ausführen:

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

## <a name="configure-and-monitor-replication-with-sql-server-management-studio-ssms"></a>Konfigurieren Sie und überwachen Sie der Replikation mit SQL Server Management Studio (SSMS)

### <a name="configure-the-distributor"></a>Konfigurieren des Verteilers
  
So konfigurieren Sie den Verteiler 

1. In SSMS eine Verbindung mit Ihrer Instanz von SQL Server in Objekt-Explorer herstellen.

1. Mit der rechten Maustaste **Replikation**, und klicken Sie auf **Verteilung konfigurieren...** .

1. Befolgen Sie die Anweisungen auf der **Verteilungskonfigurations-Assistenten**.

### <a name="create-publication-and-articles"></a>Erstellen der Veröffentlichung und die Artikel

So erstellen Sie eine Veröffentlichung und Artikeln:

1. Klicken Sie im Objekt-Explorer auf **Replikation** > **lokale Veröffentlichungen**> **neue Veröffentlichung...** .

1. Führen Sie die Anweisungen auf der **Assistenten für neue Veröffentlichung** so konfigurieren Sie den Typ der Replikation und die Artikel, die zur Veröffentlichung gehören.

### <a name="configure-the-subscription"></a>Konfigurieren Sie das Abonnement

Das Abonnement im Objekt-Explorer, klicken Sie auf **Replikation** > **lokale Abonnements**> **neue Abonnements...** .

### <a name="monitor-replication-jobs"></a>Überwachen von Replikations-Aufträgen

Mithilfe des Replikationsmonitors Replikationsaufträge zu überwachen.

Klicken Sie im Objekt-Explorer mit der Maustaste **Replikation**, und klicken Sie auf **Replikationsmonitor starten**.

## <a name="next-steps"></a>Nächste Schritte

[Konzepte: SQLServer-Replikation unter Linux](sql-server-linux-replication.md)

[Gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).
