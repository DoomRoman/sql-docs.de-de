---
title: Herunterladen und Installieren von Azure Data Studio | Microsoft-Dokumentation
description: Herunterladen und installieren Sie Azure Data Studio für Windows, MacOS oder Linux
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88b79feb3b04dcc7f872653b2e24a9f70c370f57
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038431"
---
# <a name="download-and-install-azure-data-studio"></a>Herunterladen und Installieren von Azure Data Studio

[!INCLUDE[name-sos](../includes/name-sos.md)] auf Windows, MacOS und Linux ausgeführt wird.

Herunterladen und installieren die neueste Version der *September GA-Version*:

> [!NOTE]
> Wenn Sie über SQL Operations Studio aktualisieren und Ihre Einstellungen, Tastenkombinationen in Visual Studio oder Codeausschnitte beibehalten möchten, finden Sie unter [verschieben benutzereinstellungen](#move-user-settings).

|Platform|Herunterladen|Veröffentlichungsdatum| Version |
|:---|:---|:---|:---|
|Windows|[Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2024683)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2024680)|24. September 2018 |1,0|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2024677)|24. September 2018 |1,0|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2024668)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2024672)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2024675)|24. September 2018 |1,0|

Weitere Informationen über die neueste Version finden Sie unter den [Anmerkungen zu dieser Version](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Azure Data-Studio für Windows herunterladen

Diese Version von [!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält eine standardmäßige Windows Installer-Erfahrung und ZIP-Datei: 

**Installationsprogramm**

1. Herunterladen und Ausführen der [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] Installer für Windows](https://go.microsoft.com/fwlink/?linkid=2024683).
1. Starten Sie den [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] app.


**ZIP-Datei**

1. Herunterladen [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP für Windows](https://go.microsoft.com/fwlink/?linkid=2024680).
2. Suchen Sie die heruntergeladene Datei, und extrahieren Sie sie.
3. Ausführen von `\azuredatastudio-windows\azuredatastudio.exe`


## <a name="get-azure-data-studio-for-macos"></a>Abrufen von Azure Data Studio für macOS

1. Herunterladen [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] für MacOS](https://go.microsoft.com/fwlink/?linkid=2024677).
2. Doppelklicken Sie darauf, um den Inhalt der ZIP-Datei zu erweitern.
3. Vornehmen [!INCLUDE[name-sos](../includes/name-sos-short.md)] zur Verfügung, in der *Launchpad*, ziehen Sie *Azure Daten Studio.app* auf die *Anwendungen* Ordner.


## <a name="get-azure-data-studio-for-linux"></a>Azure Data-Studio für Linux herunterladen

1. Herunterladen [!INCLUDE[name-sos](../includes/name-sos-short.md)] für Linux mithilfe eines der Installationsprogramme oder das Archiv für die ".TAR.gz":
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2024668)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2024672)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2024675)
1. Extrahieren Sie die Datei, und starten Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], öffnen Sie ein neues Terminalfenster, und geben Sie die folgenden Befehle:

   **Debian-Installation:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **u/Min Installation:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **.tar.gz Installation:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > Für Debian, Red hat und Ubuntu müssen Sie möglicherweise fehlende Abhängigkeiten. Verwenden Sie die folgenden Befehle aus, um diese Abhängigkeiten abhängig von Ihrer Version von Linux zu installieren:
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-azure-data-studio"></a>Deinstallieren Sie Azure Data Studio

Wenn Sie installiert [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit dem Windows-Installer, deinstallieren Sie die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie installiert [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit ZIP-Datei oder andere archivieren, löschen Sie anschließend einfach die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

[!INCLUDE[name-sos](../includes/name-sos-short.md)] unter Windows, MacOS und Linux ausgeführt wird, und wird auf folgenden Plattformen unterstützt:

### <a name="windows"></a>Windows
- Windows 10 (64-Bit)
- Windows 8.1 (64-Bit)
- Windows 8 (64-Bit)
- Erfordert Windows 7 (SP1) (64-Bit) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64-Bit)
- Windows Server 2012 (64-Bit)
- Windows Server 2008 R2 (64-Bit)

### <a name="macos"></a>macOS
- MacOS 10.13 High Sierra
- MacOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Nach Updates suchen
Um die neuesten Updates zu überprüfen, klicken Sie auf das Zahnradsymbol unten links des Fensters, und klicken Sie auf **nach Updates suchen**

## <a name="move-user-settings"></a>Verschieben von benutzereinstellungen

Wenn Sie Ihre benutzerdefinierten Einstellungen, Tastenkombinationen in Visual Studio oder Codeausschnitte verschieben möchten, führen Sie die folgenden Schritte aus. Dies ist wichtig, wenn Sie SQL Operations Studio-Version auf Azure Data Studio aktualisieren.

*Wenn Sie bereits über Azure Data Studio verfügen oder Sie nicht installiert oder SQL Operations Studio angepasst haben, können Sie diesen Abschnitt ignorieren.*


1. Öffnen Sie Einstellungen, indem Sie auf das Zahnradsymbol auf der linken unteren und auf **Einstellungen.**

   ![Open-Einstellungen](./media/download/open-settings.png)

2. Mit der rechten Maustaste die **Benutzereinstellungen** Registerkarte im Vordergrund, und klicken Sie auf **im Explorer anzeigen**

   ![Anzeigen-in-explorer](./media/download/reveal-in-explorer.png)

3. Kopieren Sie alle Dateien in diesem Ordner, und speichern Sie in einem übersichtlichen Ort auf dem lokalen Laufwerk, z. B. Ihren Dokumentordner finden.

   ![Einstellungen kopieren](./media/download/copy-settings.png)

4. Führen Sie die Schritte, die 1-2, wählen Sie unter Schritt 3 Fügen Sie den Inhalt, die Sie gespeichert, aufgerufen werden, in den Ordner, in Ihrer neuen Version von Azure Data Studio. Sie können auch manuell über die Einstellungen, Keybindings oder Codeausschnitte in ihren entsprechenden Speicherorten kopieren.


## <a name="next-steps"></a>Nächste Schritte

Finden Sie in der folgenden schnellstartanleitungen für den Einstieg:
- [Verbinden und Abfragen von SQLServer](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Verbinden und Abfragen von Azure Datawarehouse](quickstart-sql-dw.md)

Mitwirken an [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio) 

[Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839) und [Sammlung von Verwendungsdaten](usage-data-collection.md).
