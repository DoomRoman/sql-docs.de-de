---
title: STPolyFromText (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STPolyFromText_TSQL
- STPolyFromText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPolyFromText (geometry Data Type)
ms.assetid: a7c1c9f0-1dd5-493b-b206-83bbfa33452b
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c7ad95f8919789523007b058a46a67e708701a80
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="stpolyfromtext-geometry-data-type"></a>STPolyFromText (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt eine **geometry** -Instanz aus einer Darstellung des Typs Open Geospatial Consortium (OGC) Well-Known Text (WKT) zurück, die um alle von der Instanz getragenen Z (Höhe)- und M (Measure)-Werte erweitert wurde.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STPolyFromText ( 'polygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argumente  
 *polygon_tagged_text*  
 Die WKT-Darstellung der Instanz von **geometryPolygon**, die zurückgegeben werden soll. *polygon_tagged_text* ist ein **nvarchar(max)**-Ausdruck.  
  
 *SRID*  
 Ein **int**-Ausdruck, der die SRID (Spatial Reference ID) der **geometryPolygon**-Instanz darstellt, die zurückgegeben werden soll.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 OGC-Typ: **Polygon**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STPolyFromText()` verwendet, um eine `geometry`-Instanz zu erstellen.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPolyFromText('POLYGON ((5 5, 10 5, 10 10, 5 5))', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Statische geometry-Methoden des OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

