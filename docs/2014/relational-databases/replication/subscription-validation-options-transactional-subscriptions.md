---
title: Optionen für die Abonnementüberprüfung (Transaktionsabonnements) | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 37fdbafa1f6dbdbc593277e4e5d4df37ad054d82
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230660"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Optionen für die Abonnementüberprüfung (Transaktionsabonnements)
  Mithilfe des Dialogfelds **Optionen für die Abonnementüberprüfung** können Sie angeben, ob zur Überprüfung nur die Zeilenanzahl oder die Zeilenanzahl und eine binäre Prüfsumme verwendet werden soll.  
  
## <a name="options"></a>Tastatur  
 **Überprüfen Sie, ob der Abonnent die gleiche Anzahl von Zeilen mit replizierten Daten enthält wie der Verleger**  
 Wählen Sie den Typ der Zeilenanzahlüberprüfung aus, die ausgeführt werden soll. Bei Oracle-Veröffentlichungen ist die einzig verfügbare Option **Tatsächliche Zeilenanzahl durch direktes Abfragen der Tabellen berechnen**.  
  
 **Prüfsummen vergleichen, um die Zeilendaten zu überprüfen**  
 Zusätzlich zum Einbinden einer Reihe von Zeilen auf Verleger- und Abonnentenebene wird eine Prüfsumme aller Daten mit dem binären Prüfsummenalgorithmus berechnet. Ist die Zeilenanzahl fehlerhaft, wird die Berechnung der Prüfsumme nicht ausgeführt.  
  
 **Verteilungs-Agent nach Abschluss der Überprüfung beenden**  
 Standardmäßig wird der Verteilungs-Agent ununterbrochen ausgeführt. Wählen Sie diese Option aus, um den Agent nach dem Ausführen der Überprüfung zu beenden. Dadurch können Sie prüfen, ob die Überprüfung erfolgreich verlaufen ist, bevor die Replikation der Daten an den Abonnenten fortgesetzt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Überprüfen der Daten am Abonnenten](validate-data-at-the-subscriber.md)   
 [Überprüfen von replizierten Daten](validate-replicated-data.md)  
  
  
