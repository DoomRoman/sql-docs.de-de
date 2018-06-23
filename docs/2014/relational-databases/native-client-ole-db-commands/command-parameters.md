---
title: Befehlsparameter | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cf00eb9d28acb7727b888eb065647184653b7e87
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159989"
---
# <a name="command-parameters"></a>Befehlsparameter
  Parameter werden im Befehlstext durch ein Fragezeichen markiert. Zum Beispiel wurde die folgende SQL-Anweisung für einen einzelnen Eingabeparameter markiert:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Zum Verbessern der Leistung durch Reduzierung des Netzwerkverkehrs der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird nicht automatisch Parameterinformationen, wenn **ICommandWithParameters:: GetParameterInfo** oder  **ICommandPrepare:: Prepare** wird aufgerufen, bevor die Ausführung eines Befehls. Dies bedeutet, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erfasst nicht automatisch:  
  
-   Überprüfen Sie die Richtigkeit des angegebenen Datentyps **ICommandWithParameters:: SetParameterInfo**.  
  
-   Zuordnen des in den Accessor-Bindungsinformationen angegebenen DBTYPE zum korrekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp für den Parameter  
  
 Bei Einsatz dieser beiden Methoden können in Anwendungen möglicherweise Fehler oder Genauigkeitsverluste auftreten, wenn Datentypen angegeben werden, die nicht mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp des Parameters kompatibel sind.  
  
 Um dies zu vermeiden, sollte die Anwendung Folgendes tun:  
  
-   Sicherstellen, dass *PwszDataSourceType* entspricht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp für den Parameter auf, wenn eine feste Programmierung **ICommandWithParameters:: SetParameterInfo**.  
  
-   Sicherstellen, dass der DBTYPE–Wert, der an den Parameter gebunden wird, vom gleichen Typ wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp des Parameters ist, wenn ein Accessor fest codiert wird.  
  
-   Code aufrufen **ICommandWithParameters:: GetParameterInfo** , damit der Anbieter abrufen, kann die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen der Parameter dynamisch. Beachten Sie, dass dies einen zusätzlichen Netzwerkroundtrip zum Server bedingt.  
  
> [!NOTE]  
>  Der Anbieter unterstützt keine Aufrufen **ICommandWithParameters:: GetParameterInfo** für eine beliebige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Update- oder DELETE-Anweisung mit einer FROM-Klausel; für jede SQL-Anweisung von einer Unterabfrage mit Parametern; für SQL-Anweisungen, wie z. B. mit der parametermarkierungen in beiden Ausdrücken eines Vergleichs oder quantifizierten Prädikats enthalten; oder Abfragen, wobei einer der Parameter einen Parameter an eine Funktion ist. Bei der Verarbeitung von Batches von SQL-Anweisungen, der Anbieter auch unterstützt keine Aufrufen **ICommandWithParameters:: GetParameterInfo** für parametermarkierungen in Anweisungen nach der ersten Anweisung im Batch. Kommentare (/ * \*/) sind nicht zulässig, der [!INCLUDE[tsql](../../includes/tsql-md.md)] Befehl.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Eingabeparameter in SQL-Anweisungsbefehlen. In prozeduraufrufbefehlen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Eingabe-, Ausgabe- und Eingabe/Ausgabe-Parameter. Ausgabeparameterwerte werden entweder nach der Ausführung (nur wenn keine Rowsets zurückgegeben werden) oder nach Abschluss der Rowsetverarbeitung durch die Anwendung an die Anwendung zurückgegeben. Um sicherzustellen, dass zurückgegebene Werte gültig sind, verwenden Sie **IMultipleResults** um Rowsets zu erzwingen.  
  
 Die Namen der Parameter von gespeicherten Prozeduren müssen nicht in einer DBPARAMBINDINFO-Struktur angegeben werden. Verwenden Sie NULL für den Wert von der *PwszName* -Element an, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter sollten den Parameternamen ignorieren und nur die im angegebenen Ordinalzahl verwenden die *RgParamOrdinals*Mitglied **ICommandWithParameters:: SetParameterInfo**. Wenn der Befehlstext sowohl benannte als auch unbenannte Parameter enthält, dann müssen alle unbenannten Parameter vor den benannten Parametern angegeben werden.  
  
 Wenn Sie der Namen der Parameter einer gespeicherten Prozedur angegeben wird, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter überprüft den Namen, um sicherzustellen, dass er gültig ist. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler zurück, wenn er vom Consumer einen fehlerhaften Parameternamen erhält.  
  
> [!NOTE]  
>  Unterstützung für die bereitzustellenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML und benutzerdefinierte Typen (UDT), die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert ein neues [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle](commands.md)  
  
  