---
title: Installieren Sie neue Python-Pakete auf SQL Server-Machine Learning | Microsoft Docs
description: Hinzufügen von neuen Python-Pakete zu SQL Server 2017 Machine Learning Services (Datenbankintern) und Machine Learning-Server (eigenständig)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 77cc91c4d0a9fbe339e92705a71a3a8642de5563
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="install-new-python-packages-on-sql-server"></a>Installieren Sie neue Python-Pakete unter SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt, wie neue Python-Pakete auf einer Instanz von SQL Server 2017 Machine Learning Services zu installieren. Im Allgemeinen ist der Prozess für die Installation der neuen Pakete in einer standardumgebung Python vergleichbar. Allerdings sind einige zusätzliche Schritte erforderlich, wenn der Server nicht über eine Internetverbindung verfügt.

Um Hilfe zu erhalten, die eng zusammenliegen, in dem Pakete installiert sind, oder die Pakete installiert sind, finden Sie unter [R abrufen oder Python-Paketinformationen](../r/determine-which-packages-are-installed-on-sql-server.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

+ Sie müssen SQL Server 2017 Machine Learning Services (Datenbankintern) mit der Python-Sprachoption installiert haben. Anweisungen hierzu finden Sie unter [installieren Sie SQL Server 2017 Machine Learning Services (Datenbankintern)](../install/sql-machine-learning-services-windows-install.md).

+ Für jede Instanz des Servers müssen Sie eine separate Kopie des Pakets installieren. Pakete können nicht über Instanzen freigegeben werden.

+ Pakete muss ein Python-3.5 kompatibel und Ausführung unter Windows. 

+ Bewerten Sie, ob das Paket für die Verwendung in SQL Server-Umgebung geeignet ist. In der Regel ein Datenbankserver unterstützt wird, mehrere Dienste und Anwendungen und Ressourcen auf dem Dateisystem möglicherweise eingeschränkt, als auch Verbindungen mit dem Server. In vielen Fällen wird der Zugriff auf das Internet vollständig blockiert.

    Andere allgemeine Probleme umfassen die Verwendung von Netzwerkfunktionen, der blockiert ist, auf dem Server oder durch die Firewall oder die Pakete mit Abhängigkeiten, die auf einem Windows-Computer nicht installiert werden. 

    Einige beliebten Python-Pakete (z. B. Kolben) Aufgaben wie Webentwicklung, die in einer eigenständigen Umgebung besser ausgeführt. Es wird empfohlen, dass Sie in der Datenbank Python für Aufgaben wie das Machine Learning, die erfordern intensiver Datenverarbeitung, die enge Integration mit dem Datenbankmodul profitieren, sondern einfach Abfragen der Datenbank verwenden.

+ Administratorzugriff auf dem Server ist erforderlich, um Pakete zu installieren.

## <a name="add-a-new-python-package"></a>Fügen Sie ein neues Python-Paket hinzu

In diesem Beispiel wird davon ausgegangen, dass Sie ein neues Paket direkt auf dem SQL Server-Computer installieren möchten.

Das Paket installiert, die in diesem Beispiel ist [CNTK](https://docs.microsoft.com/cognitive-toolkit/), ein Framework zum umfassenden lernen von Microsoft, die Anpassung unterstützt Trainings- und Freigabe von verschiedenen Arten von neuronalen Netzwerken.

> [!TIP]
> Benötigen Sie Hilfe beim Konfigurieren der Python-Tools an? Finden Sie in folgenden Blogs:
> 
> [Erste Schritte mit Python-Webdienste, die mithilfe von Machine Learning-Server](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)
> 
> [David Crook: Cognitive Microsoft-Toolkit + VS-Code](http://dacrook.com/cntk-vs-code-awesome/)

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Schritt 1: Die Windows-Version von Python-Paket herunterladen

+ Bei der Installation von Python-Pakete auf einem Server ohne Internetzugang müssen Sie die WHL-Datei auf einen anderen Computer herunterladen und kopieren es auf den Server.

    Z. B. auf einem separaten Computer, Sie können die WHL Datei herunterladen von diesem Standort [ https://cntk.ai/PythonWheel/CPU-Only ](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl), und kopieren Sie die Datei `cntk-2.1-cp35-cp35m-win_amd64.whl` in einen lokalen Ordner auf dem SQL Server-Computer.

+ SQL Server-2017 verwendet Python 3.5. 

> [!IMPORTANT]
> Stellen Sie sicher, dass die Windows-Version des Pakets zu erhalten. Wenn die Datei auf .gz endet, ist es wahrscheinlich nicht die richtige Version.

Diese Seite enthält Downloads für mehrere Plattformen und für mehrere Versionen der Python: [CNTK einrichten](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Schritt 2: Öffnen Sie eine Python-Eingabeaufforderung

Suchen Sie nach der Python-Bibliothek Standardspeicherort von SQL Server verwendet. Wenn Sie mehrere Instanzen installiert haben, suchen Sie den PYTHON_SERVICE-Ordner für die Instanz, in dem Sie das Paket hinzufügen möchten.

Z. B. wenn Machine Learning-Dienste mithilfe der Standardwerte installiert wurde, und Machine Learning auf der Standardinstanz aktiviert ist, wäre der Pfad folgendermaßen:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Öffnen Sie die Python-Eingabeaufforderung, die der Instanz zugeordnet.

> [!TIP]
> Für zukünftige Debuggen und testen, empfiehlt es sich um Python Einrichten einer Umgebung für die Bibliothek Instanz spezifisch.

### <a name="step-3-install-the-package-using-pip"></a>Schritt 3: Installieren Sie das Paket, die Verwendung von pip

+ Wenn Sie mit der über die Befehlszeile Python vertraut sind, verwenden Sie zum Installieren der neuen Pakete PIP.exe. Sie finden die **Pip** Installer in die `Scripts` Unterordner. 

  SQL Server-Setup fügt dem Systempfad keine Skripts hinzu. Wenn Sie eine Fehlermeldung erhalten `pip` wird nicht erkannt als ein interner oder externer Befehl können Sie den Ordner "Skripts" der PATH-Variablen in Windows hinzufügen.

  Den vollständigen Pfad der **Skripts** Ordner in einer Standardinstallation lautet wie folgt:

    C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

+ Wenn Sie Visual Studio 2017 oder Visual Studio 2015 mit den Python-Erweiterungen verwenden, können Sie ausführen `pip install` aus der **Python-Umgebungen** Fenster. Klicken Sie auf **Pakete**, und geben Sie im Textfeld den Namen oder Speicherort des zu installierenden Pakets an. Sie brauchen geben `pip install`; es wird für Sie automatisch ausgefüllt. 

    - Wenn der Computer über Internetzugriff verfügt, geben Sie den Namen des Pakets oder die URL für ein bestimmtes Paket und eine Version aus. 
    
    Um die Version des CNTK installieren, die für Windows und Python 3.5 unterstützt wird, geben Sie z. B. die Download-URL: `https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Wenn der Computer nicht über Internetzugriff verfügt, müssen Sie die Datei WHL vor der Installation herunterladen. Geben Sie dann den lokalen Pfad und den Namen ein. Fügen Sie beispielsweise den folgenden Pfad und Dateinamen zum Installieren der WHL-Datei, die von der Website heruntergeladen: `"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Sie möglicherweise aufgefordert, die zum Erhöhen der Berechtigungen, um die Installation abzuschließen.

Im Verlauf der Installation können Sie statusmeldungen in das Eingabeaufforderungsfenster sehen:

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```


### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>Schritt 4. Laden Sie das Paket oder seine Funktionen als Teil des Skripts

Wenn die Installation abgeschlossen ist, können Sie sofort beginnen, verwenden das Paket aus, wie im nächsten Schritt beschrieben.

Beispiele für umfassenden Lernen mit CNTK, finden Sie diese Lernprogramme: [Python-API für CNTK](https://cntk.ai/pythondocs/tutorials.html)

Um Funktionen aus dem Paket in Ihr Skript zu verwenden, fügen Sie den Standard `import <package_name>` -Anweisung in der ersten Zeile des Skripts:

```python
import numpy as np
import cntk as cntk
cntk._version_
```

##  <a name="how-to-view-installed-packages-using-conda"></a>Zum Anzeigen der installierten Pakete mit conda

Es gibt verschiedene Möglichkeiten, die Sie eine Liste der installierten Pakete abrufen können. Sie können z. B. Anzeigen der installierten Pakete in der **Python-Umgebungen** Visual Studio-Fenster.

Wenn Sie die Python-Befehlszeile verwenden, können Sie mithilfe der **Conda** Paket-Manager, der mit der Python Anaconda-Umgebung hinzugefügt, die von SQL Server-Setup enthalten ist.

Vorausgesetzt, dass Sie den Ordner "Skripts" der PATH-Umgebungsvariable hinzugefügt, führen Sie diesen Befehl in eine Administratorbefehlszeile, die Pakete in Ihrer Umgebung Python aufzulisten.

```python
conda list
```

Weitere Informationen zu **Conda** und wie Sie es verwenden können zum Erstellen und Verwalten von mehreren Python-Umgebungen finden Sie unter [Verwaltung von Umgebungen mit Conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).
