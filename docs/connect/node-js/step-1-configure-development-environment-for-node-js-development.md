---
title: 'Schritt 1: Konfigurieren der Entwicklungsumgebung für die Entwicklung von Node.js | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f918eead7fb0af9d28cd85b173e3e076c5ba9416
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288959"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für Node.js-Entwicklung
Sie müssen Ihre Entwicklungsumgebung mit den Voraussetzungen zu konfigurieren, um die Entwicklung einer Anwendung mithilfe der Node.js-Treiber für SQL Server.  Die häufigste Methode ist die Verwendung den Knoten-Paket-Manager (Npm) das mühsame-Modul installieren, jedoch mühsam Moduls direkt zum download [Github](https://github.com/pekim/tedious) Falls gewünscht.  
  
Beachten Sie, dass der Treiber für Node.js TDS-Protokolls, die standardmäßig in SQL Server und Azure SQL-Datenbank aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
## <a name="windows"></a>Windows  
  
1. **Node.js-Laufzeit und Npm-Paket-Manager installieren**  
A. Wechseln Sie zu [Node.js](https://nodejs.org/en/download/)  
B. Klicken Sie auf den entsprechenden Windows Installer-Msi-Link.   
c. Nachdem das Download abgeschlossen ist, führen Sie die MSI-Datei zum Installieren von Node.js  
  
2. **Öffnen von cmd.exe**  
  
3. **Erstellen Sie ein Projektverzeichnis** , und navigieren Sie zu.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Erstellen Sie eine Knoten-Projekt.**  Um während der projekterstellung die Standardeinstellungen beibehalten möchten, drücken Sie die EINGABETASTE, bis das Projekt erstellt wurde. Am Ende dieses Schritts sehen Sie eine Datei für "Package.JSON" im Projektverzeichnis.  
```  
> npm init  
```  
  
5. **Installieren Sie mühsam-Modul in Ihrem Projekt ein.**  Dies ist die Implementierung des TDS-Protokolls, die der Treiber verwendet wird, um die Kommunikation mit SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Geöffneten Terminaldienste**  
  
2. **Installieren Sie Node.js-Laufzeit**  
```  
>sudo apt-get install node  
```  
3. **Installieren Sie Npm (Knoten der Paket-Manager)**  
```  
> sudo apt-get install npm  
```  
4. **Erstellen Sie ein Projektverzeichnis** , und navigieren Sie zu.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Erstellen Sie eine Knoten-Projekt.**  Um während der projekterstellung die Standardeinstellungen beibehalten möchten, drücken Sie die EINGABETASTE, bis das Projekt erstellt wurde. Am Ende dieses Schritts sehen Sie eine Datei für "Package.JSON" im Projektverzeichnis.  
```  
> sudo npm init  
```  
  
6. **Installieren Sie mühsam-Modul in Ihrem Projekt ein.**  Dies ist die Implementierung des TDS-Protokolls, die der Treiber verwendet wird, um die Kommunikation mit SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Node.js-Laufzeit und Npm-Paket-Manager installieren**  
A. Wechseln Sie zu [Node.js](https://nodejs.org/en/download/)  
B. Klicken Sie auf den entsprechenden Link für die Mac OS-Installer.  
c. Nachdem das Download abgeschlossen ist, führen Sie die Dmg zum Installieren von Node.js  
  
2. **Geöffneten Terminaldienste**  
  
3. **Erstellen Sie ein Projektverzeichnis** , und navigieren Sie zu.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Erstellen Sie eine Knoten-Projekt.**  Um während der projekterstellung die Standardeinstellungen beibehalten möchten, drücken Sie die EINGABETASTE, bis das Projekt erstellt wurde. Am Ende dieses Schritts sehen Sie eine Datei für "Package.JSON" im Projektverzeichnis.  
```  
> npm init  
```  
  
5. **Installieren Sie mühsam-Modul in Ihrem Projekt ein.**  Dies ist die Implementierung des TDS-Protokolls, die der Treiber verwendet wird, um die Kommunikation mit SQL Server.  
```  
> npm install tedious  
```  
  
