---
title: SQLSetPos (Desktop-Datenbanktreiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Desktop Database Drivers
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95117c82c213851d2e0600e65d8061ce532d9933
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601608"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (Desktop-Datenbanktreiber)
Die Bulk-Model-Semantik für **SQLSetPos** Ruft mit dem *Irow* Argument gleich 0 werden unterstützt.  
  
 SQL_LOCK_NO_CHANGE wird unterstützt, für die *Bestand*. SQL_LOCK_EXCLUSIVE und SQL_LOCK_UNLOCK werden nicht unterstützt.  
  
 **SQLSetPos** unterstützt aktualisierbare Joins. (Weitere Informationen finden Sie unter den *Microsoft Jet-Datenbank-Engine Handbuch für Programmierer*.)
