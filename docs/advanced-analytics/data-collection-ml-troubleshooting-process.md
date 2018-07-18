---
title: Problembehandlung bei Datensammlung für Machine Learning - SQL Server
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9b0fdd8d198675720188d6ab2417be97a9280c57
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34708408"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Problembehandlung bei der Datensammlung für Machine learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt Datensammlungsmethoden zu verwendende beim Beheben von Problemen bei der selbständigen oder mithilfe von Microsoft-Kunden unterstützen. 

**Gilt für:** SQL Server 2016-R-Services, SqlServer 2017 Machine Learning-Dienste (R und Python)


## <a name="sql-server-version-and-edition"></a>SQL Server-Version und edition

SQL Server 2016 R Services ist die erste Version von SQL Server integrierte Unterstützung für R einschließen. SQL Server 2016 Service Pack 1 (SP1) enthält mehrere wichtige Verbesserungen, einschließlich der Möglichkeit zum Ausführen externer Skripts. Wenn Sie eine SQL Server 2016-Kunde sind, sollten Sie die Installation von SP1 oder höher.

SQL Server-2017 hinzugefügt Sprachintegration Python. Integration von Python-Funktion kann nicht in früheren Versionen nicht abgerufen werden.

Für die Unterstützung nach "," erste Edition und Versionen finden Sie im Artikel, der für jede der Buildnummern aufgelistet sind die [SQL Server-Versionen](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

Abhängig von der Edition von SQL Server, die Sie verwenden können möglicherweise einige Machine learning-Funktionen nicht verfügbar oder eingeschränkt. Die folgenden Artikel Liste von Machine Learning-Funktionen in der Enterprise, Developer, Standard und Express-Editionen.

* [Editionen und unterstützten Funktionen von SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [R und Python-Funktionen von SQL Server-Editionen](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>R-Sprache und Tool-Versionen

Im Allgemeinen wird die Version des Microsoft-R, die installiert ist, wenn Sie die R-Services-Funktion oder der Machine Learning-Dienstfeature auswählen durch die SQL Server-Buildnummer bestimmt. Ob Sie ein upgrade oder Patch für SQL Server, müssen Sie auch aktualisiert oder ein patch ihre R-Komponenten.

Eine Liste der Versionen und Links zu Downloads von R-Komponente, finden Sie unter [Machine Learning-Komponenten ohne Internetzugang installieren](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). Auf Computern mit Internetzugriff ist die erforderliche Version von R identifiziert und automatisch installiert.

Es ist möglich, aktualisieren Sie die R-Server-Komponenten separat aus dem SQL Server-Datenbankmodul in einem Prozess, der als Bindung bezeichnet. Aus diesem Grund kann die Version von R, mit denen Sie beim Ausführen von R-Code in SQL Server unterscheiden, je nach sowohl die installierte Version von SQL Server und gibt an, ob Sie den Server auf die neueste Version der R migriert haben.

### <a name="determine-the-r-version"></a>Ermitteln Sie die R-version

Die einfachste Möglichkeit zum Ermitteln der R-Version wird zum Abrufen der Common Language Runtime-Eigenschaften nach dem Ausführen einer Anweisung wie z. B. die folgenden:

```SQL
exec sp_execute_external_script
       @language = N'R'
       , @script = N'
# Transform R version properties to data.frame
OutputDataSet <- data.frame(
  property_name = c("R.version", "Revo.version"), 
  property_value = c(R.Version()$version.string, Revo.version$version.string),
  stringsAsFactors = FALSE)
# Retrieve properties like R.home, libPath & default packages
OutputDataSet <- rbind(OutputDataSet, data.frame(
  property_name = c("R.home", "libPaths", "defaultPackages"),
  property_value = c(R.home(), .libPaths(), paste(getOption("defaultPackages"), collapse=", ")),
  stringsAsFactors = FALSE)
)
'
WITH RESULT SETS ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));

```

> [!TIP] 
> Wenn R Services nicht funktioniert, versuchen Sie, "rgui.exe" nur der Teil der R-Skript ausführen.

Öffnen Sie als letzte Möglichkeit Dateien auf dem Server, um die installierte Version zu bestimmen. Suchen Sie hierzu die rlauncher.config-Datei, um den Speicherort des R-Laufzeitmoduls und das aktuelle Arbeitsverzeichnis abzurufen. Es wird empfohlen, und öffnen eine Kopie der Datei, sodass Sie nicht versehentlich alle Eigenschaften ändern.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Um den R-Version und einer "revoscaler" Versionen erhalten, öffnen Sie eine R-Eingabeaufforderung, oder öffnen Sie die "rgui.exe", die mit der Instanz verknüpft ist.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`


Die R-Konsole zeigt die Versionsinformationen auf Start. Die folgende Version stellt beispielsweise die Standardkonfiguration für SQL Server 2017 CTP 2.0:

    *Microsoft R Open 3.3.3*
    
    *The enhanced R distribution from Microsoft*
    
    *Microsoft packages Copyright (C) 2017 Microsoft*
    
    *Loading Microsoft R Server packages, version 9.1.0.*


## <a name="python-versions"></a>Python-Versionen

Es gibt mehrere Möglichkeiten, die Python-Version zu erhalten. Die einfachste Möglichkeit ist zum Ausführen dieser Anweisung von Management Studio oder einem anderen Tool zur SQL-Abfrage:

```SQL
-- Get Python runtime properties:
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import sys
import pkg_resources
OutputDataSet = pandas.DataFrame(
                    {"property_name": ["Python.home", "Python.version", "Revo.version", "libpaths"],
                    "property_value": [sys.executable[:-10], sys.version, pkg_resources.get_distribution("revoscalepy").version, str(sys.path)]}
)
'
with WITH RESULT SETS (SQL keywords) ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));
```

Wenn der Machine Learning-Dienste nicht ausgeführt wird, können Sie die installierte Version von Python durch einen Blick auf die Datei pythonlauncher.config bestimmen. Es wird empfohlen, und öffnen eine Kopie der Datei, sodass Sie nicht versehentlich alle Eigenschaften ändern.

1. Nur SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config `
2. Rufen Sie den Wert für **PYTHONHOME**.
3. Ruft den Wert des aktuellen Arbeitsverzeichnisses.


> [!NOTE]
> Wenn Sie Python und R in SQL Server-2017 installiert haben, werden das Arbeitsverzeichnis und der Pool von Arbeitsthreads Konten für die R und Python-Sprachen freigegeben.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Mehrere Instanzen von R oder Python installiert?

Überprüfen Sie, ob mehr als eine Kopie der R-Bibliotheken auf dem Computer installiert ist. Diese Duplizierung möglich, wenn:

* Während der Installation wählen Sie R Services (Datenbankintern) und R-Server (eigenständig). 
* Microsoft R-Client zusätzlich zu SQL Server installiert.
* Ein anderen Satz von R-Bibliotheken wurde mithilfe von R-Tools für Visual Studio, R Studio, Microsoft R-Client oder ein anderes R-IDE installiert.
* Der Computer hostet, mehrere Instanzen von SQL Server und mehr als eine Instanz verwendet Machine Learning.

Die Bedingungen gelten für Python.

Wenn Sie feststellen, dass mehrere Bibliotheken oder Laufzeiten installiert sind, stellen Sie sicher, dass Sie erhalten nur die Fehler im Zusammenhang mit dem Python oder R-Laufzeiten, die von der SQL Server-Instanz verwendet werden.

## <a name="origin-of-errors"></a>Der Ursprung von Fehlern

Die Fehler, die angezeigt werden, wenn Sie versuchen, R-Code ausführen können von einem beliebigen der folgenden Quellen stammen:

- SQL Server-Datenbankmodul, einschließlich der gespeicherten Prozedur sp_execute_external_script
- SQLServer vertrauenswürdige Launchpad 
- Andere Komponenten von Extensibility Framework, einschließlich R und Python Startprogramme und Satelliten-Prozesse
- Anbieter, wie z. B. Microsoft Open Database Connectivity (ODBC)
- Sprache "R"

Wenn Sie mit dem Dienst zum ersten Mal arbeiten, kann es schwierig sein mitteilen, welche Dienste welche Nachrichten stammen. Es wird empfohlen, dass Sie nicht nur den genauen Meldungstext, sondern auch den Kontext, in dem Sie die Nachricht gesehen haben, erfassen. Beachten Sie die Clientsoftware, die Sie zum Ausführen von Machine Learning-Code verwenden:

- Verwenden Sie Management Studio? Eine externe Anwendung?
- Sind Sie R-Code in einem Remoteclient oder direkt in einer gespeicherten Prozedur ausführen?

## <a name="sql-server-log-files"></a>SQL Server-Protokolldateien

Abrufen der neuesten SQL Server-Fehlerprotokoll. Der vollständige Satz von Fehlerprotokollen besteht aus den Dateien aus dem folgenden Standardverzeichnis für Protokolldateien:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE] 
> Der genauen Ordnernamen unterscheidet sich je nach den Namen der Instanz.


## <a name="errors-returned-by-spexecuteexternalscript"></a>Sp_execute_external_script zurückgegebene Fehler

Erhalten Sie den vollständigen Text von Fehlern, die zurückgegeben werden, sofern vorhanden, ein, wenn Sie den Sp_execute_external_script-Befehl ausführen. 

Um Probleme mit R oder Python Zielmodell zu entfernen, können Sie dieses Skript ausführen, startet die R oder Python-Laufzeit und übergibt Daten hin und her.

**Für R**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Für Python**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

## <a name="errors-generated-by-the-extensibility-framework"></a>Fehler, die durch das Extensibility Framework generiert werden.

SQL Server generiert separate Protokolldateien für die Laufzeiten des externen Skripts Sprache. Diese Fehler werden nicht von der Python oder R-Sprache generiert. Sie sind von den Erweiterungskomponenten in SQL Server, einschließlich sprachspezifische Startprogramme und deren Satelliten-Prozesse generiert.

Sie können diese Protokolle die folgenden Standardspeicherorte abrufen:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog `

> [!NOTE] 
> Der genauen Ordnernamen unterscheidet sich basierend auf den Namen der Instanz. Abhängig von Ihrer Konfiguration möglicherweise der Ordner auf einem anderen Laufwerk.

Beispielsweise sind die folgenden protokollmeldungen mit dem Extensibility Framework verknüpft:

* *Fehler bei der LogonUser für Benutzer MSSQLSERVER01*
  
  Dies kann darauf hinweisen, dass der Worker-Konten, die Ausführung externer Skripts, die die Instanz zugreifen können.

* *Fehler bei InitializePhysicalUsersPool* 
  
  Diese Meldung bedeutet möglicherweise, dass Ihre Sicherheitseinstellungen daran hindern, Setup Erstellen des Pools von Worker-Konten, die zum Ausführen externer Skripts, die erforderlich sind.

* *Fehler bei der Initialisierung Kontext Sicherheitsmanager* 

* *Fehler bei der Initialisierung von Satelliten-Sitzungs-Manager*

## <a name="system-events"></a>Systemereignisse

1. Öffnen Sie Windows-Ereignisanzeige, und suchen Sie die **Systemereignis** Protokoll für Nachrichten, die die Zeichenfolge enthalten *Launchpad*. 
2. Öffnen Sie die Datei ExtLaunchErrorlog, und suchen Sie nach der Zeichenfolge *ErrorCode*. Überprüfen Sie die Meldung, die den ErrorCode zugeordnet ist.

Beispielsweise sind die folgenden Meldungen allgemeine Fehler im Dateisystem, die auf dem SQL Server-Erweiterungsframework beziehen: 

* *Der SQL Server Launchpad (MSSQLSERVER)-Dienst konnte wegen des folgenden Fehlers nicht gestartet:  <text>*

* *Der Dienst hat nicht auf die Start- oder Anforderung rechtzeitig reagiert.* 

* *Das Zeitlimit wurde (120000 Millisekunden) erreicht, während des Wartens auf des Diensts SQL Server Launchpad (MSSQLSERVER) eine Verbindung herstellen.* 

## <a name="dump-files"></a>Dumpdateien

Wenn Sie über fundierte Kenntnisse Debuggen sind, können Sie die Dumpdateien, einen Fehler im Launchpad analysieren.

1. Suchen Sie den Ordner, der die bootstrap-Setup-Protokollen für SQL Server enthält. In SQL Server 2016 wurde z. B. der Standardpfad c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\130\Setup Bootstrap\Log an.
2. Öffnen Sie den bootstrap protokollunterordner, der Erweiterbarkeit spezifisch sind.
3. Wenn Sie eine Supportanfrage übermitteln möchten, fügen Sie den gesamten Inhalt dieses Ordners in eine ZIP-Datei. Beispiel: c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog.
  
Der genaue Speicherort auf Ihrem System unterscheiden, und es möglicherweise auf einem anderen Laufwerk als dem Laufwerk C:. Achten Sie darauf, dass Sie die Protokolle für die Instanz abgerufen werden, auf Machine Learning installiert ist. 


## <a name="configuration-settings"></a>Konfigurationseinstellungen

Dieser Abschnitt enthält weitere Komponenten oder Anbieter, die eine Quelle von Fehlern werden können, wenn Sie R oder Python-Skripts ausführen.

### <a name="what-network-protocols-are-available"></a>Welche Netzwerkprotokolle sind verfügbar?

Machine Learning Services erfordert die folgenden Netzwerkprotokolle aus, für die interne Kommunikation zwischen Erweiterbarkeitskomponenten und für die Kommunikation mit externen R oder Python-Clients.

* Named Pipes
* TCP/IP

Öffnen Sie SQL Server Configuration Manager, um zu bestimmen, ob ein Protokoll installiert ist und, sofern es installiert ist, um zu bestimmen, ob es aktiviert ist.

### <a name="security-configuration-and-permissions"></a>Konfiguration der Sicherheit und Berechtigungen

Für Konten:

1. Öffnen Sie in der Systemsteuerung **Benutzer und Gruppen**, und suchen Sie die Gruppe verwendet, um externe Skripts für Aufträge auszuführen. Standardmäßig ist die Gruppe **SQLRUserGroup**.
2. Stellen Sie sicher, dass die Gruppe vorhanden ist und sie mindestens eine workerkonto enthält.
3. Wählen Sie in SQL Server Management Studio die Instanz, auf dem R oder Python Aufträge durchgeführt werden, wählen Sie **Sicherheit**, und überprüfen Sie, ob eine Anmeldung für SQLRUserGroup vorhanden ist.
4. Überprüfen Sie Berechtigungen für die Benutzergruppe aus.

Für einzelne Benutzerkonten:

1. Bestimmen Sie, ob die Instanz Authentifizierung im gemischten Modus, nur die SQL-Anmeldungen oder nur die Windows-Authentifizierung unterstützt. Diese Einstellung wirkt sich auf Ihre R oder Python-code Anforderungen.
2. Bestimmen Sie für jeden Benutzer, die R-Code ausgeführt werden muss, die erforderlichen Berechtigungen für jede Datenbank, in denen Objekte werden aus R geschrieben werden, werden auf Daten zugegriffen werden oder Objekte erstellt werden.
3. Um die Ausführung des Skripts zu aktivieren, Erstellen von Rollen oder Hinzufügen von Benutzern zu den folgenden Rollen nach Bedarf:

   - Alle außer *Db_owner*: erfordern EXECUTE ANY EXTERNAL SCRIPT.
   - *Db_datawriter*: um Ergebnisse aus R oder Python zu schreiben. 
   - *Db_ddladmin*: zum Erstellen neuer Objekte. 
   - *"db_datareader"*: zum Lesen von Daten, die von R oder Python-Code verwendet wird. 
4. Beachten Sie, ob Sie alle Standard-Startkonten geändert haben, bei der Installation von SQL Server 2016.
5. Wenn ein Benutzer muss neue R-Pakete installieren, oder verwenden Sie R-Pakete, die von anderen Benutzern installiert wurden, müssen Sie möglicherweise paketverwaltung für die Instanz aktivieren und dann zusätzliche Berechtigungen zuzuweisen. Weitere Informationen finden Sie unter [aktivieren oder Deaktivieren von R-paketverwaltung](r\r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Welche Ordnern unterliegen durch Antivirensoftware Sperren?

Antivirus-Software kann Ordner sperren, die verhindert, dass sowohl der Einrichtung des Machine learning-Funktionen und die skriptausführung erfolgreich. Bestimmen Sie, ob alle Ordner in der SQL Server-Struktur Virenscan unterliegen.

Wenn mehrere Dienste oder Funktionen in einer Instanz installiert werden, kann es jedoch schwierig, alle möglichen Ordner aufgelistet, die von der Instanz verwendet werden. Z. B. wenn neue Funktionen hinzugefügt werden, der neue Ordner müssen identifiziert und ausgeschlossen werden.

Darüber hinaus erstellen einige Funktionen neuer Ordner dynamisch zur Laufzeit. Beispielsweise wird mit in-Memory-OLTP-Tabellen, gespeicherte Prozeduren und Funktionen neue Verzeichnisse zur Laufzeit erstellen. Diese Ordnernamen häufig GUIDs enthalten und können nicht vorhergesagt werden. Die SQL Server vertrauenswürdige Launchpad erstellt neue Arbeitsverzeichnisse für R und Python script Aufträge.

Da es möglicherweise nicht möglich, alle Ordner ausschließen, die von den SQL Server-Prozess und dessen Funktionen benötigt werden, wird empfohlen, dass Sie die gesamte Verzeichnisstruktur der SQL Server-Instanz ausschließen.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Ist die Firewall für SQL Server öffnen? Unterstützt die Instanz Remoteverbindungen?

1. Um zu bestimmen, ob SQL Server Remoteverbindungen unterstützt, finden Sie unter [konfigurieren Remoteserververbindungen](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Bestimmen Sie, ob eine Firewallregel für SQL Server erstellt wurde. Aus Sicherheitsgründen in einer Standardinstallation möglicherweise es nicht möglich, dass remote R oder Python-Client eine Verbindung mit der Instanz herstellen. Weitere Informationen finden Sie unter [Problembehandlung Herstellen einer Verbindung mit SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).


## <a name="see-also"></a>Siehe auch

[Problembehandlung bei Machine Learning in der SQL Server](machine-learning-troubleshooting-faq.md)
