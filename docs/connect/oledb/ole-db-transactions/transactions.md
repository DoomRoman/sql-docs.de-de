---
title: Transaktionen | Microsoft-Dokumentation
description: Sitzungen im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 3cf4aa84b59e41976383b6d5d567579ba2b457bf
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022329"
---
# <a name="transactions"></a>Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server implementiert die lokale transaktionsunterstützung. Der Consumer kann verteilte oder koordinierte Transaktionen mit Microsoft Distributed Transaction Coordinator (MS DTC) verwenden. Für Consumer, die über mehrere Sitzungen hinweg Transaktionskontrolle erfordern, kann der OLE DB-Treiber für SQL Server von MS DTC initiierte und verwaltete Transaktionen verknüpfen.  
  
 Standardmäßig verwendet der OLE DB-Treiber für SQL Server einen Autocommit-Transaktionsmodus, bei dem jede diskrete Aktion in einer Consumersitzung eine vollständige Transaktion für eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] umfasst. Der Autocommitmodus des OLE DB-Treibers für SQL Server ist lokal, und Autocommittransaktionen erstrecken sich grundsätzlich nur über eine Sitzung.  
  
 Der OLE DB-Treiber für SQL Server stellt die **ITransactionLocal**-Schnittstelle zur Verfügung und ermöglicht dem Consumer, Starttransaktionen für eine Einzelverbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] explizit und implizit zu verwenden. Der OLE DB-Treiber für SQL Server unterstützt keine geschachtelte lokale Transaktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützen lokaler Transaktionen](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Unterstützen von verteilten Transaktionen](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Isolationsstufen &#40;OLE-DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
