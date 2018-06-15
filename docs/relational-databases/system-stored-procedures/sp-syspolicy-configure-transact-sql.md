---
title: Sp_syspolicy_configure (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_configure
- sp_syspolicy_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_configure
ms.assetid: 70c10922-9345-4190-ba69-808a43f760da
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c51d30c8453cd5a9c2a92a3eb2ad22016c461b8f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255934"
---
# <a name="spsyspolicyconfigure-transact-sql"></a>sp_syspolicy_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Konfiguriert Einstellungen für richtlinienbasierte Verwaltung, z. B. ob die richtlinienbasierte Verwaltung aktiviert ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_configure [ @name = ] 'name'  
    , [ @value = ] value  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@name =** ] **'***name***'**  
 Der Name der Einstellung, die Sie konfigurieren möchten. *Namen* ist **Sysname**ist erforderlich und darf nicht NULL oder eine leere Zeichenfolge.  
  
 *Namen* kann eine der folgenden Werte:  
  
-   'Enabled' – Gibt an, ob die richtlinienbasierte Verwaltung aktiviert ist.  
  
-   'HistoryRetentionInDays' – Gibt die Anzahl der Tage an, wie lange der Richtlinienauswertungsverlauf beibehalten werden soll. Bei der Einstellung 0 wird der Verlauf nicht automatisch entfernt.  
  
-   'LogOnSuccess' – Gibt an, ob die richtlinienbasierte Verwaltung erfolgreiche Richtlinienauswertungen protokolliert.  
  
 [  **@value =** ] *Wert*  
 Ist der Wert, der mit dem angegebenen Wert für anfallen *Namen*. *Wert* ist **Sql_variant**, und es ist erforderlich.  
  
-   Bei Angabe von "Enabled" für *Namen*, können Sie einen der folgenden Werte verwenden:  
  
    -   0 = Deaktiviert die richtlinienbasierte Verwaltung.  
  
    -   1 = Aktiviert die richtlinienbasierte Verwaltung.  
  
-   Bei Angabe von 'Historyretentionindays' für *Namen*, geben Sie die Anzahl der Tage als ganzzahligen Wert.  
  
-   Bei Angabe von 'LogOnSuccess' für *Namen*, können Sie einen der folgenden Werte verwenden:  
  
    -   0 = Protokolliert nur fehlerhafte Richtlinienauswertungen.  
  
    -   1 = Protokolliert sowohl erfolgreiche als auch fehlerhafte Richtlinienauswertungen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_configure im Kontext der Systemdatenbank msdb ausführen.  
  
 Um aktuelle Werte für diese Einstellungen anzuzeigen, fragen Sie die Systemsicht msdb.dbo.syspolicy_configuration ab.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer mit der Rolle PolicyAdministratorRole können Servertrigger erstellen und die Ausführung von Richtlinien planen. Dies kann sich auf die Arbeitsweise der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz auswirken. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmeldeinformationen, sollte die PolicyAdministratorRole-Rolle gewährt werden nur für Benutzer, die hinsichtlich der Kontrolle der Konfigurations der vertrauenswürdig sind die [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die richtlinienbasierte Verwaltung aktiviert.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'Enabled'  
, @value = 1;  
  
GO  
```  
  
 Im folgenden Beispiel wird die Richtlinienverlaufsbeibehaltung auf 14 Tage festgelegt.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'HistoryRetentionInDays'  
, @value = 14;  
  
GO  
```  
  
 Im folgenden Beispiel wird die richtlinienbasierte Verwaltung so konfiguriert, dass sowohl erfolgreiche als auch fehlerhafte Richtlinienauswertungen protokolliert werden.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'LogOnSuccess'  
, @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren Richtlinie der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [Sp_syspolicy_set_config_enabled &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-enabled-transact-sql.md)   
 [Sp_syspolicy_set_config_history_retention &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [Sp_syspolicy_set_log_on_success &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-log-on-success-transact-sql.md)  
  
  
