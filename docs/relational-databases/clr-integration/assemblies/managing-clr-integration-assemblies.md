---
title: Verwalten von CLR-Integrationsassemblys | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
caps.latest.revision: 56
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 83dbc743bc6c11e0ab6e197426f5012573b8badf
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694191"
---
# <a name="managing-clr-integration-assemblies"></a>Verwalten von CLR-Integrationsassemblys
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Verwalteter Code wird kompiliert und dann in Einheiten bereitgestellt, die Assembly genannt werden. Eine Assembly wird als DLL oder ausführbare Datei (EXE) gepackt. Während eine ausführbare Datei auch alleine ausgeführt werden kann, muss eine DLL in einer vorhandenen Anwendung gehostet werden. Verwaltete DLL-Assemblys in geladen und von gehostet werden können [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist es erforderlich, die Assembly mit einer CREATE ASSEMBLY-Anweisung in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank zu registrieren, bevor sie in den Prozess geladen und verwendet werden kann. Assemblys können auch von einer neueren Version aus mithilfe der ALTER ASSEMBLY-Anweisung aktualisiert oder aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe der DROP ASSEMBLY-Anweisung entfernt werden.  
  
 Assemblyinformationen befindet sich in der **Sys. assembly_files** Tabelle in der Datenbank, in dem die Assembly installiert wurde. Die **Sys. assembly_files** Tabelle enthält die folgenden Spalten.  
  
|Spalte|Description|  
|------------|-----------------|  
|assembly_id|Der für die Assembly definierte Bezeichner. Diese Nummer wird allen Objekten mit Bezug auf dieselbe Assembly zugewiesen.|  
|NAME|Der Name des Objekts.|  
|file_id|Eine Zahl, welche jedes Objekt, wobei das erste Objekt zugeordneten einer bestimmten **Assembly_id** wird der Wert 1 zugewiesen. Wenn mehrere Objekte mit demselben **Assembly_id**, wird jeder nachfolgende **File_id** -Wert um 1 erhöht.|  
|content|Die Hexadezimaldarstellung der Assembly oder Datei.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen von Assemblys](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 Erläutert das Erstellen der Assemblys SAFE, EXTERNAL_ACCESS und UNSAFE CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Ändern einer Assembly](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 Beschreibt das Aktualisieren von CLR-Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Löschen von Assemblys](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 Erläutert das Löschen von CLR-Assemblys aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [CLR-Integration und Codezugriffssicherheit](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  
