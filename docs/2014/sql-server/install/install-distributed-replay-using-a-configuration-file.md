---
title: Installieren von Distributed Replay mithilfe einer Konfigurationsdatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 3259232c-6963-4c9c-9d10-ae42aa262eef
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a1ba661a0a00931f52aa7d38cc8d96730c685fa7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078311"
---
# <a name="install-distributed-replay-using-a-configuration-file"></a>Installieren von Distributed Replay mithilfe einer Konfigurationsdatei
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup bietet die Möglichkeit, eine Konfigurationsdatei auf der Grundlage von Benutzereingaben und Systemstandards zu generieren. Wenn Sie angeben, dass die Verwaltungstools installiert werden sollen, können Sie mithilfe der Konfigurationsdatei die drei Distributed Replay-Komponenten bereitstellen (Verwaltungstool, Distributed Replay Controller und Distributed Replay Client). Unterstützt werden das Installieren, Reparieren und Deinstallieren der Distributed Replay-Komponenten.  
  
 Setup unterstützt die Verwendung der Konfigurationsdatei nur in der Befehlszeile. Die Verarbeitungsreihenfolge der Parameter während der Verwendung der Konfigurationsdatei wird im Folgenden erläutert:  
  
-   Die Konfigurationsdatei überschreibt die Standards in einem Paket  
  
-   Befehlszeilenwerte überschreiben die Werte in der Konfigurationsdatei  
  
 Weitere Informationen dazu, wie Sie mithilfe einer Konfigurationsdatei finden Sie unter [Installieren von SQL Server 2014 mithilfe einer Konfigurationsdatei](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).  
  
> [!IMPORTANT]  
>  Nachdem Sie Distributed Replay installiert haben, müssen Sie auf dem Controller und den Clientcomputern Firewallregeln erstellen und jedem Clientcomputer Berechtigungen für den Zielserver gewähren. Weitere Informationen finden Sie unter [Ausführen der Schritte nach der Installation](../../tools/distributed-replay/complete-the-post-installation-steps.md).  
  
### <a name="to-generate-a-configuration-file"></a>So generieren Sie eine Konfigurationsdatei  
  
1.  Befolgen Sie die Anweisungen des Setup-Assistenten bis zur Seite **Installationsbereit** . Der Pfad zur Konfigurationsdatei wird auf der Seite **Installationsbereit** im Abschnitt mit dem Konfigurationsdateipfad angegeben.  
  
2.  Brechen Sie das Setupprogramm ab, ohne dabei die Installation abzuschließen, um die INI-Datei zu generieren.  
  
### <a name="to-install-distributed-replay-using-the-configuration-file"></a>So installieren Sie Distributed Replay mithilfe der Konfigurationsdatei  
  
-   Führen Sie die Installation an der Eingabeaufforderung aus, und geben Sie die Datei ConfigurationFile.ini mit dem ConfigurationFile-Parameter an.  
  
 **Beispielsyntax**  
  
 Im Folgenden finden Sie ein Beispiel zum Angeben der Konfigurationsdatei an der Eingabeaufforderung:  
  
```  
Setup.exe /CTLRSVCPASSWORD="ctlrsvcpswd" /CLTSVCPASSWORD="cltsvcpswd" / ConfigurationFile=ConfigurationFile.INI\  
```  
  
> [!NOTE]  
>  Sie müssen beide Kennwörter in der Befehlszeile angeben, da Sie diese nicht in der Konfigurationsdatei konfigurieren können.  
  
  
