---
title: Datentypen und XML-Massenladen das Ladeverhalten (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ce59362d28c4d65e32834fd965cf710f49edb501
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274676"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Datentypen und XML-Massenladenverhalten (SQLXML 4.0)
  Die Datentypen, die im Zuordnungsschema (XSD- oder XDR-Schema und `sql:datatype`) angegeben werden, werden mit Ausnahme der folgenden Fälle immer ignoriert:  
  
 Bei XSD:  
  
-   Bei den Typen `dateTime` oder `time` müssen Sie die `sql:datatype`-Anmerkung angeben, da XML-Massenladen vor dem Senden der Daten an Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Datenkonvertierung durchführt.  
  
-   Wenn Sie beim Massenladen in eine Spalte vom sind `uniqueidentifier` geben [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und der XSD-Wert ist eine GUID mit geschweiften Klammern ({und}), Sie müssen angeben, **SQL: datatype = "Uniqueidentifier"** die geschweiften Klammern zu entfernen, bevor der Wert ist in der Spalte eingefügt. Wenn `sql:datatype` nicht angegeben wird, wird der Wert mit Klammern gesendet, und beim Einfügen tritt ein Fehler auf.  
  
 Weitere Informationen zu `sql:datatype`, finden Sie unter [Datentypumwandlungen und die SQL: DataType-Anmerkung &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 Bei XDR:  
  
-   Wenn der `dt:type` `datetime`, `time`, `dateTime.tz` oder `time.tz` lautet, müssen Sie die Datentypen `dt:type` und `sql:datatype` angeben, da XML-Massenladen vor dem Senden der Daten an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Datenkonvertierung durchführt.  
  
-   Wenn Ihre XML-Daten vom Typ `uuid`, `sql:datatype` muss angegeben werden; **dt: Type = "Uuid"** ist auch erforderlich, es sei denn, die Daten um Zeichenfolgendaten handelt. Wenn `dt:uuid` nicht angegeben wird, akzeptiert XML-Massenladen Zeichenfolgen mit Klammern (und entfernt diese ggf.).  
  
-   Wenn es sich bei den XML-Daten um Daten vom Typ `bin.base64` oder `bin.hex` handelt, müssen Sie den XML-Datentyp mit `dt:type` angeben. XML-Massenladen lädt die Daten dann als Hexadezimaldarstellung der Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  
