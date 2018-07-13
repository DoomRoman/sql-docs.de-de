---
title: Umbenennen von Sichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 64ab38a3e5ed5631e18293f78fae43ef8b77fcf4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204930"
---
# <a name="rename-views"></a>Umbenennen von Sichten
  Sie können in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] eine Sicht mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]umbenennen.  
  
> [!WARNING]  
>  Wenn Sie eine Sicht umbenennen, kann es vorkommen, dass Code und Anwendungen, die von der Sicht abhängen, fehlerhaft ausgeführt werden. Dies schließt andere Sichten, Abfragen, gespeicherte Prozeduren, benutzerdefinierte Funktionen und Clientanwendungen ein. Beachten Sie, dass dabei ein Fehler durch Verkettung weitere Fehler nach sich ziehen kann.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Security](#Security)  
  
-   **So benennen Sie eine Sicht um mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After renaming a view](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
 Rufen Sie eine Liste aller Abhängigkeiten der Sicht ab. Für alle Objekte, Skripts oder Anwendungen, die auf die Sicht verweisen, muss der neue Name der Sicht festgelegt werden. Weitere Informationen finden Sie unter [Get Information About a View](get-information-about-a-view.md). Es ist ratsam, die Sicht zu verwerfen und unter einem neuen Namen neu zu erstellen, anstatt die Sicht umzubenennen. Indem Sie die Sicht neu erstellen, aktualisieren Sie die Abhängigkeitsinformationen für die Objekte, auf die in der Sicht verwiesen wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für SCHEMA oder die CONTROL-Berechtigung für OBJECT sowie die CREATE VIEW-Berechtigung in der Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>So benennen Sie eine Sicht um  
  
1.  Erweitern Sie im **Objekt-Explorer**die Datenbank mit der Sicht, die Sie umbenennen möchten, und erweitern Sie dann den Ordner **Sicht** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Sicht, die Sie umbenennen möchten, und wählen Sie die Option **Umbenennen**.  
  
3.  Geben Sie den neuen Namen der Sicht ein.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So benennen Sie eine Sicht um**  
  
 Sie können den Namen der Sicht zwar mit **sp_rename** ändern, aber es wird empfohlen, die vorhandene Sicht zu löschen und dann unter einem neuen Namen neu zu erstellen.  
  
 Weitere Informationen finden Sie unter [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) und [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).  
  
##  <a name="FollowUp"></a> Nachverfolgung: Nach dem Umbenennen einer Sicht  
 Stellen Sie sicher, dass alle Objekte, Skripts und Anwendungen, die auf den alten Namen der Sicht verweisen, jetzt den neuen Namen verwenden.  
  
  
