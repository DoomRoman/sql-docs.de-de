---
title: DataMember-Eigenschaft | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d194cea2dd1a7bbabf8acd2e9d89945772eddd31
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277409"
---
# <a name="datamember-property"></a>DataMember-Eigenschaft
Gibt den Namen des Datenmembers, die aus abgerufen werden, wird die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) verwiesen wird, indem Sie die [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) Eigenschaft.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert. Der Name ist nicht in der Groß-/Kleinschreibung beachtet.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft wird verwendet, um datengebundene Steuerelemente mit der Daten-Umgebung zu erstellen. Der Daten-Umgebung verwaltet, Auflistungen von Daten (Datenquellen), enthält benannte Objekte (Datenmember), die als dargestellt werden, werden eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
 Die **DataMember** und **DataSource** Eigenschaften müssen zusammen verwendet werden.  
  
 Die **DataMember** Eigenschaft bestimmt, welches Objekt vom angegebenen der **DataSource** Eigenschaft als dargestellt wird ein **Recordset** Objekt. Die **Recordset** Objekt muss geschlossen werden, bevor diese Eigenschaft festgelegt wird. Ein Fehler wird generiert, wenn der **DataMember** Eigenschaft nicht festgelegt ist, bevor die **DataSource** -Eigenschaft, oder, wenn der **DataMember** Name wurde nicht erkannt, von dem Objekt angegeben wird, der **DataSource** Eigenschaft.  
  
## <a name="usage"></a>Verwendung  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [DataSource-Eigenschaft (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
