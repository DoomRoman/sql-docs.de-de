---
title: Verwenden von gespeicherten Prozeduren (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed9232137bcfed47852086ab1b6b76bc2bc2cb69
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582242"
---
# <a name="using-stored-procedures-mdx"></a>Verwenden von gespeicherten Prozeduren (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sie können die Funktionalität von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und Multidimensional Expressions (MDX) erweitern, indem sie mit .NET gespeicherte Prozeduren oder benutzerdefinierte Funktionen erstellen. Weitere Informationen finden Sie unter [ADOMD.NET Server-Programmierung](../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
 Wenn Sie auf eine gespeicherte Prozedur verweisen bzw. eine gespeicherte Prozedur aufrufen, geben Sie den Namen der Prozedur und dahinter Klammern an. In den Klammern können Sie Ausdrücke angeben. Diese Ausdrücke werden als Argumente bezeichnet und stellen die Daten bereit, die an die Parameter zu übergeben sind. Wenn Sie eine Funktion aufrufen, müssen Sie Argumentwerte für alle Parameter bereitstellen und die Argumentwerte in derselben Reihenfolge angeben, in der die Parameter in der benutzerdefinierten Funktion definiert sind.  
  
 Die folgende Beispielabfrage geht davon aus, dass Sie über eine auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server registrierte Assembly mit dem Namen SampleAssembly verfügen:  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *Gespeicherte Prozedur* in verwendete Terminologie ist [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] für diese Arten von Funktionen. Frühere Versionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bezeichnet diese Arten von Funktionen als *von benutzerdefinierten Funktionen*.  
  
## <a name="types-of-stored-procedures"></a>Arten von gespeicherten Prozeduren  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt sowohl COM- als auch CLR-Assemblys. CLR-Assemblys empfehlen sich wegen der für sie verfügbaren verbesserten Sicherheit. Wenn Microsoft Office Excel auf dem Server installiert ist, sind auch die Excel-Funktionen verfügbar.  
  
> [!NOTE]  
>  COM-Assemblys von Microsoft Visual Basic für Applikationen (VBA) werden automatisch registriert.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)  
  
  
