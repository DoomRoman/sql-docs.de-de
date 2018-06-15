---
title: Übersicht über die Architektur von R-sprachunterstützung in SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3784fe62669b3f6d29e94bea799e19f9eadad5f0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201672"
---
# <a name="architecture-overview-for-r-in-sql-server"></a>Übersicht über die Architektur für R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Abschnitt enthält eine Übersicht über die Architektur von SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services.

Die Architektur für die erweiterbarkeitsarchitektur ist die gleiche oder sehr ähnlich, für den SQLServer 2016 und SQLServer-2017-Versionen und Ähnliches gilt auch für R und Python. Allerdings wird erläutert, um die Diskussion zu vereinfachen, nur die R-Komponenten, einschließlich neue Komponenten, die in der SQL Server-Datenbankmodul zur externen skriptausführung, Sicherheit, R-Bibliotheken und Interoperabilität mit open-Source-r-Unterstützung hinzugefügt

Weitere Details werden in den Links für die einzelnen Abschnitte bereitgestellt.

## <a name="r-interoperability"></a>R-Interoperabilität

Installieren SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services (Datenbankintern) open Source-Verteilung von R als auch von Microsoft bereitgestellte Pakete, die verteilte und/oder parallele Verarbeitung zu unterstützen.

Die Architektur ist so konzipiert, dass externe Skripts, die mithilfe von R in einem separaten Prozess von SQL Server ausgeführt. Aktuelle Benutzer von R sollten in der Lage sein, ihren R-Code zu übertragen und mit geringfügigen Änderungen in T-SQL auszuführen.

Um die Skalierbarkeit der Lösung, oder verwenden parallelen Verarbeitung, wir empfehlen die Verwendung der ["revoscaler"](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) Paket oder die [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package) Paket. Wenn Sie nicht die verteilte Datenverarbeitung Funktionen für diese Bibliotheken verwenden, können Sie immer noch einige Leistungssteigerungen durch Ausführen von R-Code im Kontext von SQL Server abrufen.

Weitere Informationen zu externen scripting-Komponenten, die installiert werden, oder die Interaktion von SQL Server mit R, finden Sie unter [R-Interoperabilität](../../advanced-analytics/r/r-interoperability-in-sql-server.md)

## <a name="components-to-support-r-integration"></a>Komponenten zur Unterstützung der Integration von R

Das Extensibility Framework, die in SQL Server 2016 eingeführt wird in SQL Server-2017 fortgesetzt. Die Erweiterbarkeitskomponenten werden von SQL Server zum für R, um Daten zwischen R und das Datenbankmodul übergeben, und klicken Sie zum Koordinieren der paralleler Aufgaben, die für ein R-Auftrag benötigt der externe Laufzeit gestartet.

Die Rolle dieser zusätzlichen Komponenten besteht darin Data Exchange Geschwindigkeit und Komprimierung, und bietet eine sichere, leistungsstarke Plattform für die Ausführung externer Skripts zu verbessern.

Ausführliche Beschreibung der Komponenten, die Unterstützung von R, wie z. B. die [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] und RLauncher, finden Sie unter [neue Komponenten](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md).

## <a name="security"></a>Sicherheit

Beim Ausführen von R-Code mithilfe von Machine Learning Services oder SQL Server R Services erfolgen alle R-Skripts außerhalb der SQL Server-Prozess, um Sicherheit und bessere Verwaltung zu ermöglichen. Diese Isolierung von Prozessen gilt unabhängig davon, ob führen Sie das R-Skript als Teil einer gespeicherten Prozedur oder der Auftrag der SQL Server-Computer von einem Remotecomputer herstellen und Starten eines Auftrags, das der Server als computekontext verwendet.

SQL Server fängt alle auftragsanforderungen, sichert der Task und seine Daten mithilfe von Windows-Auftragsobjekte und Sicherheit für Daten, die mit SQL Server-Benutzerkonten und Datenbankrollen verwaltet.

Daten werden innerhalb der Begrenzung des Kompatibilität beibehalten, durch das Durchsetzen von SQL Server-Sicherheit auf die Tabelle, Datenbank- und Instanzebene. Der Datenbankadministrator kann steuern, wer die Fähigkeit zur Ausführung von R-Aufträge hat und der Benutzer mit der Möglichkeit zum Installieren oder Freigeben von R-Pakete. Der Administrator kann die Ressourcen verbraucht auch die Verwendung von R-Skripts, durch die Benutzer entweder remote oder lokal, überwachen und überwachen und verwalten.

## <a name="next-steps"></a>Nächste Schritte

[Komponenten mit Unterstützung für die R-Integration](new-components-in-sql-server-to-support-r.md)

[Interoperabilität mit R](r-interoperability-in-sql-server.md)

[Sicherheitsübersicht](security-overview-sql-server-r.md)
