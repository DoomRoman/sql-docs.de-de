---
title: 'Lektion 8: Erstellen von Key Performance Indicators | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c98012d53ea9db1be2a8badc33c01b9c0cbf79af
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="lesson-7-create-key-performance-indicators"></a>Lektion 7: Erstellen von Leistungskennzahlen
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion erstellen Sie Leistungskennzahlen (Key Performance Indicators, KPIs). KPIs dienen zum Messen der Leistung eines Werts, der durch ein *Basismeasure* definiert wird, anhand eines *Zielwerts* , der ebenfalls durch ein Measure oder durch einen absoluten Wert definiert wird. In Clientanwendungen zur Berichtserstellung erhalten Geschäftsleute mit KPIs einen schnellen und einfachen Einblick in den insgesamten Geschäftserfolg bzw. können Trends leichter identifizieren. Weitere Informationen finden Sie unter [KPIs](../analysis-services/tabular-models/kpis-ssas-tabular.md).  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion, Sie sollten haben die vorherige Lektion abgeschlossen: [Lektion 6: Erstellen von Measures](../analysis-services/lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Erstellen von Leistungskennzahlen  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>So erstellen Sie eine InternetCurrentQuarterSalesPerformance-KPI  
  
1.  Klicken Sie im Modell-Designer auf die **FactInternetSales** Tabelle (Registerkarte).  
  
2.  Klicken Sie im Measureraster auf eine leere Zelle.  
  
3.  Geben Sie in der Bearbeitungsleiste über der Tabelle die folgende Formel ein: 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IFERROR([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    Dieses Measure dient als Basismeasure für den KPI.  
  
4.  Mit der rechten Maustaste **InternetCurrentQuarterSalesPerformance** > **KPI erstellen**.   
  
5.  Klicken Sie im Dialogfeld Key Performance Indicator (KPI) in **Ziel** wählen **Absolutwert**, und geben Sie dann **1.1**.  
  
7.  Geben Sie im linken (unteren) Schiebereglerfeld den Wert **1**und anschließend im rechten (oberen) Schiebereglerfeld **1,07**ein.  
  
8.  Wählen Sie unter **Symbolart auswählen**den Symboltyp Diamant (rot), Dreieck (gelb) oder Kreis (grün) aus.
  
    ![als-tabellarische-lesson7-kpi](../analysis-services/media/as-tabular-lesson7-kpi.png)
    
    > [!TIP]  
    > Beachten Sie die erweiterbare **Beschreibungen** Beschriftung unterhalb der verfügbaren symbolarten. Hiermit können Sie eine Beschreibung für die verschiedenen KPI-Elemente in Clientanwendungen typbeschreibungen eingeben.  
  
9. Klicken Sie auf **OK** , um den KPI abzuschließen.  
  
    Im measureraster, beachten Sie das Symbol neben dem **InternetCurrentQuarterSalesPerformance** Measure. Dieses Symbol gibt an, dass das Measure als Basiswert für einen KPI dient.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>So erstellen Sie eine InternetCurrentQuarterMarginPerformance-KPI  
  
1.  Im measureraster für die **FactInternetSales** Tabelle, klicken Sie auf eine leere Zelle.  
  
2.  Geben Sie in der Bearbeitungsleiste über der Tabelle die folgende Formel ein:  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Mit der rechten Maustaste **InternetCurrentQuarterMarginPerformance** > **KPI erstellen**.  
  
4.  Klicken Sie im Dialogfeld Key Performance Indicator (KPI) in **Ziel** wählen **Absolutwert**, und geben Sie dann **1.25**.   
  
5.  Verschieben Sie unter **Statusschwellenwerte definieren**den linken (unteren) Schieberegler, bis im Feld der Wert **0,8**angezeigt wird. Verschieben Sie anschließend den rechten (oberen) Schieberegler, bis im Feld **1,03**angezeigt wird.  
  
6.  Wählen Sie unter **Symbolart auswählen**den Symboltyp Diamant (rot), Dreieck (gelb) oder Kreis (grün) aus. Klicken Sie anschließend auf **OK**.  
  
## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 8: Erstellen von Perspektiven](../analysis-services/lesson-8-create-perspectives.md).
  
  
