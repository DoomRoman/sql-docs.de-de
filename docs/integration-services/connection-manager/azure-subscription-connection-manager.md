---
title: Azure-Abonnementverbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpsubscrconn.f1
- sql14.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 82431376b5c7fbb052d5f36e158d269587dd7300
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47671418"
---
# <a name="azure-subscription-connection-manager"></a>Azure-Abonnementverbindungs-Manager
  Der **Azure HDInsight-Verbindungs-Manager** ermöglicht die Verbindung eines SSIS-Pakets mit einem Azure-Abonnement, indem die Werte verwendet werden, die Sie für die folgenden Eigenschaften angeben: Azure-Abonnement-ID und das Verwaltungszertifikat.  
  
 Der **Azure-Abonnement-Verbindungs-Manager** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
1.  Wählen Sie im oben angezeigten Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **Azure-Abonnement**aus, und klicken Sie auf **Hinzufügen**.  Das Dialogfeld **Azure-Abonnementverbindungs-Manager-Editor** wird geöffnet.  
  
    ![SSIS-AzureSubscriptionConnectionManager](../../integration-services/connection-manager/media/ssis-azuresubscriptionconnectionmanager.png)
  
2.  Geben Sie Ihre Azure-Abonnement-ID, die ein Azure-Abonnement eindeutig identifiziert, in **Azure-Abonnement-ID**ein.  Der Wert befindet sich im [Azure-Verwaltungsportal](https://manage.windowsazure.com) auf der Seite **Einstellungen** :  
  
    ![SSIS-AzureSettings-SubscriptionID](../../integration-services/connection-manager/media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  Wählen Sie **Verwaltungszertifikatspeicherort** und **Verwaltungszertifikatspeichername** aus den Dropdownlisten aus.  
  
4.  Geben Sie den **Fingerabdruck des Verwaltungszertifikats** ein, oder klicken Sie auf **Durchsuchen...**, um im ausgewählten Store ein Zertifikat auszuwählen. Das Zertifikat muss als Verwaltungszertifikat für das Abonnement hochgeladen werden. Klicken Sie hierzu auf der folgenden Seite des Azure-Portals auf **Hochladen** (in diesem [MSDN-Beitrag](https://msdn.microsoft.com/library/azure/gg551722.aspx) finden Sie weitere Informationen).  
  
     ![SSIS-AzureSettings-ManagementCertificate](../../integration-services/connection-manager/media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  Klicken Sie auf **Verbindung testen** , um die Verbindung zu testen.  
  
6.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
  
