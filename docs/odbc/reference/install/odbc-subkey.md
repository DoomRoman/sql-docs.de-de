---
title: Unterschlüssel für ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry entries for data sources [ODBC], ODBC subkey
- subkeys [ODBC], ODBC subkey
- ODBC subkey [ODBC]
ms.assetid: f9534144-8f42-4946-b0fb-638e9dcde9c8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee7cf624e7c118a5d9ef36738c810aecc4ec5684
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711538"
---
# <a name="odbc-subkey"></a>ODBC-Unterschlüssel
Die Werte unter dem Unterschlüssel für ODBC geben Sie Optionen für die Ablaufverfolgung von ODBC. Diese Optionen werden über der Registerkarte "Ablaufverfolgung" angezeigt wird, indem Sie im Dialogfeld ODBC-Datenquellen-Administrator festgelegt **SQLManageDataSources**. Der ODBC-Unterschlüssel selbst ist optional. Das Format dieser Werte ist, wie in der folgenden Tabelle gezeigt.  
  
|Name|Datentyp|data|  
|----------|---------------|----------|  
|Ablaufverfolgung|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*Tracefile-Pfad*|  
  
 Die Werte haben die Bedeutungen, die in der folgenden Tabelle beschrieben.  
  
|value|Bedeutung|  
|-----------|-------------|  
|Ablaufverfolgung|Wenn der Wert für die Ablaufverfolgung festgelegt wird, 1, wenn eine Anwendung ruft **SQLAllocHandle** mit der Option SQL_HANDLE_ENV auf, Ablaufverfolgung für die aufrufende Anwendung aktiviert ist.<br /><br /> Wenn das Trace-Schlüsselwort auf 0 festgelegt ist, wenn eine Anwendung ruft **SQLAllocHandle** Ablaufverfolgung ist mit der Option SQL_HANDLE_ENV auf, für die aufrufende Anwendung deaktiviert. Dies ist der Standardwert.<br /><br /> Eine Anwendung kann aktivieren oder deaktivieren die Ablaufverfolgung mit der SQL_ATTR_TRACE-Verbindungsattribut. Allerdings wird dadurch also nicht die Daten für diesen Wert geändert.|  
|TraceFile|Wenn Ablaufverfolgung aktiviert ist, schreibt den Treiber-Manager, in der Ablaufverfolgungsdatei, die durch den Wert für die Ablaufverfolgungsdatei angegeben.<br /><br /> Wenn keine der Ablaufverfolgungsdatei angegeben wird, schreibt den Treiber-Manager zur Sql.log-Datei auf das aktuelle Laufwerk. Dies ist der Standardwert.<br /><br /> Ablaufverfolgung sollte nur für eine einzelne Anwendung verwendet werden, oder jede Anwendung sollte eine andere Ablaufverfolgungsdatei angeben. Andernfalls, zwei oder mehr Anwendungen versucht, öffnen Sie die gleiche Datei zur gleichen Zeit, verursacht einen Fehler.<br /><br /> Eine Anwendung kann eine neue Ablaufverfolgungsdatei mit dem SQL_ATTR_TRACEFILE Verbindung-Attribut angeben. Allerdings wird dadurch also nicht die Daten für diesen Wert geändert.|  
  
 Nehmen wir beispielsweise an, dass die Ablaufverfolgung aktiviert ist und die Ablaufverfolgungsdatei C:\Odbc.log. Die Werte unter dem Unterschlüssel für ODBC würde wie folgt lauten:  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
