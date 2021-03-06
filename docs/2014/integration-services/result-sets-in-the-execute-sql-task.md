---
title: Resultsets den Task "SQL ausführen" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- result sets [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: 62605b63-d43b-49e8-a863-e154011e6109
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 25f917dc3831f0915b87c4a93dbb4197a3d25df0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053366"
---
# <a name="result-sets-in-the-execute-sql-task"></a>Resultsets im Task „SQL ausführen“
  In einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket ist es vom Typ des von dem Task verwendeten SQL-Befehls abhängig, ob an den Task „SQL ausführen“ ein Resultset zurückgegeben wird. Beispielsweise gibt eine SELECT-Anweisung in der Regel ein Resultset zurück, eine INSERT-Anweisung jedoch nicht.  
  
 Auch der Inhalt des Resultsets ist von dem SQL-Befehl abhängig. Das Resultset einer SELECT-Anweisung kann beispielsweise keine Zeilen, eine Zeile oder viele Zeilen enthalten. Das Resultset einer SELECT-Anweisung, die eine Anzahl oder eine Summe zurückgibt, enthält jedoch nur eine einzige Zeile.  
  
 Das Arbeiten mit Resultsets in einem Task „SQL ausführen“ bedeutet mehr, als nur zu wissen, ob ein SQL-Befehl ein Resultset zurückgibt und was dieses Resultset enthält. Es müssen weitere Benutzungsanforderungen und Richtlinien beachtet werden, um Resultsets erfolgreich in einem Task „SQL ausführen“ zu verwenden. Diese Benutzungsanforderungen und Richtlinien werden am Ende dieses Themas behandelt:  
  
-   [Angeben eines Resultsettyps](#Result_set_type)  
  
-   [Auffüllen einer Variablen mit einem Resultset](#Populate_variable_with_result_set)  
  
-   [Konfigurieren von Resultsets legt in der Execute SQL Task Editor fest.](#Configure_result_sets)  
  
##  <a name="Result_set_type"></a> Legen Sie Typ angeben eines Resultsettyps  
 Der Task SQL ausführen unterstützt die folgenden Resultsettypen:  
  
-   Das Resultset **Keine** wird verwendet, wenn die Abfrage keine Ergebnisse zurückgibt. Beispielsweise wird dieses Resultset für Abfragen verwendet, die Datensätze in einer Tabelle hinzufügen, ändern und löschen.  
  
-   Das Resultset **Einzelne Zeile** wird verwendet, wenn die Abfrage nur eine Zeile zurückgibt. Beispielsweise wird dieses Resultset für eine SELECT-Anweisung verwendet, die eine Anzahl oder eine Summe zurückgibt.  
  
-   Das Resultset **Vollständiges Resultset** wird verwendet, wenn die Abfrage mehrere Zeilen zurückgibt. Beispielsweise wird dieses Resultset für eine SELECT-Anweisung verwendet, die alle Zeilen in einer Tabelle abruft.  
  
-   Das Resultset **XML** wird verwendet, wenn die Abfrage ein Resultset in einem XML-Format zurückgibt. Beispielsweise wird dieses Resultset für eine SELECT-Anweisung verwendet, die eine FOR XML-Klausel einschließt.  
  
 Wenn der Task SQL ausführen das Resultset **Vollständiges Resultset** verwendet und die Abfrage mehrere Rowsets zurückgibt, gibt der Task nur das erste Rowset zurück. Generiert dieses Rowset einen Fehler, wird der Fehler vom Task gemeldet. Von anderen Rowsets generierte Fehler werden vom Task nicht gemeldet.  
  
##  <a name="Populate_variable_with_result_set"></a> Auffüllen einer Variablen mit einem Resultset  
 Sie können das von einer Abfrage zurückgegebene Resultset an eine benutzerdefinierte Variable binden, falls der Resultsettyp eine einzelne Zeile, ein Rowset oder XML ist.  
  
 Ist der Resultsettyp **Einzelne Zeile**, können Sie eine Spalte im Rückgabeergebnis an eine Variable binden, indem Sie den Spaltennamen als Resultsetnamen verwenden. Sie können auch die Ordnungsposition der Spalte in der Spaltenliste als Resultsetnamen verwenden. Der Resultsetnamen für die Abfrage `SELECT Color FROM Production.Product WHERE ProductID = ?` könnte beispielsweise **Color** oder **0**sein. Gibt die Abfrage mehrere Spalten zurück, und Sie möchten auf die Werte in allen Spalten zugreifen, müssen Sie jede Spalte an eine andere Variable binden. Wenn Sie Spalten mithilfe von Zahlen als Resultsetnamen zu Variablen zuordnen, geben die Zahlen die Reihenfolge wieder, in der die Spalten in der Spaltenliste der Abfrage erscheinen. In der Abfrage `SELECT Color, ListPrice, FROM Production.Product WHERE ProductID = ?`verwenden Sie beispielsweise 0 für die Spalte **Color** und 1 für die Spalte **ListPrice** . Ob ein Spaltenname als Namen eines Resultsets verwendet werden kann, hängt davon ab, für welchen Anbieter der Task konfiguriert ist. Nicht alle Anbieter machen Spaltennamen verfügbar.  
  
 Bei einigen Abfragen, die einen einzelnen Wert zurückgeben, kann es sein, dass keine Spaltennamen enthalten sind. Beispielsweise gibt die `SELECT COUNT (*) FROM Production.Product` -Anweisung keinen Spaltennamen zurück. Sie können auf das Rückgabeergebnis zugreifen, indem Sie die Ordnungsposition 0 als Ergebnisnamen verwenden. Für den Zugriff auf das Rückgabeergebnis über den Spaltennamen muss in der Abfrage eine AS <Aliasname\<-Klausel enthalten sein, damit ein Spaltenname bereitgestellt werden kann. Die `SELECT COUNT (*)AS CountOfProduct FROM Production.Product`-Anweisung stellt die **CountOfProduct** -Spalte bereit. Sie können dann auf die Rückgabeergebnisspalte zugreifen, indem Sie den **CountOfProduct** -Spaltennamen bzw. die Ordnungsposition 0 verwenden.  
  
 Für den Resultsettyp **Vollständiges Resultset** oder **XML**müssen Sie 0 als Resultsetnamen verwenden.  
  
 Wenn Sie eine Variable einem Resultset mit dem Resultsettyp **Einzelne Zeile** zuordnen, muss die Variable einen Datentyp haben, der mit dem Datentyp der Spalte im Resultset kompatibel ist. So kann beispielsweise ein Resultset, das eine Spalte mit einem `String`-Datentyp enthält, keiner Variable mit einem numerischen Datentyp zugeordnet werden. Beim Festlegen der **TypeConversionMode** Eigenschaft `Allowed`, versucht der Task SQL ausführen, die Output-Parameter zu konvertieren und Abfrageergebnisse in den Datentyp der Variablen, die Ergebnisse zugewiesen sind.  
  
 Ein XML-Resultset kann nur einer Variable mit dem Datentyp `String` oder `Object` zugeordnet werden. Hat die Variable der `String` -Datentyp, der Task SQL ausführen gibt eine Zeichenfolge und die XML-Quelle können die XML-Daten verwenden. Hat die Variable der `Object` -Datentyp ist, gibt der Task SQL ausführen ein (DOM = Document Object Model)-Objekt zurück.  
  
 Ein **vollständiges Resultset** müssen zu einer Variablen zuordnen der `Object` -Datentyp. Als Ergebnis wird ein Rowsetobjekt zurückgegeben. Sie können einen Foreach-Schleifen-Container verwenden, um die Tabellenzeilenwerte, die in der Objektvariable gespeichert sind, in Paketvariablen zu extrahieren. Verwenden Sie dann ein Skripttask, um die Daten, die in Paketvariablen gespeichert sind, in eine Datei zu schreiben. Eine Demonstration zur Durchführung dieses Vorgangs unter Verwendung eines Foreach-Schleifen-Containers und eines Skripttasks finden Sie im CodePlex-Beispiel [Execute SQL Parameters and Result Sets](http://go.microsoft.com/fwlink/?LinkId=157863)(Ausführen von SQL-Parametern und Resultsets, in englischer Sprache), auf msftisprodsamples.codeplex.com.  
  
 In der folgenden Tabelle werden die Datentypen von Variablen zusammengefasst, die Resultsets zugeordnet werden können.  
  
|Typ des Resultsets|Datentyp der Variablen|Typ des Objekts|  
|---------------------|---------------------------|--------------------|  
|Einzelne Zeile|Jeder mit der Typspalte im Resultset kompatible Typ|Nicht verfügbar|  
|Vollständiges Resultset|`Object`|Wenn der Task einen systemeigenen Verbindungs-Manager, einschließlich der ADO, OLE DB, Excel und ODBC-Verbindungs-Manager, verwendet das zurückgegebene Objekt ist ein ADO `Recordset`.<br /><br /> Wenn der Task einen verwalteten Verbindungs-Manager, wie z. B. verwendet die [!INCLUDE[vstecado](../includes/vstecado-md.md)] Verbindungs-Manager, und klicken Sie dann auf das zurückgegebene Objekt ist ein `System.Data.DataSet`.<br /><br /> Sie können einen Skripttask verwenden, den Zugriff auf die `System.Data.DataSet` Objekt, wie im folgenden Beispiel gezeigt.<br /><br /> `Dim dt As Data.DataTable` <br /> `Dim ds As Data.DataSet = CType(Dts.Variables("Recordset").Value, DataSet)` <br /> `dt = ds.Tables(0)`|  
|XML|`String`|`String`|  
|XML|`Object`|Wenn der Task einen systemeigenen Verbindungs-Manager, einschließlich der ADO, OLE DB, Excel und ODBC-Verbindungs-Manager, verwendet das zurückgegebene Objekt ist ein `MSXML6.IXMLDOMDocument`.<br /><br /> Wenn der Task einen verwalteten Verbindungs-Manager, wie z. B. verwendet die [!INCLUDE[vstecado](../includes/vstecado-md.md)] Verbindungs-Manager das zurückgegebene Objekt ist ein `System.Xml.XmlDocument`.|  
  
 Die Variable kann im Bereich des Tasks SQL ausführen oder des Pakets definiert werden. Falls die Variable einen Paketbereich aufweist, ist das Resultset für andere Tasks und Container innerhalb des Pakets verfügbar sowie für alle Pakete, die von den Tasks "Paket ausführen" oder "DTS 2000-Paket ausführen" ausgeführt werden.  
  
 Wenn Sie einem **Single row** -Resultset eine Variable zuordnen, könnten von der SQL-Anweisung zurückgegebene Werte, die noch keine Zeichenfolgen sind, in Zeichenfolgen konvertiert werden. Dazu müssen die folgenden Bedingungen erfüllt sein:  
  
-   Die Eigenschaft **TypeConversionMode** ist auf "True" festgelegt. Sie haben den Eigenschaftswert im Eigenschaftenfenster oder mit dem **Editor für den Task "SQL ausführen"** festgelegt.  
  
-   Die Konvertierung führt nicht zu einem Abschneiden von Daten.  
  
 Informationen zum Laden eines Resultsets in eine Variable finden Sie unter [Zuordnen von Resultsets zu Variablen in einem Task „SQL ausführen“](control-flow/execute-sql-task.md).  
  
##  <a name="Configure_result_sets"></a> Konfigurieren von Resultsets legt der Task "SQL ausführen"  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften von Resultsets zu erhalten, die Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Editor für den Task SQL ausführen &#40;Seite Resultset&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 [Zuordnen von Resultsets zu Variablen in einem „SQL ausführen“-Task ](control-flow/execute-sql-task.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   CodePlex-Beispiel [Execute SQL Parameters and Result Sets](http://go.microsoft.com/fwlink/?LinkId=157863)(Ausführen von SQL-Parametern und Resultsets) auf msftisprodsamples.codeplex.com  
  
  
