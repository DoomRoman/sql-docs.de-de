---
title: Unterstützung des OLE DB-Tabellenwertparameter-Typ | Microsoft Docs
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
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4b6416715cc6226766773d3f1d630dc2e42e1e37
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147657"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB-Typunterstützung für Tabellenwertparameter
  In diesem Thema wird die OLE DB-Typunterstützung für Tabellenwertparameter beschrieben.  
  
## <a name="table-valued-parameter-rowset-object"></a>Tabellenwertparameter-Rowsetobjekt  
 Sie können ein spezielles Rowsetobjekt für Tabellenwertparameter erstellen. Sie erstellen das Tabellenwertparameter-Rowsetobjekt mit ITableDefinitionWithConstraints::CreateTableWithConstraints oder IOpenRowset:: OPENROWSET. Zu diesem Zweck legen Sie die *eKind* Mitglied der *pTableID* -Parameters auf dbkind_guid_name fest, und geben Sie die CLSID_ROWSET_INMEMORY der *Guid* Member. Der servertypname für den Tabellenwertparameter muss angegeben werden, der *PwszName* Mitglied *pTableID* Verwendung IOpenRowset:: OPENROWSET. Das Tabellenwertparameter-Rowsetobjekt verhält sich wie ein reguläres Objekt des OLE DB-Anbieters von SQL Server Native Client.  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtypetable"></a>DBTYPE_TABLE  
 Der neue Typ DBTYPE_TABLE stellt einen Tabellentyp dar. Dieser Typ gibt Tabellenwertparameter in verschiedenen OLE DB-Schnittstellen an, wo ein DBTYPE erforderlich ist.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE hat das gleiche Format wie DBTYPE_IUNKNOWN. Es ist ein Zeiger auf ein Objekt im Datenpuffer. Für die vollständige Spezifikation in den Bindungen füllt der Consumer den DBOBJECT-Puffer mit *Iid* auf eine der Schnittstellen des Rowsetobjekts (IID_IRowset) festgelegt. Wenn DBOBJECT in den Bindungen angegeben wird, wird der IID_IRowset davon ausgegangen werden.  
  
 Konvertierungen zu und von DBTYPE_TABLE für andere Typen werden nicht unterstützt. IConvertType::CanConvert gibt S_FALSE für nicht unterstützte Konvertierung für jede Anforderung als DBTYPE_TABLE an DBTYPE_TABLE Konvertierung zurück. Dies geht davon aus DBCONVERTFLAGS_PARAMETER für das Command-Objekt.  
  
## <a name="methods"></a>Methoden  
 Weitere Informationen zu OLE DB-Methoden, die Tabellenwertparameter unterstützen, finden Sie unter [OLE DB Table-Valued Parameter unterstützt &#40;Methoden&#41;](ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Eigenschaften  
 Weitere Informationen zu OLE DB-Eigenschaften, die Tabellenwertparameter unterstützen, finden Sie unter [OLE DB Table-Valued Parameter unterstützt &#40;Eigenschaften&#41;](ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  