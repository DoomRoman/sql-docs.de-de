---
title: Die Ressourcenkontrolle für Machine Learning in SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: abe130ef7e465326999e0c71ce01e88dfa6269a3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31202462"
---
# <a name="resource-governance-for-machine-learning-in-sql-server"></a>Die Ressourcenkontrolle für Machine Learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel bietet einen Überblick über die Ressourcenkontrolle Funktionen in SQL Server, mit deren Hilfe reservieren und Ausgleichen von R und Python-Skripts verwendete Ressourcen.

**Gilt für:** [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)]
[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] und [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]

## <a name="goals-of-resource-governance-for-machine-learning"></a>Ziele für die Ressourcenkontrolle für Machine learning

Eine bekannte Schwachstelle mit Machine Learning-Sprachen wie z. B. R und Python ist, dass die Daten auf Computern, die nicht von kontrolliert werden häufig außerhalb der Datenbank verschoben werden IT. Ein anderes ist, dass "R" steht Singlethread, was bedeutet, dass Sie nur mit den Daten im Arbeitsspeicher verfügbar arbeiten können. 

SQL Server-Machine Learning-Services entfällt beide Probleme, und hilft bei der Einhaltung Unternehmen Compliance-Anforderungen. Erweiterte Analysen in der Datenbank behält, und eine höhere Leistung großer Datasets über Funktionen, z. B. streaming und Segmentierung Vorgänge unterstützt. Verschieben von R und Python-Berechnungen in den Datenbanken kann jedoch die Leistung anderer Dienste beeinträchtigen, die die Datenbank, einschließlich Benutzerabfragen regulären externe Anwendungen und-Datenbank geplante Aufträge verwenden.

Dieser Abschnitt enthält Informationen zum Verwalten von Ressourcen, die von externen Laufzeiten, z. B. R und Python verwendet, um die Auswirkungen auf andere Basisdienste für die Datenbank zu reduzieren. Eine Datenbank-Server-Umgebung ist in der Regel der Hub für mehrere abhängige Anwendungen und Dienste.

Sie können [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) zum Verwalten der Ressourcen, die von externen Laufzeiten für R und Python verwendet.  Für Machine Learning umfasst die Ressourcenkontrolle folgende Tasks:

+ Identifizieren von Skripts, die übermäßig viele Serverressourcen in Anspruch nehmen.
  
     Der Administrator muss in der Lage sein, Aufträge zu beenden oder einzuschränken, die zu viele Ressourcen in Anspruch nehmen.
  
+ Reduzieren unvorhersehbarer Arbeitsauslastungen.
  
     Wenn mehrere Machine Learning-Aufträge auf dem Server gleichzeitig ausgeführt werden, konnte der resultierende Ressourcenkonflikt beispielsweise dazu führen, dass unvorhersehbare Leistung oder bedrohen Abschluss der arbeitsauslastung. Wenn Ressourcenpools verwendet werden, können die Aufträge allerdings voneinander isoliert sein.
  
-   Priorisieren von Arbeitsauslastungen.
  
     Der Administrator oder der Architekt muss in der Lage, arbeitsauslastungen an, die müssen haben Vorrang vor, oder bestimmte arbeitsauslastungen beim Ressourcenkonflikt auf den Abschluss zu gewährleisten.

## <a name="how-to-use-resource-governor-to-manage-machine-learning"></a>Zum Verwenden der Ressourcenkontrolle zum Verwalten von Machine learning
 
Verwalten von Ressourcen, R oder Python-Sitzungen zugeordnet sind, durch das Erstellen einer *externen Ressourcenpool*, und der Pool oder Pools Arbeitslasten zuweisen. Ein externen Ressourcenpool ist ein neuer Ressourcenpool eingeführten [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] zur Verwaltung von R-Laufzeitumgebung und andere externe mit dem Datenbankmodul verarbeitet.

SQL Server unterstützt drei Arten von Standard-Ressourcenpools hinzu: 
  
-   Der *interne Pool* stellt die Ressourcen dar, die von SQL Server selbst verwendet werden, und kann nicht geändert oder eingeschränkt werden.
  
-   Der *Standardpool* ist ein vordefinierter Benutzerpool, den Sie verwenden können, um die Ressourcenverwendung für den Server als Ganzes zu ändern. Sie können auch Benutzergruppen definieren, die zu diesem Pool gehören, um den Zugriff auf Ressourcen zu verwalten.
  
-   Der *externe Standardpool* ist ein vordefinierter Benutzerpool für externe Ressourcen. Des Weiteren können Sie neue externe Ressourcenpools erstellen und Benutzergruppen definieren, die zu diesem Pool gehören.
  
 Darüber hinaus können Sie *benutzerdefinierte Ressourcenpools* erstellen, um Ressourcen dem Datenbankmodul oder anderen Anwendungen zuzuweisen, sowie *benutzerdefinierte externe Ressourcenpools* erstellen, um R und andere externe Prozesse zu verwalten.
  
 Eine gute Einführung in die Terminologie und allgemeinen Konzepte finden Sie unter [Ressourcenpool für die Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

  
## <a name="resource-management-walkthrough-with-resource-governor"></a>Ressource Management Exemplarische Vorgehensweise bei der Ressourcenkontrolle

Wenn Sie die Ressourcenkontrolle nicht vertraut sind, finden Sie in diesem Thema für eine kurze exemplarische Vorgehensweise zum Erstellen eines neuen externen Ressourcenpools und ändern die Standardressourcen Instanz: [Erstellen eines Ressourcenpools für externe Skripts](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)
  
 Sie können die *externen Ressourcenpool* Mechanismus zum Verwalten von Ressourcen durch die folgenden ausführbaren Dateien, die beim Machine Learning verwendet werden:

+ Rterm.exe und Satellitenprozesse
+ Python.exe und Satelliten-Prozesse
+ BxlServer.exe und Satellitenprozesse
+ Satelliten-Prozesse gestartet haben Launchpad
  
> [!NOTE]
> 
> Die direkte Verwaltung den Launchpad-Dienst mithilfe der Ressourcenkontrolle wird nicht unterstützt. Das liegt daran, dass [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ein vertrauenswürdiger Dienst ist, der so entworfen wurde, dass er nur Startprogramme hostet, die von Microsoft bereitgestellt werden. Vermeiden Sie übermäßige Ressourcen beanspruchen vertrauenswürdigen Startprogramme konfiguriert.
>   
> Es wird empfohlen, Satellitenprozesse mit dem Resource Governor zu verwalten und sie entsprechend den Bedürfnissen der individuellen Datenbankkonfiguration und Arbeitsauslastung zu optimieren.  Zum Beispiel kann jeder einzelne Satellitenprozess während der Ausführung bei Bedarf erstellt oder gelöscht werden.
  
## <a name="disable-external-script-execution"></a>Ausführen des externen Skripts deaktivieren

Die Unterstützung externer Skripts ist bei der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] optional. Auch nach der Installation von Machine learning-Funktionen, die Fähigkeit zur Ausführung externer Skripts ist standardmäßig deaktiviert und müssen Sie manuell die Eigenschaft neu zu konfigurieren und starten Sie die Instanz, um die Ausführung des Skripts zu aktivieren.

Aus diesem Grund, wenn eine Ressource-Problem, das sofort entschärft werden muss, oder ein Sicherheitsproblem vorhanden ist, ein Administrator kann sofort deaktiviert alle externen skriptausführung mithilfe [Sp_configure &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) und Festlegen der Eigenschaft `external scripts enabled` auf "false" oder 0 gesetzt.
  
## <a name="see-also"></a>Siehe auch

[Verwalten und Überwachen von Machine Learning-Lösungen](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)

[Erstellen eines Ressourcenpools für Machine Learning](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

[Ressourcenpools der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
