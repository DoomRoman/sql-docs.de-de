---
title: IDBProperties (OLE DB) | Microsoft Docs
description: IDBProperties-Schnittstelle (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d2b5fa37e7cacb6ae29a260ceb6e57089b85e817
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689823"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dank der OLE DB-Standardspezifikation können Anbieter VT_EMPTY für **DBPROPINFO::vValues**angeben. Allerdings OLE DB-Treiber für SQL Server-OLE DB immer VT_EMPTY zurückgegeben beim Aufrufen von **GetPropertyInfo** mit **DBPROPSET_ROWSETALL** Rowseteigenschaften abgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
