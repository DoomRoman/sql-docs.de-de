---
title: Ausführen von Befehlen mit Tabellenwertparametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
ms.assetid: 7ecba6f6-fe7a-462a-9aa3-d5115b6d4529
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 943dba9ff3fbd04e8344ac4d325114ee9f05a2e2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428349"
---
# <a name="executing-commands-containing-table-valued-parameters"></a>Ausführen von Befehlen, die Tabellenwertparameter enthalten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die Ausführung eines Befehls, der Tabellenwertparameter enthält, erfordert zwei Phasen:  
  
1.  Angeben der Parametertypen  
  
2.  Binden der Parameterdaten  
  
## <a name="table-valued-parameter-specification"></a>Tabellenwertparameter-Spezifikation  
 Der Consumer kann den Typ des Tabellenwertparameters angeben. Diese Angabe enthält den Typnamen des Tabellenwertparameters. Sie umfasst auch den Schemanamen, wenn der benutzerdefinierte Tabellentyp für den Tabellenwertparameter nicht im aktuellen Standardschema für die Verbindung enthalten ist. Je nach Serverunterstützung kann der Consumer auch optionale Metadateninformationen angeben, wie beispielsweise die Sortierreihenfolge der Spalten. Zudem kann er angeben, dass alle Zeilen für bestimmte Spalten Standardwerte aufweisen sollen.  
  
 Um einen Tabellenwertparameter anzugeben, wird der Consumer ruft ISSCommandWithParamter::SetParameterInfo und ruft optional isscommandwithparameters:: SetParameterProperties. Für einen Tabellenwert-Parameter die *PwszDataSourceType* Feld in der DBPARAMBINDINFO-Struktur hat den Wert DBTYPE_TABLE. Die *UlParamSize* -Feld auf festgelegt wurde ~ 0, wenn diese Länge ist unbekannt. Bestimmte Eigenschaften für Tabellenwertparameter, wie z. B. Schemaname, Typname, Spaltenreihenfolge und Standardspalten, können über isscommandwithparameters:: SetParameterProperties festgelegt werden.  
  
## <a name="table-valued-parameter-binding"></a>Tabellenwertparameter-Bindung  
 Ein Tabellenwertparameter kann ein beliebiges Rowsetobjekt sein. Während der Ausführung liest der Anbieter beim Senden von Tabellenwertparametern an den Server aus diesem Objekt.  
  
 Um den Tabellenwertparameter zu binden, ruft der Consumer IAccessor:: CreateAccessor. Die *wType* -Feld der DBBINDING-Struktur für den Tabellenwertparameter wird auf DBTYPE_TABLE festgelegt. Die *pObject* -Element der DBBINDING-Struktur ist nicht NULL ist, und die *pObject*des *Iid* Member wird auf IID_IRowset oder ein anderes Objekt des Tabellenwertparameter-Rowset festgelegt. Schnittstellen. Die verbleibenden Felder in der DBBINDING-Struktur können in der gleichen Weise festgelegt werden wie für gestreamte BLOBs.  
  
 Für die Bindungen des Tabellenwertparameters und des einem Tabellenwertparameter zugeordneten Rowsetobjekts gelten die folgenden Einschränkungen:  
  
-   Die einzigen Statuswerte, die für Rowsetspaltendaten von Tabellenwertparametern zulässig sind, lauten DBSTATUS_S_ISNULL und DBSTATUS_S_OK. DBSTATUS_S_DEFAULT führt zu einem Fehler, und der gebundene Statuswert wird auf DBSTATUS_E_BADSTATUS festgelegt.  
  
-   Ein Tabellenwertparameter kann mit dem Status DBSTATUS_S_DEFAULT markiert werden. Die einzigen gültigen Werte sind DBSTATUS_S_DEFAULT und DBSTATUS_S_OK. Wenn der Status auf DBSTATUS_S_DEFAULT festgelegt ist, entspricht der Wert des Tabellenwertparameters einer leeren Tabelle.  
  
-   Schreibgeschützte Spalten in Tabellenwertparametern (Identitätsspalte und berechnete Spalte) müssen mit der SSPROP_PARAM_TABLE_DEFAULT_COLUMNS-Eigenschaft als Standard markiert werden. Spalten, die einen Standardwert aufweisen, müssen ebenfalls mit der SSPROP_PARAM_TABLE_DEFAULT_COLUMNS-Eigenschaft als Standard markiert werden. Dann kann der Standardwert als Datenwert einer Spalte für einen bestimmten Tabellenwertparameter verwendet werden. Der Anbieter ignoriert die Datenwerte, die an als Standard markierte Spalten gebunden sind.  
  
-   Für Spalten mit DBPROP_COL_AUTOINCREMENT oder SSPROP_COL_COMPUTED werden Daten an den Server gesendet, sofern nicht auch SSPROP_PARAM_TABLE_DEFAULT festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
