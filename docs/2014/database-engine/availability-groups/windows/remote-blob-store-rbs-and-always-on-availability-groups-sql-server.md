---
title: Remote Blob Store (RBS) und AlwaysOn-Verfügbarkeitsgruppen (SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 16480ffcaf73a88f5983bef41b90f2276709d947
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212060"
---
# <a name="remote-blob-store-rbs-and-alwayson-availability-groups-sql-server"></a>Remote Blob Store (RBS) und AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] kann eine Lösung für hohe Verfügbarkeit und Notfallwiederherstellung für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][Remote Blob Store (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) -BLOB-Objekte (BLOBs) bereitstellen. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] schützt alle in einer Verfügbarkeitsdatenbank gespeicherten RBS-Metadaten und -Schemas, indem sie an die sekundären Replikate repliziert werden. Dabei handelt es sich um die SharePoint-Inhaltsdatenbank. Im Allgemeinen speichert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] diese RBS-Metadaten unabhängig vom BLOB.  
  
 Der Schutz der RBD-BLOB-Daten hängt vom Speicherort des BLOB-Speichers ab:  
  
|Speicherort des BLOB-Speichers|Können diese BLOB-Daten von Verfügbarkeitsgruppen geschützt werden?|  
|-------------------------|-----------------------------------------------------|  
|Dieselbe Datenbank, in der die (mithilfe eines RBS-FILESTREAM-Anbieters gespeicherten) RBS-Metadaten enthalten sind.|Benutzerkontensteuerung|  
|Eine andere Datenbank in derselben Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (die mithilfe eines RBS-FILESTREAM-Anbieters gespeichert wurde)|Benutzerkontensteuerung<br /><br /> Es empfiehlt sich, diese Datenbank in derselben Verfügbarkeitsgruppe anzulegen wie die Datenbank, in der die RBS-Metadaten enthalten sind.|  
|Eine andere Datenbank in einer anderen Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (die mithilfe eines RBS-FILESTREAM-Anbieters gespeichert wurde)|Benutzerkontensteuerung<br /><br /> Diese Datenbank muss in einer separaten Verfügbarkeitsgruppe enthalten sein.|  
|Ein BLOB-Speicher eines Drittanbieters|nein<br /><br /> Um diese BLOB-Daten zu schützen, verwenden Sie die Hochverfügbarkeitsmechanismen des BLOB-Speicheranbieters.|  
  
##  <a name="Limitations"></a> Einschränkungen  
  
-   Für RBS-Maintainer muss das primäre Replikat als Ziel angegeben werden.  
  
##  <a name="Recommendations"></a> Empfehlungen  
  
-   Verwenden Sie einen Verfügbarkeitsgruppenlistener. Weitere Informationen finden Sie unter [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)wichtig sind.  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Wartung von Remote BLOB-Speicher](http://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (in der [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] -Onlinedokumentation)  
  
-   [Ausführen des RBS-Maintainers](http://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (Blog)  
  
-   [Konfigurieren von Remote BLOB Storage (RBS) mit dem FILESTREAM-Anbieter (SharePoint 2010)](http://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (Blog)  
  
## <a name="see-also"></a>Siehe auch  
 [AlwaysOn-Clientkonnektivität &#40;SQLServer&#41;](always-on-client-connectivity-sql-server.md)   
 [Remoteblobspeicher &#40;RBS&#41; &#40;SQL Server&#41;](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  
