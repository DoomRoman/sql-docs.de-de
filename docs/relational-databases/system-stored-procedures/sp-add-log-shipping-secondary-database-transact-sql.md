---
title: Sp_add_log_shipping_secondary_database (Transact-SQL) | Microsoft-Dokumentation
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
- sp_add_log_shipping_secondary_database
- sp_add_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_database
ms.assetid: d29e1c24-3a3c-47a4-a726-4584afa6038a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 56090e1f012bb0e9d490997c9b3dcc7e497641c9
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43035542"
---
# <a name="spaddlogshippingsecondarydatabase-transact-sql"></a>sp_add_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt fest, um eine sekundäre Datenbanken für den Protokollversand.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[, [ @restore_delay = ] 'restore_delay']  
[, [ @restore_all = ] 'restore_all']  
[, [ @restore_mode = ] 'restore_mode']  
[, [ @disconnect_users = ] 'disconnect_users']  
[, [ @block_size = ] 'block_size']  
[, [ @buffer_count = ] 'buffer_count']  
[, [ @max_transfer_size = ] 'max_transfer_size']  
[, [ @restore_threshold = ] 'restore_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@secondary_database** =] '*Secondary_database*"  
 Der Name der sekundären Datenbank. *secondary_database* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 [ **@primary_server** =] '*Primary_server*"  
 Der Name der primären Instanz von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Protokollversandkonfiguration. *primary_server* ist vom Datentyp **sysname** und darf nicht NULL sein.  
  
 [ **@primary_database** =] '*Primary_database*"  
 Der Name der Datenbank auf dem primären Server. *primary_database* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 [ **@restore_delay** =] '*Restore_delay*"  
 Die Zeit in Minuten, die der sekundäre Server vor dem Wiederherstellen einer bestimmten Sicherungsdatei wartet. *Restore_delay* ist **Int** und darf nicht NULL sein. Der Standardwert ist 0.  
  
 [ **@restore_all** =] '*Restore_all*"  
 Falls 1, stellt der sekundäre Server bei Ausführung des Wiederherstellungsauftrags alle verfügbaren Sicherungen des Transaktionsprotokolls wieder her. Andernfalls wird der Vorgang nach der Wiederherstellung einer Datei beendet. *Restore_all* ist **Bit** und darf nicht NULL sein.  
  
 [ **@restore_mode** = ] '*restore_mode*'  
 Der Wiederherstellungsmodus für die sekundäre Datenbank.  
  
 0 = Das Protokoll wird mit NORECOVERY wiederhergestellt.  
  
 1 = das Protokoll mit STANDBY wiederhergestellt.  
  
 *Wiederherstellen* ist **Bit** und darf nicht NULL sein.  
  
 [ **@disconnect_users** =] '*Disconnect_users*"  
 Falls 1, werden Benutzer beim Ausführen eines Wiederherstellungsvorgangs von der sekundären Datenbank getrennt. Standard = 0. *Trennen Sie* Benutzer **Bit** und darf nicht NULL sein.  
  
 [ **@block_size** =] '*Block_size*"  
 Die Größe in Bytes, die als Blockgröße für das Sicherungsmedium verwendet wird. *Block_size* ist **Int** hat den Standardwert 1.  
  
 [ **@buffer_count** =] '*Buffer_count*"  
 Die Gesamtanzahl der beim Sicherungs- oder Wiederherstellungsvorgang verwendeten Puffer. *Buffer_count* ist **Int** hat den Standardwert 1.  
  
 [ **@max_transfer_size** =] '*Max_transfer_size*"  
 Die Größe der maximalen Eingabe- oder Ausgabeanforderung in Bytes, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an das Sicherungsmedium ausgegeben wird. *Max_transfersize* ist **Int** und kann NULL sein.  
  
 [ **@restore_threshold** =] '*Restore_threshold*"  
 Die Anzahl der zulässigen Minuten zwischen Wiederherstellungsvorgängen, bevor eine Warnung generiert wird. *Restore_threshold* ist **Int** und darf nicht NULL sein.  
  
 [ **@threshold_alert** =] '*Threshold_alert*"  
 Die Warnung, die bei Überschreiten des Sicherungsschwellenwerts ausgelöst wird. *Threshold_alert* ist **Int**, hat den Standardwert 14,420.  
  
 [ **@threshold_alert_enabled** =] '*Threshold_alert_enabled*"  
 Gibt an, ob eine Warnung ausgelöst wird, wenn *Backup_threshold* überschritten wird. Der Standardwert 1 bedeutet, dass die Warnung ausgelöst wird. *Threshold_alert_enabled* ist **Bit**.  
  
 [ **@history_retention_period** =] '*History_retention_period*"  
 Die Zeitdauer (in Minuten), für die der Verlauf beibehalten wird. *history_retention_period* ist vom Datentyp **int**. Der Standardwert ist NULL. Falls nichts angegeben wird, wird ein Wert von 14420 verwendet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_add_log_shipping_secondary_database** muss ausgeführt werden, aus der **master** Datenbank auf dem sekundären Server. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  **Sp_add_log_shipping_secondary_primary** aufgerufen werden soll, bevor Sie diese gespeicherte Prozedur, um die primären Protokollversand-Datenbankinformationen auf dem sekundären Server zu initialisieren.  
  
2.  Fügt einen Eintrag für die sekundäre Datenbank in **Log_shipping_secondary_databases** unter Verwendung der angegebenen Argumente.  
  
3.  Hinzufügen eines lokalen Überwachungsdatensatzes in **Log_shipping_monitor_secondary** auf dem sekundären Server mithilfe bereitgestellter Argumente.  
  
4.  Falls der Überwachungsserver vom sekundären Server übereinstimmt, fügt ein Überwachungsdatensatzes **Log_shipping_monitor_secondary** auf dem Überwachungsserver mithilfe angegebener Parameter.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die Verwendung der **Sp_add_log_shipping_secondary_database** gespeicherte Prozedur zum Hinzufügen der Datenbank **LogShipAdventureWorks** als sekundäre Datenbank in einer Protokollversandkonfiguration mit der primären Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] auf dem primären Server tribeca befindet.  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_database   
@secondary_database = N'LogShipAdventureWorks'   
,@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks2012'   
,@restore_delay = 0   
,@restore_mode = 1   
,@disconnect_users = 0   
,@restore_threshold = 45     
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440 ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
