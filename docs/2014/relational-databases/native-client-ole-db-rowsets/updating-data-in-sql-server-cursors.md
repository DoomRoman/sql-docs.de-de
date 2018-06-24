---
title: Aktualisieren von Daten in SQL Server-Cursor | Microsoft Docs
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
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31bf68fc2328b0cb2d12f881579ba6b3ff9f0d79
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056463"
---
# <a name="updating-data-in-sql-server-cursors"></a>Aktualisieren von Daten in SQL Server-Cursorn
  Beim Abrufen und Aktualisieren von Daten über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Cursorn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Consumer-Anwendung gebunden ist, indem Sie die gleichen Überlegungen und Einschränkungen, die für jede andere Clientanwendung gelten.  
  
 Nur Zeilen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursorn nehmen an der gleichzeitigen Datenzugriffssteuerung teil. Wenn der Consumer ein änderbares Rowset anfordert, wird die Parallelitätssteuerung von DBPROP_LOCKMODE kontrolliert. Um die Steuerungsebene für den gleichzeitigen Zugriff zu ändern, legt der Consumer die DBPROP_LOCKMODE-Eigenschaft vor dem Öffnen des Rowsets fest.  
  
 Transaktionsisolationsstufen können zu beträchtlichen Verzögerungen bei der Zeilenpositionierung führen, wenn Transaktionen aufgrund des Designs der Clientanwendung über längere Zeit geöffnet bleiben. Wird standardmäßig die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwendet, die von DBPROPVAL_TI_READCOMMITTED angegebene Read committed-Isolationsstufe. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die dirty read-Isolation, wenn die rowsetparallelität schreibgeschützt ist. Daher kann der Consumer in einem änderbaren Rowset eine höhere Isolationsstufe jedoch keine niedrigere Stufe erfolgreich anfordern.  
  
## <a name="immediate-and-delayed-update-modes"></a>Unmittelbarer und verzögerter Updatemodus  
 Im sofortupdatemodus, hat jeder Aufruf von **IRowsetChange:: SetData** bewirkt, dass einen Roundtrip zum der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn der Consumer mehrere Änderungen an einer einzelnen Zeile vornimmt, es ist jedoch effizienter, um alle Änderungen mit einem einzelnen übergeben **SetData** aufrufen.  
  
 Im verzögerten Updatemodus ein Roundtrip zu den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für jede Zeile im angegebenen der *cRows* und *RghRows* Parameter des **IRowsetUpdate:: Update**.  
  
 In beiden Modi stellt ein Roundtrip eine separate Transaktion dar, wenn kein Transaktionsobjekt für das Rowset geöffnet ist.  
  
 Wenn Sie verwenden **IRowsetUpdate:: Update**die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter versucht, jede angegebene Zeile zu verarbeiten. Einen Fehler aufgrund ungültiger Daten, Längen- oder Statuswerte Werte für jede Zeile nicht angehalten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Verarbeitung. Es können nur alle oder keine der anderen am Update beteiligten Zeilen geändert werden. Der Consumer muss das zurückgegebene untersuchen *PrgRowStatus* Array Fehler bestimmen Datenzeile, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück.  
  
 Ein Consumer darf nicht davon ausgehen, dass Zeilen in einer bestimmten Reihenfolge verarbeitet werden. Wenn ein Consumer es erfordert, dass die Verarbeitung von Datenänderungen in mehr als einer Zeile in einer bestimmten Reihenfolge durchgeführt wird, muss der Consumer diese Reihenfolge in der Anwendungslogik festlegen und eine Transaktion öffnen, um den Prozess darin einzuschließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Daten in Rowsets](updating-data-in-rowsets.md)  
  
  