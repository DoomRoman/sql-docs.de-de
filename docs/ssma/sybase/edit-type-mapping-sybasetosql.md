---
title: Bearbeiten der Zuordnung (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 513f071a-d5e6-4ed5-acca-269bf76323c5
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 950155f09d2addb4240ffb0529d624542c545442
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779206"
---
# <a name="edit-type-mapping-sybasetosql"></a>Bearbeiten der Zuordnung (SybaseToSQL)
Die **bearbeiten Type Mapping** Dialogfeld können Sie angeben, wie Datentypen zwischen Quelle und Ziel-Datenbankobjekten zugeordnet sind.  
  
Sie können dieses Dialogfeld an mehreren Stellen zuzugreifen:  
  
-   Bei der Auswahl einer Quelldatenbank oder ein Datenbankobjekt, das **Type Mapping** -Registerkarte wird rechts neben dem Metadaten-Explorer angezeigt. Klicken Sie auf **hinzufügen** fügen Sie eine neue Zuordnung hinzu, oder klicken Sie auf **bearbeiten** so ändern Sie eine vorhandene Zuordnung.  
  
-   Auf der **Tools** klicken Sie im Menü **Projekteinstellungen** oder **Projekt Standardeinstellungen**. Wählen Sie im daraufhin angezeigten Dialogfeld **Type Mapping**. Klicken Sie auf **hinzufügen** fügen Sie eine neue Zuordnung hinzu, oder klicken Sie auf **bearbeiten** so ändern Sie eine vorhandene Zuordnung.  
  
Tabelle-spezifische Zuordnungen datentypzuordnungen für Projekte und Datenbank zu überschreiben. Datenbank-spezifische Zuordnungen überschreiben Projekt Zuordnungen.  
  
## <a name="options"></a>Tastatur  
**Quelltyp**  
Wählen Sie den Quelltyp für die Daten zum Zuweisen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Datentyp.  
  
Wenn der Datentyp mit variabler Länge ist, erscheint die folgenden Felder unter **Datenquellentyp**:  
  
**From**  
Geben Sie die minimale Länge für diese Zuordnung. Z. B. für die **Nchar** -Datentyp, können Sie 10, um anzugeben, dass diese Zuordnung für einen Bereich beginnend ist eingeben **nchar(10)**.  
  
**Aktion**  
Geben Sie die maximale Länge für diese Zuordnung. Z. B. für die **Nchar** -Datentyp, können Sie 20, um anzugeben, dass diese Zuordnung für einen Bereich endet am eingeben **nchar(20)**.  
  
**Zieltyp**  
Wählen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Datentyp, dem der Quelldatentyp zugeordnet ist. Wenn SSMA erstellt, die Tabelle oder eine gespeicherte Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], ändert sich der Quelldatentyp auf diesen Datentyp.  
  
Wenn der Datentyp mit variabler Länge ist, erscheint das folgende Feld unter **Zieltyp**:  
  
**Replace with**  
Geben Sie die Ziellänge für diese Zuordnung. Z. B. für die **Nvarchar** -Datentyp, können Sie 20, um anzugeben, dass die angegebene Quelle-Datentyp zugeordnet werden sollte eingeben **nvarchar(20)**.  
  
