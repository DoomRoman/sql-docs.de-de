---
title: 'Aufgabe 8: Erstellen einer Verbunddomänenregel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 19b4922446f564435970fbb7f0422a3c98de48df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48151960"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>Aufgabe 8: Erstellen einer Verbunddomänenregel
  In dieser Aufgabe erstellen Sie eine Regel für die **Address Validation** verbunddomäne. Sie definieren eine domänenübergreifende Regel: Wenn **City** ist **Berlin**, **Zustand** muss **Zertifizierungsstelle** , in denen **City** und **Zustand** zwei Domänen sind.  
  
1.  Wechseln Sie im rechten Bereich die **VD-Regeln** Registerkarte.  
  
2.  Klicken Sie auf **Fügt eine neue domänenregel hinzu** auf der Symbolleiste.  
  
3.  Typ **City Regel** für **Namen** , und drücken Sie **EINGABETASTE**.  
  
4.  In der **erstellen Sie eine Regel** wählen Sie im Bereich **City** in der Domänenliste aus, und wählen Sie die Bedingung **Wert ist gleich** und **Berlin** für die -Wert.  
  
5.  In der **dann** wählen Sie im Bereich **Zustand** in der Domänenliste aus, und wählen **Wert ist gleich**, Typ **Zertifizierungsstelle** für Wert ein, und drücken Sie **Registerkarte**.  
  
     ![Verbunddomänenregel](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Verbunddomänenregel")  
  
6.  Klicken Sie auf **schließen** Schaltfläche am unteren Rand der Seite auf der Hauptseite des DQS-Client wechseln. In der nächsten Lektion veröffentlichen Sie die Wissensdatenbank. Beachten Sie, dass die Wissensdatenbank gesperrt ist (Schlosssymbol).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Konfigurieren eines Reference Data Service](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
