---
title: Verwalten von Rollen mit SSMS | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82e232e34028ffd38942f95a74c5ef271d2b48bf
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="manage-roles-by-using-ssms"></a>Verwalten von Rollen mit SSMS 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Sie können Rollen für ein bereitgestelltes tabellarisches Modell mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen, bearbeiten und verwalten.  
  
 Aufgaben in diesem Thema:  
  
-   [So erstellen Sie eine neue Rolle](#bkmk_new_role)  
  
-   [So kopieren Sie eine Rolle](#bkmk_copy_role)  
  
-   [So bearbeiten Sie eine Rolle](#bkmk_edit_role)  
  
-   [So löschen Sie eine Rolle](#bkmk_deletet_role)  
  
> [!CAUTION]  
>  Wenn ein tabellarisches Modellprojekt, dessen Rollen mithilfe des Rollen-Managers in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] definiert wurden, erneut bereitgestellt wird, dann werden die in einem bereitgestellten tabellarischen Modell definierten Rollen überschrieben.  
  
> [!CAUTION]  
>  Wenn Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden, um eine Arbeitsbereichsdatenbank für tabellarische Modelle zu verwalten, während das Modellprojekt in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] geöffnet ist, kann die Datei Model.bim beschädigt werden. Wenn Sie Rollen für eine Arbeitsbereichsdatenbank für tabellarische Modelle erstellen und verwalten, verwenden Sie den Rollen-Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
###  <a name="bkmk_new_role"></a> So erstellen Sie eine neue Rolle  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die tabellarische Modelldatenbank, für die Sie eine neue Rolle erstellen möchten, klicken Sie mit der rechten Maustaste auf **Rollen**, und klicken Sie dann auf **Neue Rolle**.  
  
2.  Klicken Sie im Dialogfeld **Rolle erstellen** im Fenster "Seite auswählen" auf **Allgemein**.  
  
3.  Geben Sie im Fenster für allgemeine Einstellungen im Feld **Name** einen Namen für die Rolle ein.  
  
     Der Name der Standardrolle wird für jede neue Rolle automatisch inkrementell erhöht. Es wird empfohlen, einen Namen einzugeben, durch den der Elementtyp eindeutig identifiziert wird, beispielsweise "Finance Managers" oder "Human Resources Specialists".  
  
4.  Aktivieren Sie in **Legen Sie die Datenbankberechtigung für diese Rolle fest**eine der folgenden Berechtigungsoptionen:  
  
    |Berechtigung|Description|  
    |----------------|-----------------|  
    |**Vollzugriff (Administrator)**|Mitglieder können Änderungen am Modellschema vornehmen und alle Daten anzeigen.|  
    |**Datenbank verarbeiten**|Mitglieder können die Vorgänge Verarbeiten und Alles verarbeiten ausführen. Sie können weder das Modellschema ändern noch Daten anzeigen.|  
    |**Lesen**|Mitglieder dürfen Daten (basierend auf Zeilenfiltern) anzeigen, doch sie können keine Änderungen am Modellschema vornehmen.|  
  
5.  Klicken Sie im Dialogfeld **Rolle erstellen** im Fenster "Seite auswählen" auf **Mitgliedschaft**.  
  
6.  Klicken Sie im Mitgliedschaftseinstellungen-Fenster auf **Hinzufügen**, und fügen Sie dann im Dialogfeld **Benutzer oder Gruppen auswählen** die Windows-Benutzer oder die Gruppen hinzu, die Sie als Elemente hinzufügen möchten.  
  
7.  Wenn die Rolle, die Sie erstellen, Leseberechtigungen aufweist, können Sie Zeilenfilter für jede beliebige Tabelle hinzufügen, in der eine DAX-Formel verwendet wird. Hinzuzufügende Zeilenfilter, in der **Rolleneigenschaften - \<Rolename >** Dialogfeld **Seite auswählen**, klicken Sie auf **Zeilenfilter**.  
  
8.  Der Zeilenfilter-Fenster, wählen Sie eine Tabelle, und klicken Sie auf der **DAX-Filter** Feld, und klicken Sie dann in der **DAX-Filter - \<Tablename >** geben eine DAX-Formel.  
  
    > [!NOTE]  
    >  DAX-Filter - \<Tablename > Feld nicht enthalten einen AutoVervollständigen-Abfrage-Editor oder insert-Funktion. Um beim Schreiben einer DAX-Formel die Funktion zum AutoVervollständigen verwenden zu können, müssen Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]einen DAX-Formel-Editor verwenden.  
  
9. Klicken Sie auf **OK** , um die Rolle zu speichern.  
  
###  <a name="bkmk_copy_role"></a> So kopieren Sie eine Rolle  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die tabellarische Modelldatenbank, die die Rolle enthält, die Sie kopieren möchten, und erweitern Sie dann **Rollen**. Klicken Sie mit der rechten Maustaste auf die Rolle, und klicken Sie dann auf **Duplizieren**.  
  
###  <a name="bkmk_edit_role"></a> So bearbeiten Sie eine Rolle  
  
-   Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die tabellarische Modelldatenbank, die die Rolle enthält, die Sie bearbeiten möchten, und erweitern Sie dann **Rollen**. Klicken Sie mit der rechten Maustaste auf die Rolle, und klicken Sie dann auf **Eigenschaften**.  
  
     In der **Rolleneigenschaften** \<Rolename > Klicken Sie im Dialogfeld Berechtigungen ändern, hinzufügen oder Entfernen von Mitgliedern und Hinzufügen/Bearbeiten von Zeilenfilter.  
  
###  <a name="bkmk_deletet_role"></a> So löschen Sie eine Rolle  
  
-   Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die tabellarische Modelldatenbank, die die Rolle enthält, die Sie löschen möchten, und erweitern Sie dann **Rollen**. Klicken Sie mit der rechten Maustaste auf die Rolle, und klicken Sie dann auf **Löschen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
