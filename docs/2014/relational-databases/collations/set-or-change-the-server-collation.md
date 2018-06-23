---
title: Festlegen oder Ändern der Serversortierung | Microsoft-Dokumentation
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
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f341ba87e716856fcad8ca2831f1fcf97f0071a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148145"
---
# <a name="set-or-change-the-server-collation"></a>Festlegen oder Ändern der Serversortierung
  Die Serversortierung fungiert als Standardsortierung für alle Systemdatenbanken, die zusammen mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert werden, sowie für alle neu erstellten Benutzerdatenbanken. Die Serversortierung wird bei der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angegeben. Weitere Informationen finden Sie unter [Collation and Unicode Support](collation-and-unicode-support.md).  
  
## <a name="changing-the-server-collation"></a>Ändern der Serversortierung  
 Das Ändern der Standardsortierung für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann ein komplexer Vorgang sein, der die folgenden Schritte umfasst:  
  
-   Sicherstellen, dass Ihnen alle Informationen oder Skripts zur Verfügung stehen, die zum erneuten Erstellen der Benutzerdatenbanken und aller darin enthaltenen Objekte erforderlich sind.  
  
-   Exportieren aller Daten mithilfe eines Tools wie z. B. dem [bcp Utility](../../tools/bcp-utility.md). Weitere Informationen finden Sie unter [Massenimport und -export von Daten &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
-   Löschen aller Benutzerdatenbanken.  
  
-   Neuerstellen der Masterdatenbank unter Angabe der neuen Sortierung in der SQLCOLLATION-Eigenschaft des **setup** -Befehls. Zum Beispiel:  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     Weitere Informationen finden Sie unter [Neuerstellen von Systemdatenbanken](../databases/system-databases.md).  
  
-   Erstellen aller Datenbanken und aller darin enthaltenen Objekte.  
  
-   Importieren aller Daten.  
  
> [!NOTE]  
>  Anstatt die Standardsortierung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu ändern, können Sie eine Standardsortierung für alle neu zu erstellenden Datenbanken angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Collation and Unicode Support](collation-and-unicode-support.md)   
 [Festlegen oder Ändern der Datenbanksortierung](set-or-change-the-database-collation.md)   
 [Festlegen oder Ändern der Spaltensortierung](set-or-change-the-column-collation.md)   
 [Neuerstellen von Systemdatenbanken](../databases/system-databases.md)  
  
  