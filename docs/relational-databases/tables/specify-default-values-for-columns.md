---
title: Angeben von Standardwerten für Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 171f7806dacb158bb1ad596f300787f5b6c8ada9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33009607"
---
# <a name="specify-default-values-for-columns"></a>Angeben von Standardwerten für Spalten
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Sie können einen Standardwert angeben, der mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in die Spalte in [!INCLUDE[tsql](../../includes/tsql-md.md)]eingegeben wird. Wenn kein Standardwert zugewiesen ist und Benutzer die Spalte leer lassen, wird wie folgt verfahren:  
  
-   Wenn NULL-Werte zugelassen sind, wird NULL in die Spalte eingefügt.  
  
-   Wenn NULL-Werte nicht zugelassen sind, bleibt die Spalte leer. Die Zeile kann jedoch erst dann gespeichert werden, wenn ein Wert in die Spalte eingegeben wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So geben Sie einen benutzerdefinierten Standardwert an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn die Eingabe im Feld **Standardwert** einen gebundenen Standardwert ersetzt (der ohne Klammern angezeigt wird), werden Sie aufgefordert, die Bindung des Standardwerts aufzuheben und ihn durch den neuen Standardwert zu ersetzen.  
  
-   Werte für Zeichenfolgen müssen in einfache Anführungszeichen (') gesetzt werden. Verwenden Sie keine doppelten Anführungszeichen ("), da diese für in Anführungszeichen gesetzte Bezeichner reserviert sind.  
  
-   Um einen numerischen Standardwert einzugeben, geben Sie die Zahl ohne Anführungszeichen ein.  
  
-   Wenn Sie ein Objekt bzw. eine Funktion eingeben, geben Sie den Namen des Objekts bzw. der Funktion ein, ohne ihn in Anführungszeichen einzuschließen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>So geben Sie einen Standardwert für eine Spalte an  
  
1.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle mit den Spalten, für die Sie Dezimalstellen ändern möchten, und klicken Sie auf **Entwerfen**.  
  
2.  Wählen Sie die Spalte aus, für die Sie einen Standardwert angeben möchten.  
  
3.  Geben Sie den neuen Standardwert auf der Registerkarte **Spalteneigenschaften** in der Eigenschaft **Standardwert oder -bindung** ein.  
  
    > [!NOTE]  
    >  Um einen numerischen Standardwert einzugeben, geben Sie die Zahl ein. Geben Sie bei einem Objekt oder einer Funktion den entsprechenden Namen ein. Geben Sie für einen alphanumerischen Standardwert den Wert in einfachen Anführungszeichen ein.  
  
4.  Klicken Sie im Menü **Datei** auf **Speichern** > *Tabellenname*.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>So geben Sie einen Standardwert für eine Spalte an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
