---
title: Erstellen Sie eine Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], snapshots
- snapshots [SQL Server replication], parameterized filters and
- filters [SQL Server replication], parameterized
ms.assetid: 00dfb229-f1de-4d33-90b0-d7c99ab52dcb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 10e8c84af197c600c9b89f850ab84fc27fd56e2d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217740"
---
# <a name="create-a-snapshot-for-a-merge-publication-with-parameterized-filters"></a>Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern
  In diesem Thema wird beschrieben, wie eine Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) erstellt wird.  
  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Zur Erstellung einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern müssen Sie zunächst eine Standardmomentaufnahme (Schemamomentaufnahme) erstellen, die alle veröffentlichten Daten und die Abonnentenmetadaten für das Abonnement enthält. Weitere Informationen finden Sie unter [Erstellen und Anwenden der Anfangsmomentaufnahme](create-and-apply-the-initial-snapshot.md). Nachdem Sie die Schemamomentaufnahme erstellt haben, können Sie den Teil der Momentaufnahme generieren, der die abonnentenspezifische Partition der veröffentlichten Daten enthält.  
  
-   Wenn das Filtern nach einem oder mehreren Artikeln in der Veröffentlichung nicht überlappende Partitionen ergibt, die für jedes Abonnement eindeutig sind, wird für Metadaten bei jedem Ausführen des Merge-Agents einen Cleanup ausgeführt. Das bedeutet, dass die partitionierte Momentaufnahme schneller abläuft. Bei dieser Methode sollten Sie zulassen, dass Abonnenten das Generieren und Übermitteln von Momentaufnahmen einleiten. Weitere Informationen zu Filteroptionen finden Sie im Abschnitt „Festlegen von ‚Partitionsoptionen‘“ von [Momentaufnahmen für Mergeveröffentlichungen mit parametrisierten Filtern](snapshots-for-merge-publications-with-parameterized-filters.md).  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Sie können Momentaufnahmen für Partitionen im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** auf der Seite **Datenpartitionen** generieren. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md). Sie können zulassen, dass Abonnenten die Momentaufnahmegenerierung und -übermittlung starten bzw. Momentaufnahmen generieren.  
  
 Vor der Generierung von Momentaufnahmen für eine oder mehrere Partitionen müssen Sie folgende Aktionen ausführen:  
  
1.  Erstellen Sie eine Mergeveröffentlichung mit dem Assistenten für neue Veröffentlichung, und geben Sie einen oder mehrere Zeilenfilter auf der Seite **Filter hinzufügen** an. Weitere Informationen finden Sie unter [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
2.  Generieren Sie eine Schemamomentaufnahme für die Veröffentlichung. Es wird standardmäßig eine Schemamomentaufnahme generiert, sobald Sie den Assistenten für neue Veröffentlichung abschließen. Sie können auch eine Schemamomentaufnahme aus [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]generieren.  
  
#### <a name="to-generate-a-schema-snapshot"></a>So generieren Sie eine Schemamomentaufnahme  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Veröffentlichungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung, für die Sie eine Momentaufnahme erstellen möchten, und klicken Sie anschließend auf **Status des Momentaufnahme-Agents anzeigen**.  
  
4.  Klicken Sie im Dialogfeld **Status des Momentaufnahme-Agents anzeigen - \<Publication>** auf **Start**.  
  
     Nachdem der Momentaufnahme-Agent die Momentaufnahme generiert hat, wird eine Meldung angezeigt, die beispielsweise wie folgt lautet: "[100%] Es wurde eine Momentaufnahme mit 17 Artikel(n) generiert".  
  
#### <a name="to-allow-subscribers-to-initiate-snapshot-generation-and-delivery"></a>So lassen Sie zu, dass Abonnenten die Momentaufnahmegenerierung und -übermittlung starten  
  
1.  Klicken Sie auf der Seite **Datenpartitionen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** auf **Bei Bedarf automatisch eine Partition definieren und eine Momentaufnahme generieren, wenn ein neuer Abonnent zu synchronisieren versucht**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-generate-and-refresh-snapshots"></a>So generieren und aktualisieren Sie Momentaufnahmen  
  
1.  Klicken Sie auf der Seite **Datenpartitionen** des Dialogfelds **Veröffentlichungseigenschaften – \<Veröffentlichung>** auf **Hinzufügen**.  
  
2.  Geben Sie einen Wert für **HOST_NAME()** und/oder **SUSER_SNAME()** ein, der der Partition zugeordnet ist, für die Sie eine Momentaufnahme erstellen möchten.  
  
3.  Optional können Sie einen Zeitplan für das Aktualisieren von Momentaufnahmen angeben:  
  
    1.  Aktivieren Sie die Option **Ausführung des Momentaufnahme-Agents für diese Partition zu folgenden Zeitpunkten planen**.  
  
    2.  Akzeptieren Sie den Standardzeitplan für die Aktualisierung von Momentaufnahmen, oder klicken Sie auf **Ändern** , um einen anderen Zeitplan anzugeben.  
  
4.  Klicken Sie auf **OK**, und Sie gelangen wieder zum Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>**.  
  
5.  Wählen Sie die Partition im Eigenschaftsraster aus, und klicken Sie anschließend auf **Die ausgewählten Momentaufnahmen jetzt generieren**.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Mithilfe von gespeicherten Prozeduren und dem Momentaufnahme-Agent können Sie folgende Aktionen durchführen:  
  
-   Abonnenten das Anfordern der Momentaufnahmegenerierung und -anwendung beim erstmaligen Synchronisieren ermöglichen.  
  
-   Vorabgenerieren von Momentaufnahmen für jede Partition.  
  
-   Manuell eine Momentaufnahme für jeden Abonnenten generieren.  
  
    > [!IMPORTANT]  
    >  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
#### <a name="to-create-a-publication-that-allows-subscribers-to-initiate-snapshot-generation-and-delivery"></a>So erstellen Sie eine Veröffentlichung, die es Abonnenten ermöglicht, die Generierung und Übermittlung von Momentaufnahmen zu initiieren  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) aus. Geben Sie die folgenden Parameter an:  
  
    -   Den Namen der Veröffentlichung für **@publication**.  
  
    -   Der Wert `true` für **@allow_subscriber_initiated_snapshot**, wodurch Abonnenten den momentaufnahmeprozess zu initiieren.  
  
    -   (Optional) Für **@max_concurrent_dynamic_snapshots**. Wird die maximale Anzahl von Prozessen ausgeführt, wenn ein Abonnent versucht, eine Momentaufnahme zu generieren, wird der Prozess in eine Warteschlange eingefügt. Standardmäßig gibt es für die Anzahl gleichzeitig ausgeführter Prozesse keine Beschränkung.  
  
2.  Führen Sie auf dem Verleger [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) aus. Geben Sie den in Schritt 1 verwendeten Veröffentlichungsnamen **@publication** und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen, unter denen die [Replication Snapshot Agent](agents/replication-snapshot-agent.md) -Authentifizierung beim Herstellen einer Verbindung mit der Herausgeber müssen Sie auch den Wert angeben **0** für **@publisher_security_mode** und [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**. Dadurch wird ein Auftrag des Momentaufnahme-Agents für die Veröffentlichung erstellt. Weitere Informationen darüber, wie eine Anfangsmomentaufnahme generiert und ein benutzerdefinierter Zeitplan für den Momentaufnahme-Agent definiert wird, finden Sie unter [Erstellen und Anwenden der Anfangsmomentaufnahme](create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &amp;#40;SQL Server-Konfigurations-Manager&amp;#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Führen Sie [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) aus, um der Veröffentlichung Artikel hinzuzufügen. Diese gespeicherte Prozedur muss einmal für jeden Artikel in der Veröffentlichung ausgeführt werden. Wenn Sie parametrisierte Filter verwenden, müssen Sie mithilfe des Parameters **@subset_filterclause** einen parametrisierten Filter für einen oder mehrere Artikel angeben. Weitere Informationen finden Sie unter [Define and Modify a Parameterized Row Filter for a Merge Article](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Werden andere Artikel basierend auf dem parametrisierten Zeilenfilter gefiltert, dann führen Sie [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) aus, um den Join oder die logische Datensatzbeziehung zwischen Artikeln zu definieren. Diese gespeicherte Prozedur muss einmal für jede zu definierende Beziehung ausgeführt werden. Weitere Informationen finden Sie unter [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Wenn der Merge-Agent die Momentaufnahme zur Initialisierung des Abonnenten anfordert, wird die Momentaufnahme für die anfordernde Partition des Abonnements automatisch generiert.  
  
#### <a name="to-create-a-publication-and-pre-generate-or-automatically-refresh-snapshots"></a>So erstellen Sie eine Veröffentlichung, und generieren vorab Momentaufnahmen oder aktualisieren sie automatisch  
  
1.  Führen Sie [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) aus, um die Publikation zu erstellt. Weitere Informationen finden Sie unter [Create a Publication](publish/create-a-publication.md).  
  
2.  Führen Sie auf dem Verleger [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) aus. Geben Sie den in Schritt 1 verwendeten Veröffentlichungsnamen für **@publication** und die Windows-Anmeldeinformationen, unter denen der Momentaufnahme-Agent ausgeführt wird, für **@job_login** und **@password**. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**. Dadurch wird ein Auftrag des Momentaufnahme-Agents für die Veröffentlichung erstellt. Weitere Informationen darüber, wie eine Anfangsmomentaufnahme generiert und ein benutzerdefinierter Zeitplan für den Momentaufnahme-Agent definiert wird, finden Sie unter [Erstellen und Anwenden der Anfangsmomentaufnahme](create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &amp;#40;SQL Server-Konfigurations-Manager&amp;#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Führen Sie [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) aus, um der Veröffentlichung Artikel hinzuzufügen. Diese gespeicherte Prozedur muss einmal für jeden Artikel in der Veröffentlichung ausgeführt werden. Wenn Sie parametrisierte Filter verwenden, müssen Sie mithilfe des Parameters **@subset_filterclause** einen parametrisierten Filter für einen oder mehrere Artikel angeben. Weitere Informationen finden Sie unter [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Werden andere Artikel basierend auf dem parametrisierten Zeilenfilter gefiltert, dann führen Sie [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) aus, um den Join oder die logische Datensatzbeziehung zwischen Artikeln zu definieren. Diese gespeicherte Prozedur muss einmal für jede zu definierende Beziehung ausgeführt werden. Weitere Informationen finden Sie unter [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql) unter Angabe des Werts aus Schritt 1 für **@publication** aus. Achten Sie auf den Wert von **snapshot_jobid** im Resultset.  
  
6.  Konvertieren Sie den in Schritt 5 ermittelten Wert von **snapshot_jobid** in **uniqueidentifier**.  
  
7.  Führen Sie auf dem Verleger für die **msdb**-Datenbank [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql) aus, wobei Sie den in Schritt 6 konvertierten Wert für **@job_id** angeben.  
  
8.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql) aus. Geben Sie den Namen der Veröffentlichung aus Schritt 1 für **@publication** und den zur Definition der Partition verwendeten Wert entweder für **@suser_sname**, wenn [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) in der Filterklausel verwendet wird, oder für **@host_name** an, wenn [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) in der Filterklausel verwendet wird.  
  
9. Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank[sp_adddynamicsnapshot_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql) aus. Geben Sie den Namen der Veröffentlichung aus Schritt 1 für **@publication**, den Wert aus Schritt 8 für **@suser_sname** oder **@host_name** sowie einen Zeitplan für den Auftrag an. Dadurch wird der Auftrag erstellt, der die parametrisierte Momentaufnahme für die angegebene Partition generiert. Weitere Informationen finden Sie unter [Specify Synchronization Schedules](specify-synchronization-schedules.md).  
  
    > [!NOTE]  
    >  Dieser Auftrag wird mit dem gleichen Windows-Konto ausgeführt wie der in Schritt 2 definierte Anfangs-Momentaufnahmeauftrag. Um den parametrisierten Momentaufnahmeauftrag und seine zugehörige Datenpartition zu entfernen, führen Sie [sp_dropdynamicsnapshot_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql) aus.  
  
10. Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql) aus, und geben Sie den Wert aus Schritt 1 für **@publication** und den Wert **@suser_sname** oder **@host_name** aus Schritt 8 an. Achten Sie auf den Wert von **dynamic_snapshot_jobid** im Resultset.  
  
11. Führen Sie auf dem Verteiler für die **msdb**-Datenbank [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql) aus, wobei Sie den in Schritt 9 ermittelten Wert für **@job_id** angeben. Dadurch wird der parametrisierte Momentaufnahmeauftrag für die Partition gestartet.  
  
12. Wiederholen Sie die Schritte 8 bis 11, um für jedes Abonnement eine partitionierte Momentaufnahme zu generieren.  
  
#### <a name="to-create-a-publication-and-manually-create-snapshots-for-each-partition"></a>So erstellen Sie eine Veröffentlichung und für jede Partition manuell Momentaufnahmen  
  
1.  Führen Sie [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) aus, um die Publikation zu erstellt. Weitere Informationen finden Sie unter [Create a Publication](publish/create-a-publication.md).  
  
2.  Führen Sie auf dem Verleger [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) aus. Geben Sie den in Schritt 1 verwendeten Veröffentlichungsnamen für **@publication** und die Windows-Anmeldeinformationen, unter denen der Momentaufnahme-Agent ausgeführt wird, für **@job_login** und **@password**. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**. Dadurch wird ein Auftrag des Momentaufnahme-Agents für die Veröffentlichung erstellt. Weitere Informationen darüber, wie eine Anfangsmomentaufnahme generiert und ein benutzerdefinierter Zeitplan für den Momentaufnahme-Agent definiert wird, finden Sie unter [Erstellen und Anwenden der Anfangsmomentaufnahme](create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &amp;#40;SQL Server-Konfigurations-Manager&amp;#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Führen Sie [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) aus, um der Veröffentlichung Artikel hinzuzufügen. Diese gespeicherte Prozedur muss einmal für jeden Artikel in der Veröffentlichung ausgeführt werden. Wenn Sie parametrisierte Filter verwenden, müssen Sie mithilfe des Parameters **@subset_filterclause** einen parametrisierten Filter für einen oder mehrere Artikel angeben. Weitere Informationen finden Sie unter [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Werden andere Artikel basierend auf dem parametrisierten Zeilenfilter gefiltert, dann führen Sie [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) aus, um den Join oder die logische Datensatzbeziehung zwischen Artikeln zu definieren. Diese gespeicherte Prozedur muss einmal für jede zu definierende Beziehung ausgeführt werden. Weitere Informationen finden Sie unter [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Starten Sie den Momentaufnahmeauftrag oder führen Sie den Replikationsmomentaufnahme-Agent von der Eingabeaufforderung aus, um das Standard-Momentaufnahmeschema und andere Dateien zu erzeugen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
6.  Führen Sie den Replikationsmomentaufnahme-Agent erneut von der Eingabeaufforderung aus, um BCP-Dateien (Massenkopierdateien) zu erstellen, wobei Sie den Speicherort der partionierten Momentaufnahme für **-DynamicSnapshotLocation** und eine oder beide der folgenden Eigenschaften zur Definition der Partition angeben:  
  
    -   **-DynamicFilterHostName** – der Wert, wenn [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) verwendet wird.  
  
    -   **-DynamicFilterLogin** - der Wert, wenn [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) verwendet wird.  
  
7.  Wiederholen Sie Schritt 8, um für jedes Abonnement eine partitionierte Momentaufnahme zu generieren.  
  
8.  Führen Sie den Merge-Agent für jedes Abonnement aus, um die partitionierte Anfangsmomentaufnahme auf die Abonnenten anzuwenden, wobei Sie die folgenden Eigenschaften angeben:  
  
    -   **-Hostname** &ndash; der zur Definition der Partition verwendete Wert, wenn der tatsächliche Wert von HOST_NAME überschrieben wurde.  
  
    -   **-DynamicSnapshotLocation** &ndash; der Speicherort der dynamischen Momentaufnahme für diese Partition.  
  
> [!NOTE]  
>  Weitere Informationen zur Programmierung von Replikations-Agents finden Sie unter [Ausführbare Konzepte für die Programmierung von Replikations-Agents](concepts/replication-agent-executables-concepts.md).  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel wird eine Mergeveröffentlichung mit parametrisierten Filtern erstellt, bei der die Abonnenten den Momentaufnahmegenerierungsprozess initiieren. Die Werte für **@job_login** und **@job_password** werden mithilfe von Skriptvariablen übergeben.  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
 In diesem Beispiel wird eine Mergeveröffentlichung mit parametrisierten Filtern erstellt, bei der die Partition jedes Abonnenten durch Ausführung von [sp_addmergepartition](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql) definiert wird, und der gefilterte Momentaufnahmeauftrag durch Ausführung von [sp_adddynamicsnapshot_job](/sql/relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql) unter Angabe der Partitionierungsinformationen erstellt wird. Die Werte für **@job_login** und **@job_password** werden mithilfe von Skriptvariablen übergeben.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic2.sql#sp_mergedynamicpubpluspartition)]  
  
 In diesem Beispiel wird eine Mergeveröffentlichung mit parametrisierten Filtern erstellt, bei der die Partition und der gefilterte Momentaufnahmeauftrag jedes Abonnenten durch Angabe der Partitionierungsinformationen erstellt wird. Ein Abonnent gibt die Partitionierungsinformationen mithilfe von Befehlszeilenparametern an, wenn die Replikations-Agents manuell ausgeführt werden. In diesem Beispiel wird davon ausgegangen, dass auch ein Abonnement für die Veröffentlichung erstellt wurde.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPartitionManual](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic3.sql#sp_mergedynamicpubpartitionmanual)]  
  
 
```
REM Line breaks are added to improve readability.   
REM In a batch file, commands must be made in a single line.  
REM Run the Snapshot agent from the command line to generate the standard snapshot   
REM schema and other files.   
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub% -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  
  
PAUSE  
```

```
REM Run the Snapshot agent from the command line, this time to generate   
REM the bulk copy (.bcp) data for each Subscriber partition.    
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
MD %SnapshotDir%  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub%  -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  -DynamicFilterHostName "adventure-works\Fernando"    
-DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
```

```
REM Run the Merge Agent for each subscription to apply the partitioned   
REM snapshot for each Subscriber.    
SET Publisher = %computername%  
SET Subscriber = %computername%  
SET PubDB = AdventureWorks2012   
SET SubDB = AdventureWorks2012Replica   
SET PubName = AdvWorksSalesPersonMerge   
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publisher  %Publisher%    
-Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB %PubDB%    
-SubscriberDB %SubDB% -Publication %PubName%  -PublisherSecurityMode 1  -OutputVerboseLevel 3    
-Output -SubscriberSecurityMode 1  -SubscriptionType 3 -DistributorSecurityMode 1    
-Hostname "adventure-works\Fernando"  -DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE
```
  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Sie können Replikationsverwaltungsobjekte (RMO) verwenden, um partitionierte Momentaufnahmen mit einem der folgenden Verfahren programmgesteuert zu generieren:  
  
-   Abonnenten das Anfordern der Momentaufnahmegenerierung und -anwendung beim erstmaligen Synchronisieren ermöglichen.  
  
-   Vorabgenerieren von Momentaufnahmen für jede Partition.  
  
-   Manuelles Generieren einer Momentaufnahme für jeden Abonnenten durch Ausführen des Momentaufnahme-Agent  
  
> [!NOTE]  
>  Wenn das Filtern für einen Artikel nicht überlappende Partitionen ergibt, die für jedes Abonnement eindeutig sind (durch Angabe des Werts <xref:Microsoft.SqlServer.Replication.PartitionOptions.NonOverlappingSingleSubscription> für <xref:Microsoft.SqlServer.Replication.MergeArticle.PartitionOption%2A> beim Erstellen eines Mergeartikels), werden Metadaten immer dann bereinigt, wenn der Merge-Agent ausgeführt wird. Das bedeutet, dass die partitionierte Momentaufnahme schneller abläuft. Bei dieser Methode sollten Sie zulassen, dass Abonnenten das Generieren von Momentaufnahmen anfordern. Weitere Informationen finden Sie unter "Verwenden der richtigen Filteroptionen" im Thema [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Sie Anmeldeinformationen speichern müssen, verwenden Sie die [Kryptografiedienste](http://go.microsoft.com/fwlink/?LinkId=34733) von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-create-a-publication-that-allows-subscribers-to-initiate-snapshot-generation-and-delivery"></a>So erstellen Sie eine Veröffentlichung, die es Abonnenten ermöglicht, die Generierung und Übermittlung von Momentaufnahmen zu initiieren  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> -Klasse für die Veröffentlichungsdatenbank, legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die Instanz von <xref:Microsoft.SqlServer.Management.Common.ServerConnection> aus Schritt 1 fest, und rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf. Wenn <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> den Wert `false` zurückgibt, vergewissern Sie sich, dass die Datenbank vorhanden ist.  
  
3.  Wenn <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> Eigenschaft `false`, legen Sie ihn auf `true` , und rufen Sie <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> -Klasse, und legen Sie die folgenden Eigenschaften für dieses Objekt fest:  
  
    -   Die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Den Namen der veröffentlichten Datenbank für <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Einen Namen für die Veröffentlichung für <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Die maximale Anzahl an Aufträgen für dynamische Momentaufnahmen, die für <xref:Microsoft.SqlServer.Replication.MergePublication.MaxConcurrentDynamicSnapshots%2A>ausgeführt werden können. Da von Abonnenten initiierte Momentaufnahmeanforderungen jederzeit erfolgen können, begrenzt diese Eigenschaft die Anzahl der Momentaufnahme-Agentaufträge, die gleichzeitig ausgeführt werden können, wenn mehrere Abonnenten ihre partitionierte Momentaufnahme gleichzeitig anfordern. Wenn die maximale Anzahl an Aufträgen ausgeführt wird, werden weitere Anforderungen für partitionierte Momentaufnahmen in die Warteschlange eingefügt, bis einer der Aufträge abgeschlossen ist.  
  
    -   Verwenden Sie den bitweisen logischen OR (`|` in Visual C#- und `Or` in Visual Basic) Operator, um den Wert hinzufügen <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowSubscriberInitiatedSnapshot> zu <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>.  
  
    -   Die Felder <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> und <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> von <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> , um die Anmeldeinformationen für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto bereitzustellen, unter dem der Momentaufnahme-Agentauftrag ausgeführt wird.  
  
        > [!NOTE]  
        >  Wenn die Veröffentlichung von einem Mitglied der festen Serverrolle `sysadmin` erstellt wird, empfiehlt es sich, <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> festzulegen. Weitere Informationen finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> -Methode auf, um die Veröffentlichung zu erstellen.  
  
    > [!IMPORTANT]  
    >  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Eigenschaften einschließlich <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie die <xref:Microsoft.SqlServer.Replication.Publication.Create%2A>-Methode aufrufen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &amp;#40;SQL Server-Konfigurations-Manager&amp;#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
6.  Verwenden Sie die <xref:Microsoft.SqlServer.Replication.MergeArticle> -Eigenschaft, um der Veröffentlichung Artikel hinzuzufügen. Geben Sie die <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> -Eigenschaft für wenigstens einen Artikel an, der den parametrisierten Filter definiert. (Optional) Erstellen Sie <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> -Objekte, die Joinfilter zwischen Artikeln definieren. Weitere Informationen finden Sie unter [Define an Article](publish/define-an-article.md).  
  
7.  Wenn der Wert des <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> ist `false`, rufen Sie <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> um die anfängliche Momentaufnahme-Agentauftrag für diese Veröffentlichung zu erstellen.  
  
8.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> -Methode des in Schritt 4 erstellten <xref:Microsoft.SqlServer.Replication.MergePublication> -Objekts auf. Dadurch wird der Agentauftrag gestartet, der die Anfangsmomentaufnahme generiert. Weitere Informationen darüber, wie eine Anfangsmomentaufnahme generiert und ein benutzerdefinierter Zeitplan für den Momentaufnahme-Agent definiert wird, finden Sie unter [Erstellen und Anwenden der Anfangsmomentaufnahme](create-and-apply-the-initial-snapshot.md).  
  
9. (Optional) Kontrollieren Sie, wann die <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A>-Eigenschaft auf `true` lautet, um zu ermitteln, wann die Anfangsmomentaufnahme verwendet werden kann.  
  
10. Wenn der Merge-Agent eines Abonnenten die Verbindung erstmalig herstellt, wird automatisch eine partitionierte Momentaufnahme generiert.  
  
#### <a name="to-create-a-publication-and-pregenerate-or-automatically-refresh-snapshots"></a>So erstellen Sie eine Veröffentlichung und generieren Momentaufnahmen vorab oder aktualisieren sie automatisch  
  
1.  Verwenden Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> -Klasse, um eine Mergeveröffentlichung zu definieren. Weitere Informationen finden Sie unter [Create a Publication](publish/create-a-publication.md).  
  
2.  Verwenden Sie die <xref:Microsoft.SqlServer.Replication.MergeArticle> -Eigenschaft, um der Veröffentlichung Artikel hinzuzufügen. Geben Sie die <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> -Eigenschaft für mindestens einen Artikel an, der den parametrisierten Filter definiert, und erstellen Sie beliebige <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> -Objekte, die Joinfilter zwischen Artikeln definieren. Weitere Informationen finden Sie unter [Define an Article](publish/define-an-article.md).  
  
3.  Wenn der Wert des <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> ist `false`, rufen Sie <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> den Momentaufnahme-Agentauftrag für diese Veröffentlichung zu erstellen.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> -Methode des in Schritt 1 erstellten <xref:Microsoft.SqlServer.Replication.MergePublication> -Objekts auf. Durch diese Methode wird der Agentauftrag gestartet, der die Anfangsmomentaufnahme generiert. Weitere Informationen darüber, wie eine Anfangsmomentaufnahme generiert und ein benutzerdefinierter Zeitplan für den Momentaufnahme-Agent definiert wird, finden Sie unter [Erstellen und Anwenden der Anfangsmomentaufnahme](create-and-apply-the-initial-snapshot.md).  
  
5.  Überprüfen Sie auf einen Wert von `true` für die <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> Eigenschaft, um zu bestimmen, wann die anfangsmomentaufnahme verwendet werden kann.  
  
6.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePartition> -Klasse, und legen Sie die Kriterien für den parametrisierten Filter des Abonnenten fest, indem Sie eine der folgenden Eigenschaften oder beide verwenden:  
  
    -   Wenn die Partition des Abonnenten durch das Ergebnis von [SUSER_SNAME (Transact-SQL)](/sql/t-sql/functions/suser-sname-transact-sql) definiert wird, verwenden Sie <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A>.  
  
    -   Wenn die Partition des Abonnenten durch das Ergebnis von [HOST_NAME (Transact-SQL)](/sql/t-sql/functions/host-name-transact-sql) oder eine Überladung dieser Funktion definiert wird, verwenden Sie <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A>.  
  
7.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> -Klasse, und legen Sie dieselbe Eigenschaft wie in Schritt 6 fest.  
  
8.  Verwenden Sie die <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> -Klasse, um einen Zeitplan für die Generierung der gefilterten Momentaufnahme für die Abonnentenpartition zu definieren.  
  
9. Rufen Sie mithilfe der Instanz von <xref:Microsoft.SqlServer.Replication.MergePublication> aus Schritt 1 <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergePartition%2A>auf. Übergeben Sie das <xref:Microsoft.SqlServer.Replication.MergePartition> -Objekt aus Schritt 6.  
  
10. Rufen Sie mithilfe der Instanz von <xref:Microsoft.SqlServer.Replication.MergePublication> aus Schritt 1 die <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergeDynamicSnapshotJob%2A> -Methode auf. Übergeben Sie das <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> -Objekt aus Schritt 7 und das <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> -Objekt aus Schritt 8.  
  
11. Rufen Sie <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergeDynamicSnapshotJobs%2A>auf, und suchen Sie im zurückgegebenen Array nach dem <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> -Objekt für den neu hinzugefügten Auftrag für die partitionierte Momentaufnahme.  
  
12. Rufen Sie die <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob.Name%2A> -Eigenschaft für den Auftrag ab.  
  
13. Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
14. Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Management.Smo.Server> -Klasse für SQL Server Management Objects (SMO), indem Sie das <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt aus Schritt 13 übergeben.  
  
15. Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Management.Smo.Agent.Job> -Klasse, indem Sie die <xref:Microsoft.SqlServer.Management.Smo.Server.JobServer%2A> -Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Server> -Objekts aus Schritt 14 und den Auftragnamen aus Schritt 12 übergeben.  
  
16. Rufen Sie die <xref:Microsoft.SqlServer.Management.Smo.Agent.Job.Start%2A> -Methode auf, um den Auftrag für die partitionierte Momentaufnahme zu starten.  
  
17. Wiederholen Sie die Schritte 6 bis 16 für jeden Abonnenten.  
  
#### <a name="to-create-a-publication-and-manually-create-snapshots-for-each-partition"></a>So erstellen Sie eine Veröffentlichung und für jede Partition manuell Momentaufnahmen  
  
1.  Verwenden Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> -Klasse, um eine Mergeveröffentlichung zu definieren. Weitere Informationen finden Sie unter [Create a Publication](publish/create-a-publication.md).  
  
2.  Verwenden Sie die <xref:Microsoft.SqlServer.Replication.MergeArticle> -Eigenschaft, um der Veröffentlichung Artikel hinzuzufügen. Geben Sie die <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> -Eigenschaft für mindestens einen Artikel an, der den parametrisierten Filter definiert, und erstellen Sie beliebige <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> -Objekte, die Joinfilter zwischen Artikeln definieren. Weitere Informationen finden Sie unter [Define an Article](publish/define-an-article.md).  
  
3.  Generieren Sie die Anfangsmomentaufnahme. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
4.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Klasse, und legen Sie die folgenden erforderlichen Eigenschaften fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> – Name des Verlegers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> – Name der Veröffentlichungsdatenbank  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> &ndash; Den Namen der Veröffentlichung  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> &ndash; Den Namen des Verteilers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> – Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> , wenn die integrierte Windows-Authentifizierung verwendet werden soll, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> , wenn die SQL Server-Authentifizierung verwendet werden soll.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> – Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> , wenn die integrierte Windows-Authentifizierung verwendet werden soll, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> , wenn die SQL Server-Authentifizierung verwendet werden soll.  
  
5.  Legen Sie den Wert <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>fest.  
  
6.  Legen Sie eine oder mehrere der folgenden Eigenschaften fest, um die Partitionierungsparameter zu definieren:  
  
    -   Wenn die Partition des Abonnenten durch das Ergebnis von [SUSER_SNAME (Transact-SQL)](/sql/t-sql/functions/suser-sname-transact-sql) definiert wird, verwenden Sie <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin%2A>.  
  
    -   Wenn die Partition des Abonnenten durch das Ergebnis von [HOST_NAME (Transact-SQL)](/sql/t-sql/functions/host-name-transact-sql) oder eine Überladung dieser Funktion definiert wird, verwenden Sie <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName%2A>.  
  
7.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> -Methode auf.  
  
8.  Wiederholen Sie die Schritte 4 - 7 für jeden Abonnenten.  
  
###  <a name="PShellExample"></a> Beispiele (RMO)  
 In diesem Beispiel wird eine Mergeveröffentlichung erstellt, die es Abonnenten ermöglicht, die Momentaufnahmegenerierung anzufordern.  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
 In diesem Beispiel werden die Abonnentenpartition und die gefilterte Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Zeilenfiltern manuell erstellt.  
  
 [!code-csharp[HowTo#rmo_CreateMergePartition](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepartition)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePartition](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepartition)]  
  
 In diesem Beispiel wird der Momentaufnahme-Agent manuell gestartet, um die gefilterten Momentaufnahmedaten für den Abonnenten einer Mergeveröffentlichung mit parametrisierten Zeilenfiltern zu generieren.  
  
 [!code-csharp[HowTo#rmo_GenerateFilteredSnapshot](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_generatefilteredsnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateFilteredSnapshot](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_generatefilteredsnapshot)]  
  
## <a name="see-also"></a>Siehe auch  
 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)   
 [Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md)   
 [Momentaufnahmen für eine Mergeveröffentlichung mit parametrisierten Filtern](snapshots-for-merge-publications-with-parameterized-filters.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)  
  
  
