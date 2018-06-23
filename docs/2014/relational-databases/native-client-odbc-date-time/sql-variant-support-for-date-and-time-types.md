---
title: Sql_variant-Unterstützung für Datums- und Uhrzeittypen | Microsoft Docs
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
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba207a78704e8e8582bffdd4df2b2846673ff58c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147891"
---
# <a name="sqlvariant-support-for-date-and-time-types"></a>Sql_variant-Unterstützung für Datums- und Uhrzeittypen
  In diesem Thema wird beschrieben, in welcher Weise der `sql_variant`-Datentyp die erweiterte Datums- und Uhrzeitfunktionalität unterstützt.  
  
 Das Spaltenattribut SQL_CA_SS_VARIANT_TYPE wird zur Rückgabe des C-Typs einer Variant-Ergebnisspalte verwendet. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] führt zusätzlich das Attribut sql_ca_ss_variant_sql_type eingeführt, mit dem der SQL-Typ einer variant-Ergebnisspalte in den Implementierungszeilendeskriptor (IRD) festgelegt. SQL_CA_SS_VARIANT_SQL_TYPE kann auch in Implementation Parameter Descriptor (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) verwendet werden, an die SQL-Typ, der eine SQL_SS_TIME2 oder SQL_SS_TIMESTAMPOFFSET-Parameter, der C-Typ SQL_C_BINARY ist mit dem Typ SQL_SS_VARIANT gebunden.  
  
 Die neuen Typen SQL_SS_TIME2 und SQL_SS_TIMESTAMPOFFSET können vom SQLColAttribute festgelegt werden. SQL_CA_SS_VARIANT_SQL_TYPE kann von SQLGetDescField zurückgegeben werden.  
  
 Für Ergebnisspalten konvertiert der Treiber Daten von Variant- zu Datum-/Uhrzeit-Typen. Weitere Informationen finden Sie unter [Konvertierungen von SQL-in C](datetime-data-type-conversions-from-sql-to-c.md). Wenn Spalten an SQL_C_BINARY gebunden werden, muss die Pufferlänge so groß sein, dass der Puffer die dem SQL-Typ entsprechende Struktur aufnehmen kann.  
  
 Für die SQL_SS_TIME2- und SQL_SS_TIMESTAMPOFFSET-Parameter konvertiert der Treiber, wie in der nachfolgenden Tabelle beschrieben, C-Werte in `sql_variant`-Werte. Wenn ein Parameter als SQL_C_BINARY gebunden ist und der Servertyp SQL_SS_VARIANT lautet, dann wird er als Binärwert behandelt, sofern die Anwendung SQL_CA_SS_VARIANT_SQL_TYPE nicht auf einen anderen SQL-Typ festgelegt hat. In diesem Fall hat QL_CA_SS_VARIANT_SQL_TYPE Vorrang; d. h. wenn SQL_CA_SS_VARIANT_SQL_TYPE festgelegt wurde, wird damit das Standardverhalten überschrieben, wonach der SQL-Varianttyp vom C-Typ abgeleitet wird.  
  
|C-Typ|Servertyp|Kommentare|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_STINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SSHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_USHORT|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_LONG|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SLONG|ssNoversion|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_ULONG|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SBIGINT|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_FLOAT|REAL|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_DOUBLE|FLOAT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_UTINYINT|TINYINT|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE wird nicht festgelegt.|  
|SQL_C_BINARY|Uhrzeit|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Skalierungsgruppe wird auf SQL_DESC_PRECISION (den *DecimalDigits* Parameter `SQLBindParameter`).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Skalierungsgruppe wird auf SQL_DESC_PRECISION (den *DecimalDigits* Parameter `SQLBindParameter`).|  
|SQL_C_TYPE_DATE|date|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Skalierungsgruppe wird auf SQL_DESC_PRECISION (den *DecimalDigits* Parameter `SQLBindParameter`).|  
|SQL_C_NUMERIC|Decimal|Genauigkeit ist festgelegt auf SQL_DESC_PRECISION (den *ColumnSize* Parameter `SQLBindParameter`).<br /><br /> Legen Sie die Skalierung auf SQL_DESC_SCALE (den *DecimalDigits* -Parameter von SQLBindParameter).|  
|SQL_C_SS_TIME2|Uhrzeit|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE wird ignoriert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datum und Uhrzeit-Verbesserungen &#40;ODBC&#41;](date-and-time-improvements-odbc.md)  
  
  