---
title: FULLTEXTSERVICEPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FULLTEXTSERVICEPROPERTY_TSQL
- FULLTEXTSERVICEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], properties
- FULLTEXTSERVICEPROPERTY function
- services [SQL Server], full-text search properties
- test
ms.assetid: b7dcacb0-af83-4807-9d1e-49148b56b59c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c56e70fc866c3666107677338feb3285cabb38b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812178"
---
# <a name="fulltextserviceproperty-transact-sql"></a>FULLTEXTSERVICEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen über die Eigenschaften der Volltext-Engine zurück. Diese Eigenschaften können mit **sp_fulltext_service** festgelegt und abgerufen werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FULLTEXTSERVICEPROPERTY ('property')  
```  
  
## <a name="arguments"></a>Argumente  
 *property*  
 Ein Ausdruck, der den Namen der Eigenschaft der Volltextdienstebene enthält. In der folgenden Tabelle finden Sie eine Liste der Eigenschaften und eine Beschreibung der zurückgegebenen Informationen.  
  
> [!NOTE]  
>  Die folgenden Eigenschaften werden in einem künftigen Release von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht mehr unterstützt: **ConnectTimeout**, **DataTimeout** und **ResourceUsage**. Vermeiden Sie die Verwendung dieser Eigenschaften in Neuentwicklungen, und planen Sie die Änderung von Anwendungen, die diese Eigenschaften derzeit verwenden.  
  
|Eigenschaft|value|  
|--------------|-----------|  
|**ResourceUsage**|Gibt 0 zurück. Wird nur aus Gründen der Abwärtskompatibilität unterstützt.|  
|**connecttimeout**|Gibt 0 zurück. Wird nur aus Gründen der Abwärtskompatibilität unterstützt.|  
|**IsFullTextInstalled**|Gibt an, ob die Volltextkomponente mit der aktuellen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert ist.<br /><br /> 0 = Volltext ist nicht installiert.<br /><br /> 1 = Volltext ist installiert.<br /><br /> NULL = Ungültige Eingabe oder Fehler.|  
|**DataTimeout**|Gibt 0 zurück. Wird nur aus Gründen der Abwärtskompatibilität unterstützt.|  
|**LoadOSResources**|Gibt an, ob Wörtertrennungen und Filter des Betriebssystems mit dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert und verwendet werden. Diese Eigenschaft ist standardmäßig deaktiviert, damit das Verhalten nicht versehentlich durch Betriebssystemupdates geändert wird. Wenn die Verwendung von Betriebssystemressourcen aktiviert wird, kann auf Ressourcen für Sprachen und Dokumenttypen zugegriffen werden, die beim [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Indexdienst registriert sind, für die jedoch keine instanzspezifische Ressource installiert wurde. Wenn Sie das Laden von Betriebssystemressourcen aktivieren, stellen Sie sicher, dass es sich bei den Betriebssystemressourcen um vertrauenswürdige signierte Binärdateien handelt. Andernfalls können sie nicht geladen werden, wenn **VerifySignature** auf 1 festgelegt ist.<br /><br /> 0 = Nur spezifische Filter und Wörtertrennungen für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden.<br /><br /> 1 = Betriebssystemfilter und Wörtertrennungen laden.|  
|**VerifySignature**|Gibt an, ob der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search-Dienst ausschließlich signierte Binärdateien lädt. Standardmäßig werden nur vertrauenswürdige signierte Binärdateien geladen.<br /><br /> 0 = Es wird nicht überprüft, ob Binärdateien signiert sind.<br /><br /> 1 = Es wird überprüft, ob ausschließlich vertrauenswürdige signierte Binärdateien geladen werden.|  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird geprüft, ob nur signierte Binärdateien geladen werden. Der Rückgabewert gibt an, dass diese Überprüfung nicht stattfindet.  
  
```  
SELECT fulltextserviceproperty('VerifySignature');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
0  
```  
  
 Beachten Sie, dass Sie die folgende `sp_fulltext_service`-Anweisung verwenden können, um die Signaturüberprüfung auf den Standardwert 1 zurückzusetzen:  
  
```  
EXEC sp_fulltext_service @action='verify_signature', @value=1;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)  
  
  
