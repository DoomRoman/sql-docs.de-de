---
title: Ziel-Editor für SAP BW (Seite „Erweitert“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sapbwdestination.advanced.f1
ms.assetid: 862957db-bbc6-4dda-bc0e-591457f1baa7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5325e3382a1f0d1977273434e15857230131220a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756458"
---
# <a name="sap-bw-destination-editor-advanced-page"></a>Ziel-Editor für SAP BW (Seite Erweitert)
  Auf der Seite **Erweitert** im **Ziel-Editor für SAP BW** legen Sie erweiterte Einstellungen wie Paketgröße und Timoutinformationen fest.  
  
 Weitere Informationen zum SAP BW-Ziel von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW finden Sie unter [SAP BW-Ziel](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
 **So öffnen Sie die Seite "Erweitert"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem das SAP BW-Ziel enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das SAP BW-Ziel.  
  
3.  Klicken Sie im **Ziel-Editor für SAP BW**auf **Erweitert** , um die Seite **Erweitert** des Editors zu öffnen.  
  
## <a name="options"></a>Tastatur  
  
> [!NOTE]  
>  Wenn Sie nicht alle Werte kennen, die zur Konfiguration des Ziels erforderlich sind, müssen Sie ggf. Ihren SAP-Administrator um Unterstützung bitten.  
  
 **Paketgröße**  
 Geben Sie an, wie viele Datenzeilen auf einmal übertragen werden. Der optimale Wert für diesen Parameter hängt vom SAP NetWeaver BW-System und ggf. zusätzlichen Schritten zur Verarbeitung der Daten ab. In der Regel liefern Werte zwischen 2.000 und 20.000 die beste Leistung.  
  
 **Prozesskette auslösen**  
 (Optional) Geben Sie den Namen einer Prozesskette an, die ausgelöst wird, nachdem die Daten vollständig geladen wurden.  
  
 **Timeout beim Warten auf InfoPackage**  
 Geben Sie die maximale Anzahl von Sekunden an, die das Ziel wartet, bis das InfoPackage erstellt ist.  
  
 **Warten, bis Datenübertragung abgeschlossen ist**  
 Geben Sie an, ob das Ziel warten soll, bis das SAP NetWeaver BW-System die Daten vollständig geladen hat.  
  
 **InfoPackage nicht starten (nur warten)**  
 Geben Sie an, dass vom Ziel kein InfoPackage ausgelöst, sondern nur auf eine Benachrichtigung gewartet wird, dass das SAP NetWeaver BW-System mit dem Laden der Daten begonnen hat.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Ziel-Editor für SAP BW &#40;Seite „Verbindungs-Manager“&#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Ziel-Editor für SAP BW &#40;Seite „Zuordnungen“&#41;](../../integration-services/data-flow/sap-bw-destination-editor-mappings-page.md)   
 [Ziel-Editor für SAP BW &#40;Seite „Fehlerausgabe“&#41;](../../integration-services/data-flow/sap-bw-destination-editor-error-output-page.md)   
 [F1-Hilfe zum Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
