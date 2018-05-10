---
title: Sicherheit in tabellarischen Modellen auf Objektebene | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a52b94dc7056b52892e744485be979a19808f6a1
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="object-level-security"></a>Sicherheit auf Nachrichtenebene-Objekt
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Daten für die modellelementsicherheit wird gestartet, bei der Implementierung von effektiv [Rollen](../../analysis-services/tabular-models/roles-ssas-tabular.md) und Filter auf Zeilenebene Benutzerberechtigungen für Datenmodellobjekte und Daten zu definieren. Tabellenmodelle 1400 ab, Sie können auch Sicherheitsfunktionen auf Objektebene, gehören auf Tabellenebene Sicherheit und die Sicherheit auf Nachrichtenebene Spalte in der [Rollenobjekt](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md).

## <a name="table-level-security"></a>Sicherheit auf Tabellenebene

Klicken Sie mit Sicherheit auf Tabellenebene Sie können nicht nur den Zugriff auf Daten aus Tabellen, aber auch vertrauliche Tabellennamen, Spaltennamen, hilft, verhindern, dass böswillige Benutzer ermitteln, wenn eine Tabelle vorhanden ist. 

 Sicherheit auf Tabellenebene wird festgelegt, in den JSON-basierte Metadaten in die Model.bim [Tabular Model Scripting Language (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md), oder [tabellarisches Objekt Model (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md). Festlegen der **MetadataPermission** Eigenschaft des der **TablePermissions** -Klasse in der [Rollen-Objekt](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) zu **keine**.

In diesem Beispiel wird die MetadataPermission-Eigenschaft der Klasse TablePermissions für die Product-Tabelle auf none festgelegt:

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Product",
        "metadataPermission": "none"
      }
    ]
  }
```

## <a name="column-level-security"></a>Sicherheit auf Spaltenebene

Ähnelt der Sicherheit auf Tabellenebene mit Sicherheit auf Spaltenebene können Sie nicht nur Zugriff auf Spaltendaten, sondern auch vertrauliche Spaltennamen, beschränken hilft zu verhindern, dass böswillige Benutzer aus eine Spalte zu ermitteln.

 Sicherheit auf Spaltenebene festgelegt ist, in den JSON-basierte Metadaten in die Model.bim [Tabular Model Scripting Language (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md), oder [tabellarisches Objekt Model (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md). Festlegen der **MetadataPermission** Eigenschaft des der **ColumnPermissions** -Klasse in der [Rollen-Objekt](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) zu **keine**.

In diesem Beispiel wird die MetadataPermission-Eigenschaft der Klasse ColumnPermissions für die Rate der Base-Spalte in der Employees-Tabelle auf none festgelegt:

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Employee",
        "columnPermissions": [
          {
            "name": "Base Rate",
            "metadataPermission": "none"
          }
        ]
      }
    ]
  }
```

## <a name="restrictions"></a>Einschränkungen

*  Sicherheit auf Nachrichtenebene Tabelle kann nicht für ein Modell festgelegt werden, wenn er eine beziehungskette zuwiderläuft. Zur Entwurfszeit wird ein Fehler generiert.
 Z. B. wenn Beziehungen zwischen Tabellen A und B, und B und C vorhanden sind, nicht Tabelle b gesichert werden Wenn Tabelle B gesichert ist, kann keine Abfrage in Tabelle A die Beziehungen zwischen Tabellen A und B, und B und C. Datenübertragung. In diesem Fall kann eine separate Beziehung zwischen Tabellen A und b konfiguriert werden

    ![Sicherheit auf Tabellenebene](../../analysis-services/tabular-models/media/ssas-ols.png)  


*  Sicherheit auf Zeilenebene und Sicherheit auf Nachrichtenebene Objekt können nicht aus anderen Rollen kombiniert werden, da sie unbeabsichtigte Zugriff auf gesicherte Daten führen könnte. Zur Abfragezeit für Benutzer, die Mitglieder dieser Kombination von Rollen sind, wird ein Fehler generiert.

*  Dynamische Berechnungen (Measures, KPIs, DetailRows) werden automatisch eingeschränkt, wenn sie einer gesicherten Tabelle oder Spalte verweisen. Zwar gibt es keinen Mechanismus, um ein Measure explizit zu sichern, ist es möglich, ein Measure implizit zu sichern, indem Sie die Aktualisierung des Ausdrucks, der auf einer gesicherten Tabelle oder Spalte verweisen.

*  Beziehungen, die eine gesicherte Spalte verweisen arbeiten, solange die Tabelle, der in die Spalte ist nicht geschützt sind.




## <a name="see-also"></a>Siehe auch  
[Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
[Roles-Objekt (TMSL)](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)  
[Tabular Model Scripting Language (TMSL) (Skriptsprache für tabellarische Modelle (TMSL))](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
[Tabellarischen Objektmodell (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md).

  
