---
title: EnvelopeAngle (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4a66a7995d4ad6a97ca7d90798038dc2fe372150
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836720"
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt den maximalen Winkel zwischen dem durch `EnvelopeCenter()` zurückgegebenen Punkt und einem Punkt in der **geography** -Instanz in Grad zurück.  
  
 Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **float**  
  
 CLR-Rückgabetyp: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt einen Punkt in der **geography** -Instanz in Grad zurück. Bei Verwendung mit EnvelopeCenter () gibt `EnvelopeAngle()` einen umschließenden Kreis einer **geography**-Instanz zurück.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wurde diese Methode auf **FullGlobe**-Instanzen erweitert.  
  
 Die in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] für `EnvelopeAngle()` verwendete Hemisphäreneinschränkung wurde entfernt. Bei Instanzen, deren Winkel 90 Grad übersteigt, wird jedoch 180 Grad zurückgegeben. `EnvelopeAngle()` ist bei Instanzen von **geography**, die mehr als eine Hemisphäre umfassen, nicht exakt.  
  
## <a name="examples"></a>Beispiele  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  
