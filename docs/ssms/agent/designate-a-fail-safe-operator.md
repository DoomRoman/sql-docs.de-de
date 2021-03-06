---
title: Bestimmen eines Ausfallsicherheitsoperators | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 12958d837ad000fec77e6d5c4a0f167ef2bdd7ec
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "42776287"
---
# <a name="designate-a-fail-safe-operator"></a>Bestimmen eines Ausfallsicherheitsoperators
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Ein Ausfallsicherheitsoperator ist ein Benutzer, der die Warnungen empfängt, wenn der vorgesehene Operator nicht erreichbar ist. In diesem Thema wird beschrieben, wie Sie einen Ausfallsicherheitsoperator zum Empfang von [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnbenachrichtigungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]festlegen.  
  
**In diesem Thema**  
  
-   **Vorbereitungen:**  
  
    [Einschränkungen](#Restrictions)  
  
    [Security](#Security)  
  
-   **So bestimmen Sie einen Ausfallsicherheitsoperator mit**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Vorbereitungen  
  
### <a name="Restrictions"></a>Einschränkungen  
  
-   Die Pager- und **net send** -Optionen werden in zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht mehr im [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktionen zurzeit verwenden.  
  
-   Beachten Sie, dass E-Mail- und Pagerbenachrichtigungen an Operatoren nur versendet werden können, wenn der SQL Server-Agent für die Verwendung von Datenbank-E-Mail konfiguriert ist. Weitere Informationen finden Sie unter [Zuweisen von Warnungen zu einem Operator](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Aufträge problemlos mithilfe einer grafischen Oberfläche verwaltet werden. Dies ist die empfohlene Vorgehensweise für die Erstellung und Verwaltung der Auftragsinfrastruktur.  
  
### <a name="Security"></a>Sicherheit  
  
#### <a name="Permissions"></a>Berechtigungen  
Nur Mitglieder der festen Serverrolle **sysadmin** können Ausfallsicherheitsoperatoren bestimmen.  
  
## <a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-designate-a-fail-safe-operator"></a>So bestimmen Sie einen Ausfallsicherheitsoperator  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, der den SQL Server-Agent-Operator enthält, den Sie als ausfallsicher bestimmen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent** , und wählen Sie **Eigenschaften**aus.  
  
3.  Klicken Sie im Dialogfeld **Eigenschaften des SQL Server-Agents >***Servername* unter **Seite auswählen** auf **Warnungssystem**.  
  
4.  Aktivieren Sie unter **Ausfallsicherheitsoperator**die Option **Ausfallsicherheitsoperator aktivieren**.  
  
5.  Wählen Sie in der Liste **Operator** den Operator aus, den Sie als ausfallsicher bestimmen möchten.  
  
6.  Aktivieren Sie entweder eines oder alle der folgenden Kontrollkästchen – **E-Mail**, **Pager**oder **NET SEND**–, um zu bestimmen, wie der Operator benachrichtigt wird.  
  
7.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
