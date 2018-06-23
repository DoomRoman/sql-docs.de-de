---
title: Ausführen von Vorlagendateien mit der ' CommandStream '-Eigenschaft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fd2f29f14d4af758581e368986398720dd3b5a0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061567"
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a>Ausführen von Vorlagendateien mit der 'CommandStream'-Eigenschaft
  In diesem Beispiel wird veranschaulicht, wie Vorlagendateien, die aus SQL- oder XPath-Abfragen bestehende Vorlagendateien mithilfe der CommandStream-Eigenschaft des SqlXmlCommand-Objekt angegeben werden können. In dieser Anwendung eine FileStreamobject für eine Befehlsdatei geöffnet wird, und der Dateidatenstrom wird zugewiesen, als die CommandStream, die ausgeführt wird.  
  
 Im folgenden Beispiel wird die CommandType-Eigenschaft als SqlXmlCommandType.Template (nicht als TemplateFile) angegeben.  
  
 Es folgt die Beispiel-XML-Vorlage:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 Dies ist die C#-Beispielanwendung. Um die Anwendung zu testen, speichern Sie die Vorlage (TemplateFile.xml), und führen Sie dann die Anwendung aus. Die Anwendung führt die in der XML-Vorlage angegebene Abfrage aus und zeigt das daraufhin generierte XML-Dokument auf dem Bildschirm an.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         MemoryStream ms = new MemoryStream();  
         StreamWriter sw = new StreamWriter(ms);  
         ms.Position = 0;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandStream = new FileStream("TemplateFile.xml", FileMode.Open, FileAccess.Read);  
         cmd.CommandType = SqlXmlCommandType.Template;  
         using (Stream strm = cmd.ExecuteStream())  
         {  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;        
      }  
  
      public static int Main(String[] args)  
      {  
         testParams();     
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Speichern Sie die in diesem Beispiel bereitgestellte XML-Vorlage in einem Ordner.  
  
2.  Speichern Sie den C#-Code (DocSample.cs, der bereitgestellt wird), in diesem Beispiel im selben Ordner, in dem das Schema gespeichert ist. (Wenn Sie die Dateien in einem anderen Ordner speichern, müssen Sie den Code bearbeiten und den entsprechenden Verzeichnispfad für das Zuordnungsschema angeben.)  
  
3.  Kompilieren Sie den Code. Verwenden Sie zur Kompilierung des Codes an der Eingabeaufforderung die folgende Zeichenfolge:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Dadurch wird eine ausführbare Datei (DocSample.exe) erstellt.  
  
4.  Führen Sie DocSample.exe an der Eingabeaufforderung aus.  
  
  