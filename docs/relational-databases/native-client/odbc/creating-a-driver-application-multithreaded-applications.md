---
title: Multithread-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 1752f8ceb437c0c5d896f6080f8800e114192d73
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39544720"
---
# <a name="creating-a-driver-application---multithreaded-applications"></a>Erstellen einer Treiberanwendung – Multithreadanwendungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ist ein Multithreadtreiber. Das Schreiben einer Multithreadanwendung ist eine Alternative zum Verwenden von asynchronen Aufrufen zur Verarbeitung von mehreren ODBC-Aufrufen. Ein Thread kann einen synchronen ODBC-Aufruf erstellen, und andere Threads können verarbeitet werden, während der erste Thread blockiert wird und auf die Antwort auf seinen Aufruf wartet. Dieses Modell ist effizienter als asynchrone Aufrufe, da Verarbeitungsaufwand beseitigt wird, wie Netzwerkverkehr und die wiederholte Erstellung von ODBC-Funktionsaufrufen zum Überprüfen von SQL_STILL_EXECUTING.  
  
 Der asynchrone Modus ist immer noch eine effektive Methode der Verarbeitung. Die Leistungsverbesserungen eines Multithreadmodells genügen nicht, um das Umschreiben asynchroner Anwendungen zu rechtfertigen. Wenn Benutzer DB-Library-Anwendungen konvertieren, die das asynchrone DB-Library-Modell verwenden, empfiehlt sich die Konvertierung in das asynchrone ODBC-Modell.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer SQL Server Native Client-ODBC-Treiberanwendung](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
  
