---
title: Datenverwaltungsansichten (DMVs) für SQLServer Machine Learning-Dienste | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8d7d20d396ca5b853d959c84a371fe808415c5fb
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395892"
---
# <a name="dmvs-for-sql-server-machine-learning-services"></a>DMVs für SQL Server-Machine Learning-Dienste
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Listet die systemkatalogsichten und DMVs, die Machine Learning in SQL Server verknüpft sind.

Weitere Informationen zu erweiterten Ereignissen finden Sie unter [erweiterte Ereignisse für Machine Learning](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md).

> [!TIP]
> Verwenden Sie integrierte Berichte, um Machine Learning-Sitzungen überwachen und die Paket-Auslastung. Weitere Informationen finden Sie unter [Überwachen von Machine Learning mithilfe von benutzerdefinierten Berichten in Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="system-configuration-and-system-resources"></a>Systemkonfiguration und Ressourcen

Sie können überwachen und analysieren Sie die Ressourcen, die von externen Skripts verwendet werden, mithilfe von [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] systemkatalogsichten und DMVs.

+ [ sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)

  Gibt Informationen für Benutzerverbindungen und Systemsitzungen zurück. Sie können die Systemsitzungen anhand der *session_id*-Spalte identifizieren. Werte größer als oder gleich 51 sind Benutzerverbindungen und Werte kleiner als 51 sind Systemprozesse.

+ [sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)

  Gibt eine Zeile für jeden Leistungsindikator im System zurück, der vom Server verwendet wird.  Mithilfe dieser Informationen können Sie sehen, wie viele Skripts ausgeführt wurden, welche Skripts mit welchem Authentifizierungsmodus ausgeführt wurden oder wie viele R-Aufrufe für die gesamte Instanz ausgegeben wurden.

  In diesem Beispiel werden nur die Leistungsindikatoren im Zusammenhang mit R-Skript abgerufen:

  ```SQL
  SELECT * from sys.dm_os_performance_counters WHERE object_name LIKE '%External Scripts%'
  ```

  Die folgenden Leistungsindikatoren werden von dieser DMV für externe Skripts pro Instanz gemeldet:

  + **Total Executions**: Anzahl externer Prozesse gestartet durch lokale oder remote-Aufrufe
  + **Parallele Ausführungen**: Anzahl der Fälle, in denen ein Skript enthalten die _@parallel_ -Spezifikation und die [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] konnte zum Generieren und verwenden einen parallelen Abfrageplan
  + **Streaming Executions**: Anzahl der Fälle, in denen die streaming-Funktion aufgerufen wurde
  + **SQL CC Executions**: Anzahl von externen Skripts ausführen, in dem der Aufruf Remote instanziiert wurde und SQL Server als computekontext verwendet,
  + **Implied Auth. Logins**: Gibt an, wie oft ein ODBC-Loopback-Aufruf mit implizierter Authentifizierung abgeschlossen wurde, d.h. dass [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] den Aufruf im Auftrag des Benutzers ausführt und die Skriptanforderung sendet
  + **Gesamtausführungszeit (ms)**: verstrichene Zeit zwischen dem Aufruf und der Abschluss des Aufrufs
  + **Execution Errors**: Wie oft Skripts Fehler gemeldet haben Diese Zahl umfasst keine R-Fehler.


+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)

  Diese DMV gibt eine einzelne Zeile für jedes Workerkonto an, das ein externes Skript ausführt. Beachten Sie, dass dieses Workerkonto sich von den Anmeldeinformationen der Person unterscheidet, die das Skript sendet. Wenn ein einzelner Windows-Benutzer mehrere Skriptanforderungen sendet, würde nur ein Workerkonto zum Behandeln aller Anforderungen dieses Benutzer zugewiesen werden. Wenn sich ein anderer Windows-Benutzer anmeldet, um ein externes Skript auszuführen, würde die Anforderung von einem separaten Arbeitskonto verarbeitet werden.

  Diese DMV gibt keine Ergebnisse zurück, wenn derzeit keine Skripts ausgeführt werden. Daher ist es besonders hilfreich für die Überwachung lang ausgeführter Skripts. Es gibt folgende Werte zurück:

  + **External_script_request_id**: eine GUID, die auch als temporärer Name des Arbeitsverzeichnisses zum Speichern von Skripts und Zwischenergebnisse verwendet wird
  + **Sprache**: einen Wert wie z. B. `R` , die die Sprache des externen Skripts bezeichnet
  + **Degree_of_parallelism**: eine ganze Zahl, der angibt, welche Anzahl von parallelen Prozesse, die verwendet wurden
  + **External_user_name**: ein Launchpad-Worker zu berücksichtigen, wie z. B. **SQLRUser01**

+ [sys.dm_external_script_execution_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)

  Diese dynamische Verwaltungssicht ist zur internen Überwachung (Telemetrie), um nachzuverfolgen, wie viele Aufrufe von externen Skripts für eine Instanz ausgeführt werden. Der telemetriedienst startet, wenn [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] und inkrementiert einen datenträgerbasierten Zähler jedes Mal ein bestimmtes Machine learning-Funktion aufgerufen wird.

  Der Indikator wird pro Aufruf an eine bestimmte Funktion für die nachverfolgte erhöht. Wenn `rxLinMod` z. B. parallel aufgerufen und ausgeführt wird, wird der Leistungsindikator um 1 erhöht.
  
  Leistungsindikatoren sind im Allgemeinen nur so lange gültig, wie der Prozess aktiv ist, der sie generiert hat. Daher kann eine Abfrage für eine DMV keine ausführlichen Daten für Dienste anzeigen, die beendet wurden. Beispielsweise zeigt eine DMV möglicherweise keine Daten an, wenn das Launchpad mehrere parallele R-Aufträge erstellt und sie sehr schnell ausgeführt und anschließend durch das Windows-Auftragsobjekt bereinigt werden.
 
  Daher bleiben die von der DMV verfolgten Leistungsindikatoren aktiv und der Status für Leistungsindikatoren von „dm_external_script _execution“ wird beibehalten, indem Schreibvorgänge auf den Datenträger verwendet werden, auch wenn die Instanz heruntergefahren wird.
 
 Weitere Informationen zu Leistungsindikatoren von [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] finden Sie unter [Verwenden von SQL Server-Objekten](../../relational-databases/performance-monitor/use-sql-server-objects.md).

## <a name="resource-governor-views"></a>Sichten der Ressourcenkontrolle

In den Editionen, die Unterstützung der Ressourcenkontrolle, möglich Erstellen von externen Ressourcenpools für R oder Python-Workloads En effektiv nachverfolgen und Verwalten von Ressourcen.

+ [sys.resource_governor_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)

  Gibt Informationen zum aktuellen Status der Ressourcenpools, zur aktuellen Konfiguration der Ressourcenpools sowie Statistiken zu den Ressourcenpools zurück.

  > [!IMPORTANT]
  > 
  > Sie müssen Ressourcenpools ändern, die auf anderen Serverdiensten angewendet werden, bevor Sie R-Diensten zusätzliche Ressourcen zuteilen können.

+ [sys.resource_governor_external_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)

  Eine neue Katalogansicht, die die aktuellen Konfigurationswerte für externe Ressourcenpools anzeigt.
  In der Enterprise Edition können Sie zusätzliche externe Ressourcenpools konfigurieren: Beispielsweise können Sie Ressourcen für R-Aufträge in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] getrennt von denen verarbeiten, die von einem Remoteclient stammen.

  > [!NOTE]
  > 
  > Führen in der Standard Edition alle externen Skripts für Aufträge in der gleichen externen standardressourcenpool.

+ [sys.resource_governor_workload_groups](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)

  Gibt Statistiken zu Arbeitsauslastungsgruppen sowie die aktuelle Konfiguration der Arbeitsauslastungsgruppen zurück. Diese Sicht kann mit `sys.dm_resource_governor_resource_pools` verknüpft werden, um den Ressourcenpoolnamen abzurufen.
  Für externe Skripts wurde eine neue Spalte hinzugefügt, die die Id des externen Pools der zugeordneten Arbeitsauslastungsgruppe anzeigt.

+ [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)

  Eine neue Systemkatalogsicht, die die Prozessoren und die Ressourcen anzeigt, die einem bestimmten Ressourcenpool zugeordnet werden.

  Gibt eine Zeile pro Zeitplanungsmodul in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] zurück, wobei jedes Zeitplanungsmodul einem einzelnen Prozessor zugeordnet ist. Mithilfe dieser Sicht können Sie den Zustand eines Zeitplanungsmoduls überwachen oder Endlostasks identifizieren.

  In der Standardkonfiguration werden Workload-Pools automatisch Prozessoren zugewiesen, und es gibt daher keine Affinitätswerte, die zurückgegeben werden.

  Der Zeitplan für die Affinität ordnet den Ressourcenpool den von den angegebenen IDs identifizierten [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Zeitplänen zu. Diese IDs zugeordnet werden, um die Werte in der `scheduler_id` Spalte `sys.dm_os_schedulers`.


> [!NOTE] 
> 
> Obwohl die Möglichkeit zum Konfigurieren und Anpassen von Ressourcenpools nur in den Editionen Enterprise und Developer besteht, sind die Standardpools sowie die DMVs in allen Editionen verfügbar. Aus diesem Grund können Sie diese DMVs in der Standard Edition verwenden, bestimmen von Resource Caps für Ihre externe Skripts für Aufträge.

Allgemeine Informationen zum Überwachen von [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Instanzen finden Sie unter [Katalogsichten](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) und [Dynamische Verwaltungssichten in Verbindung mit der Ressourcenkontrolle](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="monitoring-script-execution"></a>Überwachen der Ausführung des Skripts

R und Python-Skripts, die parallel [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] gestartet werden, indem die [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Schnittstelle. Das Launchpad wird jedoch nicht durch Ressourcen gesteuert oder separat überwacht, da davon ausgegangen wird, dass es sich um sichere Dienste von Microsoft handelt, die Ressourcen entsprechend verwalten.

Einzelne unter dem Launchpad-Dienst ausgeführte Skripts werden mithilfe von verwaltet die [Windows-Auftragsobjekt](/windows/desktop/ProcThread/job-objects). Ein Auftragsobjekt ermöglicht es, Gruppen von Prozessen als Einheit zu verwalten. Jedes Objekt ist hierarchisch aufgebaut und steuert die Attribute aller zugeordneten Prozesse. Vorgänge für ein Auftragsobjekt wirken sich auf alle Prozesse aus, die dem Auftragsobjekt zugeordnet sind.

Daher sollten Sie daran denken, auch alle zugehörigen Prozesse beendet werden, wenn Sie einen Auftrag im Zusammenhang mit einem Objekt beenden müssen. Wenn Sie ein R-Skript ausführen, das einem Windows-Auftragsobjekt zugewiesen ist, und das Skript einen entsprechenden ODBC-Auftrag ausführt, der beendet werden muss, wird der übergeordnete Prozess des R-Skripts ebenfalls beendet.

Wenn Sie ein externes Skript, das parallelen Verarbeitung verwendet starten, verwaltet ein einzelnes Windows-Auftragsobjekt alle untergeordneten Prozesse.

Verwenden Sie die Funktion `IsProcessInJob`, um festzustellen, ob ein Prozess in einem Auftrag ausgeführt wird.

## <a name="next-steps"></a>Nächste Schritte

[Verwalten und Überwachen von Machine Learning-Lösungen](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
