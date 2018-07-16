---
title: NULL-Zulässigkeit und Vergleiche mit Dreiwertiger Logik | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4a01f167900a0aa64759297f6a3b4b2d2c81cf86
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356202"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Zulässigkeit von NULL-Werten und Vergleiche mit dreiwertiger Logik
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn Sie mit vertraut sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen finden Sie ähnliche Semantik und Genauigkeit in die **System.Data.SqlTypes** -Namespace in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Es gibt jedoch einige Unterschiede, und die wichtigsten dieser Unterschiede werden in diesem Thema behandelt.  
  
## <a name="null-values"></a>NULL-Werte  
 Ein Hauptunterschied zwischen den systemeigenen CLR (Common Language Runtime)-Datentypen und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen besteht darin, dass Erstere keine NULL-Werte zulassen, Letztere dagegen die uneingeschränkte NULL-Semantik bereitstellen.  
  
 Vergleiche werden durch NULL-Werte beeinflusst. Wenn die beiden Werte x und y verglichen werden und x oder y NULL ist, dann ergeben einige logische Vergleiche den Wert UNKNOWN statt true oder false.  
  
## <a name="sqlboolean-data-type"></a>SqlBoolean-Datentyp  
 Zur Darstellung dieser dreiwertigen Logik wurde im **System.Data.SqlTypes** -Namespace der **SqlBoolean** -Typ eingeführt. Vergleiche zwischen beliebigen Werten des Typs **SqlTypes** ergeben einen Wert des **SqlBoolean** -Typs. Der UNKNOWN-Wert wird durch den NULL-Wert des **SqlBoolean** -Typs dargestellt. Die Eigenschaften **IsTrue**, **IsFalse**und **IsNull** dienen zur Überprüfung des Werts eines **SqlBoolean** -Typs.  
  
## <a name="operations-functions-and-null-values"></a>Vorgänge, Funktionen und NULL-Werte  
 Alle arithmetischen Operatoren (+, -, \*, /, %), bitweise Operatoren (~, &, und |), und die meisten Funktionen geben NULL zurück, wenn einer der Operanden oder Argumente des **"SqlTypes"** NULL sind. Die **IsNull** -Eigenschaft gibt stets den Wert true oder false zurück.  
  
## <a name="precision"></a>Genauigkeit  
 Dezimaldatentypen in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR gelten andere Maximalwerte als die der numerischen Datentypen und dezimaldatentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Außerdem wird bei den Dezimaldatentypen der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-CLR die maximale Genauigkeit angenommen. In der CLR für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]jedoch **SqlDecimal** bietet die gleiche maximale Genauigkeit und Skalierung und die gleiche Semantik wie die dezimaldatentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="overflow-detection"></a>Überlauferkennung  
 In der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-CLR wird durch die Addition von zwei sehr großen Zahlen möglicherweise keine Ausnahme ausgelöst. Wenn kein Prüfvorgang verwendet wurde, dann wird das zurückgegebene Ergebnis möglicherweise als negative Ganzzahl dargestellt. In **System.Data.SqlTypes**werden Ausnahmen für alle Überlauf- und Unterlauffehler sowie Fehler aufgrund einer Division durch 0 ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
