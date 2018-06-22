---
title: Anwenden einer XSL-Transformation (SQLXMLOLEDB-Anbieter) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 170bed8eece89add964d3f8f0b3ab3fe46552b26
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046414"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a>Anwenden einer XSL-Transformation (SQLXMLOLEDB-Anbieter)
  In dieser ADO-Beispielanwendung wird eine SQL-Abfrage ausgeführt und auf das Ergebnis eine XSL-Transformation angewendet. Festlegen der ClientSideXML-Eigenschaft auf "true" erzwingt die Verarbeitung des Rowsets auf der Clientseite. Der Befehlsdialekt wird auf {5d531cb2-e6ed-11d2-b252-00c04f681b71} festgelegt, da die SQL-Abfrage in einer Vorlage angegeben ist und dieser Dialekt angegeben werden muss, wenn eine Vorlage ausgeführt wird. Die Xsl-Eigenschaft gibt die XSL-Datei zu verwenden, um die Transformation anzuwenden. Der Wert der Eigenschaft des Basis-Pfad wird verwendet, um nach der XSL-Datei zu suchen. Wenn Sie einen Pfad im Wert der XSL-Eigenschaft angeben, ist der Pfad relativ zum Pfad, der in der Basis-Pfad-Eigenschaft angegeben ist.  
  
 In diesem Beispiel wird gezeigt, wie die folgenden für den SQLXMLOLEDB-Anbieter spezifischen Eigenschaften verwendet werden:  
  
-   ClientSideXML  
  
-   XSL  
  
 In dieser clientseitigen ADO-Beispielanwendung wird eine XML-Vorlage, die aus einer einfachen SQL-Abfrage besteht, auf dem Server ausgeführt.  
  
 Da die ClientSideXML-Eigenschaft auf "true" festgelegt ist, wird die SELECT-Anweisung ohne die FOR XML-Klausel an den Server gesendet. Der Server führt die Abfrage aus und gibt ein Rowset an den Client zurück. Der Client wendet anschließend die FOR XML-Transformation auf das Rowset an und generiert das XML-Dokument.  
  
 Die Xsl-Eigenschaft wird in der Anwendung angegeben. Daher gilt die XSL-Transformation im XML-Dokument, das auf dem Client generiert wird, und das Ergebnis ist eine zweispaltige Tabelle.  
  
 Zum Ausführen des Vorlagenbefehls muss für die XML-Vorlage der Dialekt {5d531cb2-e6ed-11d2-b252-00c04f681b71} angegeben werden.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen. In diesem Beispiel wird überdies die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client als Datenanbieter angegeben, was die Installation zusätzlicher Netzwerkclientsoftware erforderlich macht. Weitere Informationen finden Sie unter [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 Im Folgenden finden Sie die XSL-Vorlage. Aus der Anwendung dieser XSL-Vorlage ergibt sich eine zweispaltige Tabelle.  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  