---
title: SQL-Eigenschaft – Beispiel (VBScript) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- SQL property [ADO], VBScript example
ms.assetid: 32c33bcf-3320-4836-9e2e-99c8978ce581
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b76b4bfc372c688101882a7250c54a4d4c0c536c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673531"
---
# <a name="sql-property-example-vbscript"></a>SQL-Eigenschaft – Beispiel (VBScript)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Der folgende Code zeigt, wie Sie festlegen der [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) SQL-Parameter zur Entwurfszeit und die Bindung, die mit einem datenbewusste Steuerelement unter Verwendung der Datenbank namens *Pubs*, die im Lieferumfang von Microsoft SQL Server. Das Beispiel zu testen, kopieren den folgenden Code in ein normales ASP-Dokument mit dem Namen **SQLDesignVBS.asp** auf Ihrem Webserver.  
  
```  
<!-- BeginSQLDesignVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>SQL Property Example (VBScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>SQL Property Example (VBScript)</h1>  
  
<!-- RDS.DataControl -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDC HEIGHT=1 WIDTH=1>  
   <PARAM NAME="SQL" VALUE="Select FirstName, LastName from Employees">  
   <PARAM NAME="SERVER" VALUE="http://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider='sqloledb';Initial Catalog='Northwind';Integrated Security='SSPI';">  
</OBJECT>  
  
<!-- Data Table -->  
  
<TABLE DATASRC=#RDC BORDER=1>  
   <TR>  
      <TD> <SPAN DATAFLD="FirstName"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="LastName"></SPAN> </TD>  
   </TR>  
</TABLE>  
  
</body>  
</html>  
<!-- EndSQLDesignVBS -->  
```  
  
 Das folgende Beispiel zeigt, wie Sie die erforderlichen Parameter der **RDS. DataControl** zur Laufzeit. Zum Testen dieses Beispiels ausgeschnitten, und fügen Sie den folgenden Code in ein normales ASP-Dokument, und nennen Sie sie **SQLRuntimeVBS.asp**. ASP-Skript wird auf den Server identifiziert.  
  
```  
<!-- BeginSQLRuntimeVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>SQL Property Example (VBScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>SQL Property Example (VBScript)</h1>  
  
<H2>RDS API Code Examples </H2>  
<H3>Remote Data Service SQL Property Set at Run Time</H3>  
  
<!-- RDS.DataControl with no parameters set at design time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDC HEIGHT=1 WIDTH=1>  
</OBJECT>  
  
<TABLE DATASRC=#RDC>  
   <TR>  
      <TD> <SPAN DATAFLD="FirstName"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="LastName"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="Title"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="Type"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="Email"></SPAN> </TD>  
   </TR>  
</TABLE>  
  
<HR>  
<Input Size=70 Name="txtServer" Value= "http://<%=Request.ServerVariables("SERVER_NAME")%>">  
<BR>  
<Input Size=70 Name="txtConnect" Value="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind';">  
<BR>  
<Input Size=70 Name="txtSQL" VALUE="Select * from Employees">  
<HR>  
<INPUT TYPE=BUTTON NAME="Run" VALUE="Run"><BR>  
  
<Script Language="VBScript">  
<!--  
' Set parameters of RDS.DataControl at Run Time.  
Sub Run_OnClick  
   RDC.Server = txtServer.Value  
   RDC.SQL = txtSQL.Value  
   RDC.Connect = txtConnect.Value  
   RDC.Refresh  
End Sub  
-->  
</Script>  
  
</body>  
</html>  
<!-- EndSQLRuntimeVBS -->  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [SQL-Eigenschaft](../../../ado/reference/rds-api/sql-property.md)



