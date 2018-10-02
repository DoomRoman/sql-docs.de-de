---
title: STGeomCollFromText (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeomCollFromText_TSQL
- STGeomCollFromText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromText (geometry Data Type)
ms.assetid: 19e757b3-cb2e-4852-87b9-40a815ab707e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a5305ccc5c6a1fa8e6011f3ab87026c03a721b9e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47817088"
---
# <a name="stgeomcollfromtext-geometry-data-type"></a>STGeomCollFromText (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt eine **geometry** -Instanz aus einer Darstellung des Typs Open Geospatial Consortium (OGC) Well-Known Text (WKT) zurück, die um alle von der Instanz getragenen Z (Höhe)- und M (Measure)-Werte erweitert wurde.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STGeomCollFromText ( 'geometrycollection_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argumente  
 *geometrycollection_tagged_text*  
 Die WKT-Darstellung der Instanz von **geometry** , die zurückgegeben werden soll. *geometry_tagged_text* ist ein **nvarchar(max)** -Ausdruck.  
  
 *SRID*  
 Ein **int** -Ausdruck, der die SRID (Spatial Reference ID) der **geometry** -Instanz darstellt, die Sie zurückgeben möchten.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Der OGC-Typ der **geometry** -Instanz, die von `STGeomCollFromText()` zurückgegeben wird, wird auf die entsprechende WKT-Eingabe festgelegt.  
  
 Diese Methode löst eine Ausnahme aus, wenn die Eingabe nicht gültig ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STGeomCollFromText()` verwendet, um eine geometry-Instanz zu erstellen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION ( POLYGON((5 5, 10 5, 10 10, 5 5)), POINT(10 10) )', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Statische geometry-Methoden des OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

