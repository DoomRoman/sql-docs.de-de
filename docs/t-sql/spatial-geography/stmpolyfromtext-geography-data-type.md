---
title: STMPolyFromText (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STMPolyFromText (geography Data Type)
- STMPolyFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMPolyFromText method
ms.assetid: 15356c0f-5144-418d-aa96-3e7ea5fecea3
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4fcda3984b8b0cca330d8602e083371ece0c0638
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33062367"
---
# <a name="stmpolyfromtext-geography-data-type"></a>STMPolyFromText (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt eine **geography** -Instanz von einer Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung zurück, die um alle von der Instanz getragenen Z (Höhe)- und M (Measure)-Werte erweitert ist.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STMPolyFromText ( 'multipolygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argumente  
 *multipolygon_tagged_text*  
 Die WKT-Darstellung der **geographyMultiPolygon**-Instanz, die zurückgegeben werden soll. *multipolygon_tagged_text* ist ein **nvarchar(max)**-Ausdruck.  
  
 *SRID*  
 Ein **int**-Ausdruck, der die SRID (Spatial Reference ID) der **geographyMultiPolygon**-Instanz darstellt, die zurückgegeben werden soll.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 Rückgabetyp: **Sql Geography**  
  
 OGC-Typ: **MultiPolygon**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STMPolyFromText()` verwendet, um eine `geography`-Instanz zu erstellen.  
  
```  
DECLARE @g geography;  
SET @g = geography::STMPolyFromText('MULTIPOLYGON(((-122.358 47.653, -122.348 47.649, -122.358 47.658, -122.358 47.653)), ((-122.341 47.656, -122.341 47.661, -122.351 47.661, -122.341 47.656)))', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Statische geography-Methoden des OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
