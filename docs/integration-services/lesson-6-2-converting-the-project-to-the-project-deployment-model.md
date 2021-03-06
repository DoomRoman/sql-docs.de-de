---
title: 'Schritt 2: Konvertieren des Projekts in das Projektbereitstellungsmodell | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ce29d9e39b2abd46845a035183e6dee80f6c7236
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767708"
---
# <a name="lesson-6-2---converting-the-project-to-the-project-deployment-model"></a>Lektion 6-2: Konvertieren des Projekts in das Projektbereitstellungsmodell
In dieser Aufgabe verwenden Sie den Konvertierungs-Assistenten von Integration Services-Projekt, um das Projekt in das Projektbereitstellungsmodell zu konvertieren.  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a>Konvertieren des Projekts in das Projektbereitstellungsmodell  
  
1.  Klicken Sie im Menü „Projekt“ auf „Paketbereitstellungsmodell konvertieren“.  
  
2.  Überprüfen Sie die Schritte der Konvertierungs-Assistent von Integration Services-Einführungsseite und klicken Sie auf Weiter.  
  
3.  Klicken Sie auf der Seite zur Paketauswahl in die Paketliste, deaktivieren Sie alle Kontrollkästchen außer Lektion 6.dtsx, und klicken Sie dann auf Weiter.  
  
4.  Klicken Sie auf der Projekteigenschaftenseite auf Weiter.  
  
5.  Klicken Sie auf der Seite Task 'Paket ausführen' aktualisieren auf Weiter.  
  
6.  Stellen Sie auf auf der Konfigurationsauswahlseite sicher, dass das Paket Lektion 6.dtsx in der Konfigurationsliste ausgewählt ist, und klicken Sie auf Weiter.  
  
7.  Stellen Sie auf der Seite zum Erstellen von Parametern sicher, dass das Paket Lektion 6.dtsx ausgewählt ist, und der Bereich in der Konfigurationseigenschaftsliste auf Paket festgelegt ist, und klicken Sie dann auf Weiter.  
  
8.  Stellen Sie auf der Seite zur Konfiguration der Parameter sicher, dass die Werte für den Namen und den Wert demselben Namen und Wert entsprechen, den Sie in der Lektion 5 für den Variablen- und Konfigurationswert angegeben haben, und klicken Sie dann auf Weiter.  
  
9. Beachten Sie auf der Überprüfungsseite im Zusammenfassungsbereich, dass der Assistent die Informationen aus der Konfigurationsdatei verwendet hat, um die zu konvertierenden Eigenschaften festzulegen.  
  
10. Klicken Sie auf Konvertieren.  
  
    Beim Abschluss der Konvertierung einer Nachricht wird eine Warnung angezeigt, das die Änderungen nicht gespeichert werden, bis das Projekt in Visual Studio gespeichert wird. Klicken Sie im Warnungsdialogfeld auf OK.  
  
11. Klicken Sie im Konvertierungs-Assistenten des Integration Services-Projekts auf Schließen.  
  
12. Klicken Sie in SQL Server Data Tools auf das Menü "Datei", klicken Sie auf "Speichern", um das konvertierte Paket zu speichern.  
  
13. Klicken Sie auf der Registerkarte "Parameter", und stellen Sie sicher, dass das Paket jetzt einen Parameter für VarFolderName enthält und der Wert denselben Pfad für den Ordner der neuen Beispieldaten aus der Lektion 5-Konfigurationsdatei angegeben ist.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
[Schritt 3: Testen des Pakets aus Lektion 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
  
  
