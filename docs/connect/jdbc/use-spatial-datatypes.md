---
title: Räumliche Datentypen mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 726711458f62011fc7bcaef268887813c9c9c3d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842005"
---
# <a name="using-spatial-datatypes"></a>Verwendung von räumlichen Datentypen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Räumliche Datentypen (Geometry und Geography) werden ab der Vorschauversion 6.5.0 JDBC-Treiber unterstützt. Räumliche Datentypen werden derzeit nicht mit gespeicherten Prozeduren, Table Valued Parameters (TVP), BulkCopy und Always Encrypted unterstützt. Diese Seite zeigt, dass verschiedene Fälle von Geometry- und Geography-Datentypen mit dem JDBC-Treiber verwenden. Überprüfen Sie eine Übersicht über räumliche Datentypen, [Übersicht über räumliche Datentypen](https://docs.microsoft.com/en-us/sql/relational-databases/spatial/spatial-data-types-overview) Seite.

## <a name="creating-a-geometry--geography-object"></a>Erstellen einer Geometry-/ Geography-Objekt

Es gibt zwei Hauptmethoden zum Erstellen einer Geometrie / Geography-Objekt – entweder konvertieren aus einer Well-Known Text (WKT) oder ein Well-Known Binary (WKB).

### <a name="creating-from-wkt"></a>Erstellen von WKT

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

Dadurch wird ein LINESTRING-Geometry-Objekt mit System Bezeichner SRID (Spatial Reference) 0, und ein geografieobjekt mit SRID 4326 erstellt.

### <a name="creating-from-wkb"></a>Erstellen aus einer WKB

```java
byte[] geomWKB = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogWKB = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomWKB);
Geography geogWKT = Geography.deserialize(geogWKB);
```

Dadurch wird ein Geometry- und Geography-Objekt erstellt, die von der WKT erstellt wurden, die zuvor entspricht.

## <a name="working-with-a-geometry--geography-object"></a>Arbeiten mit einer Geometrie / Geography-Objekt

Wenn der Benutzer verfügt über eine Tabelle in SQL Server wie unten:

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Eine Beispielskript zum Einfügen eines geometriewerts wäre:

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
```

Dasselbe für die Geography-Entsprechung, die mit einer Geografiespalte möglich und **setGeography()** Methode.

Lesen Sie eine Geometrie / Geography-Spalte:

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

Dasselbe für die Geography-Entsprechung, die mit einer Geografiespalte möglich und **getGeography()** Methode.

## <a name="newly-introduced-apis"></a>Neu eingeführten APIs

Hierbei handelt es sich um den neuen öffentlichen APIs, die mit folgender Ergänzung, in den Klassen eingeführt wurden **SQLServerPreparedStatement**, **SQLServerResultSet**, **Geometrie**, und  **Geography**.

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Methode|und Beschreibung|
|:------|:----------|
|"void" SetGeometry (Int-n, Geometrie X)| Legt den angegebenen Parameter mit dem angegebenen microsoft.sql.Geometry Klassenobjekt.
|"void" SetGeography (Int-n, Geography X)| Legt den angegebenen Parameter mit dem angegebenen microsoft.sql.Geography Klassenobjekt.

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Methode|und Beschreibung|
|:------|:----------|
|Geometry GetGeometry (ColunIndex Int)| Gibt den Wert der angegebenen Spalte in der aktuellen Zeile dieses ResultSet-Objekts als Objekt in der Programmiersprache Java com.microsoft.sqlserver.jdbc.Geometry zurück.
|Geometry GetGeometry (Zeichenfolge Spaltenname)| Gibt den Wert der angegebenen Spalte in der aktuellen Zeile dieses ResultSet-Objekts als Objekt in der Programmiersprache Java com.microsoft.sqlserver.jdbc.Geometry zurück.
|Geography GetGeography (ColunIndex Int)| Gibt den Wert der angegebenen Spalte in der aktuellen Zeile dieses ResultSet-Objekts als Objekt in der Programmiersprache Java com.microsoft.sqlserver.jdbc.Geography zurück.
|Geography GetGeography (Zeichenfolge Spaltenname)| Gibt den Wert der angegebenen Spalte in der aktuellen Zeile dieses ResultSet-Objekts als Objekt in der Programmiersprache Java com.microsoft.sqlserver.jdbc.Geography zurück.

### <a name="geometry"></a>Geometry

|Methode|und Beschreibung|
|:------|:----------|
|Geometry STGeomFromText (Wkt String, Int SRID)| Konstruktor für eine Geometry-Instanz aus einer WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium), die um alle von der Instanz getragenen Z- und M-Werte (Höhe/Measure) erweitert wurde.
|Geometry STGeomFromWKB (Byte [] Wkb)| Konstruktor für eine Geometry-Instanz aus einer Darstellung des Typs „Open Geospatial-Konsortium (OGC) Well-Known Binary (WKB)“.
|Geometrien Deserialisieren (Byte [] Wkb)| Konstruktor für eine Geometry-Instanz aus einem internen SQL Server-Format für räumliche Daten.
|Geometry-Analyse (well-Zeichenfolge)| Konstruktor für eine Geometry-Instanz aus einer WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium). Räumliche Verweisbezeichner ist auf 0 eingestellt.
|Geometry, Point (Double X "," double "y" Int SRID)| Konstruktor für eine Geometry-Instanz, die die X- und Y-Werte und eine Spatial Reference Identifier eine Point-Instanz darstellt.
|Zeichenfolge STAsText()| Gibt die WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium) einer Geometry-Instanz zurück. Dieser Text enthält keine Z (Höhe)- oder M (Measure)-Werte, die von der Instanz getragen werden.
|Byte [] STAsBinary()| Gibt die WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium) einer Geometry-Instanz zurück. Dieser Wert enthält keine Z- oder M-Werte, die von der Instanz getragen werden.
|Byte [] serialize()| Gibt die Bytes zurück, die ein internes SQL Server-Format vom Geometry-Typ darstellen.
|Boolesche hasM()| Gibt zurück, wenn das Objekt einen M (Measure)-Wert enthält.
|Boolesche hasZ()| Gibt zurück, wenn das Objekt einen Z (Höhe)-Wert enthält.
|Doppelte getX()| Gibt die X-Koordinatenwert zurück.
|Doppelte getY()| Gibt die Y-Koordinatenwert zurück.
|Doppelte getM()| Gibt den Wert M (Measure) des Objekts.
|Doppelte getZ()| Gibt die Z-(Höhe)-Wert des Objekts zurück.
|Int getSrid()| Gibt den Wert (SRID, Spatial Reference Identifier).
|Boolesche isNull()| Gibt zurück, wenn das Geometry-Objekt auf null festgelegt ist.
|Int STNumPoints()| Gibt die Anzahl der Punkte in der Geometry-Objekt zurück.
|Zeichenfolge STGeometryType()| Gibt den durch eine geometry-Instanz dargestellten Open Geospatial Consortium (OGC)-Typnamen zurück.
|Zeichenfolge asTextZM()| Gibt die Well-Known Text (WKT)-Darstellung der Geometry-Objekt zurück.
|Zeichenfolge toString()| Gibt die Zeichenfolgendarstellung des Geometry-Objekts zurück.

### <a name="geography"></a>Geography

|Methode|und Beschreibung|
|:------|:----------|
|Geography STGeomFromText (Wkt String, Int SRID)| Konstruktor für eine Geography-Instanz aus einer WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium), die um alle von der Instanz getragenen Z- und M-Werte (Höhe/Measure) erweitert wurde.
|Geography STGeomFromWKB (Byte [] Wkb)| Konstruktor für eine Geography-Instanz aus einer Darstellung des Typs „Open Geospatial-Konsortium (OGC) Well-Known Binary (WKB)“.
|Geography Deserialisieren (Byte [] Wkb)| Konstruktor für eine Geography-Instanz aus einem internen SQL Server-Format für räumliche Daten.
|Geography-Analyse (well-Zeichenfolge)| Konstruktor für eine Geography-Instanz aus WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium). Räumliche Verweisbezeichner ist auf 0 eingestellt.
|Geografiepunkt (Lat, Lon double, Int SRID doppelte)| Konstruktor für eine Geography-Instanz, die mit Ihren Breitengrad- und Längengradwerten sowie mit einem Spatial Reference Identifier eine Point-Instanz darstellt.
|Zeichenfolge STAsText()| Gibt die WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium) einer Geography-Instanz zurück. Dieser Text enthält keine Z (Höhe)- oder M (Measure)-Werte, die von der Instanz getragen werden.
|Byte [] STAsBinary())| Gibt die WKB-Darstellung (Well-Known Binary) von OGC (Open Geospatial Consortium) einer Geography-Instanz zurück. Dieser Wert enthält keine Z- oder M-Werte, die von der Instanz getragen werden.
|Byte [] serialize()| Gibt die Bytes zurück, die ein internes SQL Server-Format vom Geography-Typ darstellen.
|Boolesche hasM()| Gibt zurück, wenn das Objekt einen M (Measure)-Wert enthält.
|Boolesche hasZ()| Gibt zurück, wenn das Objekt einen Z (Höhe)-Wert enthält.
|Doppelte getLatitude()| Der Breitengradwert zurückgegeben.
|Doppelte getLongitude()| Gibt den Wert der geografische Länge zurück.
|Doppelte getM()| Gibt den Wert M (Measure) des Objekts.
|Doppelte getZ()| Gibt die Z-(Höhe)-Wert des Objekts zurück.
|Int getSrid()| Gibt den Wert (SRID, Spatial Reference Identifier).
|Boolesche isNull()| Gibt zurück, wenn der Geography-Objekt auf null festgelegt ist.
|Int STNumPoints()| Gibt die Anzahl der Punkte in der Geography-Objekt zurück.
|Zeichenfolge STGeographyType()| Gibt den durch eine geography-Instanz dargestellten Open Geospatial Consortium (OGC)-Typnamen zurück.
|Zeichenfolge asTextZM()| Gibt die Well-Known Text (WKT)-Darstellung der Geography-Objekt zurück.
|Zeichenfolge toString()| Gibt die Zeichenfolgendarstellung des Geography-Objekts zurück.

## <a name="limitations-of-spatial-datatypes"></a>Einschränkungen für räumliche Datentypen

1. Die räumlichen Sub-Datentypen **CircularString**, **CompoundCurve**, **CurvePolygon**, und **FullGlobe** werden nur unterstützt, starten von SQLServer 2012 und höher.

2. Verschlüsselung kann nicht immer mit räumlichen Datentypen verwendet werden.

3. Gespeicherte Prozeduren, BulkCopy und Tabellenwertparameter Vorgänge werden mit räumlichen Datentypen derzeit nicht unterstützt.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Beispiel für räumliche Datentypen (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
