---
title: Sp_helpmergeconflictrows (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergeconflictrows_TSQL
- sp_helpmergeconflictrows
helpviewer_keywords:
- sp_helpmergeconflictrows
ms.assetid: 131395a5-cb18-4795-a7ae-fa09d8ff347f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 26bf2e89462c0096c9a6fd2a081cb72c68e9a32a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746578"
---
# <a name="sphelpmergeconflictrows-transact-sql"></a>sp_helpmergeconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Zeilen in der angegebenen Konflikttabelle zurück. Diese gespeicherte Prozedur wird auf dem Computer ausgeführt, auf dem die Konflikttabelle gespeichert ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergeconflictrows [ [ @publication = ] 'publication' ]  
        , [ @conflict_table = ] 'conflict_table'  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publsher_db' ]   
    [ , [ @logical_record_conflicts = ] logical_record_conflicts ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert **%**. Wenn die Veröffentlichung angegeben wird, werden alle Konflikte dieser Veröffentlichung zurückgegeben. Z. B. wenn die **MSmerge_conflict_Customers** Tabelle hat Konfliktzeilen für die **WA** und **Zertifizierungsstelle** Publications, übergeben einen Namen für die Veröffentlichung **Zertifizierungsstelle**  ruft Konflikte für die **Zertifizierungsstelle** Veröffentlichung.  
  
 [  **@conflict_table=**] **"***Conflict_table***"**  
 Der Name der Konflikttabelle. *Conflict_table* ist **Sysname**, hat keinen Standardwert. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden Konflikttabellen heißen mithilfe der Formatnamen mit **MSmerge_conflict_* Veröffentlichung *_* Artikel ***, mit einer Tabelle für die einzelnen veröffentlicht Artikel.  
  
 [ **@publisher=**] **'***publisher***'**  
 Der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 Ist der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@logical_record_conflicts=** ] *Logical_record_conflicts*  
 Gibt an, ob das Resultset Informationen zu Konflikten in logischen Datensätzen enthält. *Logical_record_conflicts* ist **Int**, hat den Standardwert 0. **1** bedeutet, dass Informationen zu Konflikten logischer Datensätze zurückgegeben werden.  
  
## <a name="result-sets"></a>Resultsets  
 **Sp_helpmergeconflictrows** gibt ein Resultset aus der Basistabellenstruktur und diese zusätzlichen Spalten besteht.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar(255)**|Ursprung des Konflikts.|  
|**conflict_type**|**int**|Code zur Angabe des Konflikttyps:<br /><br /> **1** = Update-Konflikt: der Konflikt wird erkannt, auf der Zeilenebene.<br /><br /> **2** = Spalte Update-Konflikt: der Konflikt auf Spaltenebene erkannt.<br /><br /> **3** = Update-Delete-WINS-Konflikt: der Löschvorgang gewinnt den Konflikt.<br /><br /> **4** = Update gewinnt Delete-Konflikt: der gelöschte Zeilen-GUID, die den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **5** = Fehler beim Hochladen Anweisung einfügen: der Einfügevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **6** = Fehler beim Einfügen herunterladen: der Einfügevorgang des Verlegers konnte nicht auf dem Abonnenten angewendet werden.<br /><br /> **7** = hochladen konnte nicht gelöscht: der Löschvorgang des Abonnenten konnte nicht an den Verleger hochgeladen werden.<br /><br /> **8** = Fehler beim Löschen von herunterladen: der Löschvorgang des Verlegers konnte nicht auf den Abonnenten heruntergeladen werden.<br /><br /> **9** = hochladen konnte nicht aktualisiert: der Updatevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **10** = Fehler beim Aktualisieren herunterladen: der Updatevorgang des Verlegers konnte nicht auf den Abonnenten angewendet werden.<br /><br /> **12** = logischer Datensatz Delete, Update gewinnt: der gelöschte logische Datensatz, der den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **13** = logischer Datensatz Konflikt Insert/Update: Einfügung in einen logischen Datensatz steht in Konflikt mit einem Update.<br /><br /> **14** = logischer Datensatz löschen Wins-Update-Konflikt: der aktualisierte logische Datensatz, der den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.|  
|**reason_code**|**int**|Fehlercode, der kontextabhängig sein kann.|  
|**reason_text**|**varchar(720)**|Fehlerbeschreibung, die kontextabhängig sein kann.|  
|**pubid**|**uniqueidentifier**|Veröffentlichungsbezeichner.|  
|**MSrepl_create_time**|**datetime**|Zeitpunkt, zu dem die Konfliktinformationen hinzugefügt wurden.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpmergeconflictrows** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle die **Db_owner** festen und **Replmonitor** Rolle in der Verteilungsdatenbank kann Ausführen**Sp_helpmergeconflictrows**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Konfliktinformationen für Mergepublikationen &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
