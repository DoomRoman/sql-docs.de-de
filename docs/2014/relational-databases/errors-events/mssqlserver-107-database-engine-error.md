---
title: MSSQLSERVER_107 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 4fee44ea6826f93ee32b8d22eb5cba00595627bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150818"
---
# <a name="mssqlserver107"></a>MSSQLSERVER_107
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|107|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|P_NOCORRMATCH|  
|Meldungstext|Das Spaltenpräfix '%.*ls' stimmt mit keinem in der Abfrage verwendeten Tabellen- oder Aliasnamen überein.|  
  
## <a name="explanation"></a>Erklärung  
 Die Auswahlliste der Abfrage enthält ein Sternchen (*), das falsch mit einem Spaltenpräfix gekennzeichnet ist. Dieser Fehler kann unter folgenden Bedingungen zurückgegeben werden:  
  
-   Das Spaltenpräfix stimmt mit keinem in der Abfrage verwendeten Tabellen- oder Aliasnamen überein. In der folgenden Anweisung wird beispielsweise ein Aliasname (`T1`) als Spaltenpräfix verwendet, der Alias ist jedoch nicht in der FROM-Klausel definiert.  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   Wenn in der FROM-Klausel ein Aliasname für die Tabelle festgelegt ist, wird ein Tabellenname als Spaltenpräfix angegeben. In der folgenden Anweisung wird beispielsweise der Tabellenname `ErrorLog` als Spaltenpräfix verwendet, für die Tabelle ist jedoch ein Alias (`T1`) in der FROM-Klausel definiert.  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
     Wenn in der FROM-Klausel ein Alias für einen Tabellennamen angegeben wurde, kann nur der Alias verwendet werden, der den Spalten in der Tabelle als Präfix vorangestellt wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 Gleichen Sie die Spaltenpräfixe mit den in der FROM-Klausel der Abfrage angegeben Tabellen- oder Aliasnamen ab. Die oben genannten Anweisungen können beispielsweise folgendermaßen korrigiert werden:  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
 oder  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MSSQLSERVER_4104](mssqlserver-4104-database-engine-error.md)  
  
  