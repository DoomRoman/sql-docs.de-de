---
title: Nächste Abrufposition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0b3bb59d06f0ac6b12ac9ca2f6785659a16e0e11
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426329"
---
# <a name="fetching-rows---next-fetch-position"></a>Abrufen von Zeilen – nächste Abrufposition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verfolgt die nächste Abrufposition also, die eine Sequenz von Aufrufen an die **GetNextRows** Methode (ohne überspringt, Änderungen der Richtung oder dazwischen liegenden aufruft, um die  **FindNextRow**, **Seek**, oder **RestartPosition** Methoden) das gesamte Rowset liest, ohne zu überspringen oder eine beliebige Zeile wiederholt. Die nächste Abrufposition wird entweder durch den Aufruf geändert **IRowset:: GetNextRows**, **IRowset:: RestartPosition**, oder **IRowsetIndex:: Seek**, oder durch Aufrufen von **FindNextRow** mit einer Null- *pBookmark* Wert. Aufrufen von **FindNextRow** mit einen *pBookmark* Wert wirkt sich auf die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Zeilen](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
