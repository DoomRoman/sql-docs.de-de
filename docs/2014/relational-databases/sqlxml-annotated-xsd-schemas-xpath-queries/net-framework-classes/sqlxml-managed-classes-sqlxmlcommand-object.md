---
title: SqlXmlCommand-Objekt (verwaltete SQLXML Klassen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0aba35418c1a7759f5c083bd5e5f7485118cbfc3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207220"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a>SqlXmlCommand-Objekt (Verwaltete SQLXML-Klassen)
  Dies ist der Konstruktor für die SqlXmlCommand-Objekt:  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 Wobei `cnString` der ADO- oder OLEDB-Verbindungszeichenfolge entspricht, die den Server, die Datenbank und die Anmeldeinformationen identifiziert, z. B. `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.  
  
 In der Verbindungszeichenfolge muss für den `Provider` SQLOLEDB festgelegt werden, und `Data Provider` sollte nicht in der Anbieterzeichenfolge enthalten sein.  
  
 Ein Arbeitsbeispiel finden Sie unter [SQL-Abfragen ausführen &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
## <a name="methods"></a>Methoden  
 TheSqlXmlCommand Objekt unterstützt mehrere Methoden, einschließlich der folgenden Methoden zum Ausführen eines Befehls:  
  
 void ExecuteNonQuery()-Methode  
 Führt den Befehl aus, gibt aber nichts zurück. Diese Methode ist nützlich, wenn Sie einen Nichtabfragebefehl ausführen möchten (ein Befehl, der nichts zurückgibt). Ein Beispiel ist das Ausführen eines Updategrams oder DiffGrams, das Datensätze aktualisiert, aber nichts zurückgibt.  
  
 Stream-ExecuteStream()  
 Gibt ein neues Stream-Objekt zurück. Diese Methode ist nützlich, wenn Sie möchten, dass Ihnen die Abfrageergebnisse in einem neuen Datenstrom zurückgegeben werden. Ein Arbeitsbeispiel finden Sie unter [SQL-Abfragen ausführen &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 Öffentliche void ExecuteToStream (Stream OutputStream)  
 Schreibt die Abfrageergebnisse in einen vorhandenen Datenstrom. Diese Methode ist nützlich, wenn Sie einen Datenstrom haben, auf dem benötigten Ergebnisse anhängen (z. B. die Ergebnisse der Abfrage, die in der System.Web.HttpResponse.OutputStream geschrieben haben). Ein Arbeitsbeispiel finden Sie unter [SQL-Abfragen ausführen &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 "XmlReader" ExecuteXmlReader()  
 Gibt ein XmlReader-Objekt zurück. Sie können diese Methode verwenden, entweder direkt Manipulieren von Daten in das XmlReader-Objekt, oder geben Sie die kettenarchitektur von "System.xml". Weitere Informationen finden Sie in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework-Dokumentation. Ein Arbeitsbeispiel finden Sie unter [Ausführen von SQL-Abfragen mithilfe der "ExecuteXMLReader"-Methode](executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
 TheSqlXmlCommand Objekt unterstützt auch diese zusätzlichen Methoden:  
  
 SqlXmlParameter CreateParameter()  
 Erstellt ein SqlXmlParameter-Objekt. Sie können festlegen, Werte für die *Namen* und *Wert* Parameter dieses Objekts. Diese Methode ist nützlich, wenn Sie Parameter an einen Befehl übergeben möchten. Ein Arbeitsbeispiel finden Sie unter [SQL-Abfragen ausführen &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 "void" ClearParameters()  
 Löscht Parameter, die für ein angegebenes Befehlsobjekt erstellt wurden. Diese Methode ist nützlich, wenn Sie mehrere Abfragen für das gleiche Befehlsobjekt ausführen möchten.  
  
## <a name="properties"></a>Eigenschaften  
 SqlXmlCommand-Objekt unterstützt auch die folgenden Eigenschaften:  
  
 ClientSideXml  
 Legen Sie diese Eigenschaft auf True fest, wenn die Konvertierung des Rowsets in XML statt auf dem Server auf dem Client erfolgen soll. Diese Eigenschaft ist nützlich, wenn Sie die Ladeleistungslast auf die mittlere Ebene verschieben möchten. Die Eigenschaft ermöglicht außerdem das Verwenden der vorhandenen gespeicherten Prozeduren als Wrapper mit FOR XML, um eine XML-Ausgabe zu erhalten.  
  
 SchemaPath  
 Der Name des Zuordnungsschemas zusammen mit dem Verzeichnispfad (z. B. C:\x\y\MySchema.xml). Diese Eigenschaft ist nützlich, um ein Zuordnungsschema für XPath-Abfragen anzugeben. Der angegebene Pfad kann relativ oder absolut sein. Wenn der Pfad relativ ist, wird der Basispfad, der im Basispfad angegeben wird zum Auflösen des relativen Pfads. Wird kein Basispfad angegeben, ist der relative Pfad relativ zum aktuellen Verzeichnis. Ein Arbeitsbeispiel finden Sie unter [zugreifen auf SQLXML-Funktionalität in der .NET-Umgebung](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 XslPath  
 Der Name der XSL-Datei, einschließlich des Verzeichnispfads. Der angegebene Pfad kann relativ oder absolut sein. Wenn der Pfad relativ ist, wird der Basispfad, der im Basispfad angegeben wird zum Auflösen des relativen Pfads. Wird kein Basispfad angegeben, ist der relative Pfad relativ zum aktuellen Verzeichnis. Ein Arbeitsbeispiel finden Sie unter [Anwenden einer XSL-Transformation &#40;verwaltete SQLXML-Klassen&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 Basispfad  
 Der Basispfad (ein Verzeichnispfad). Diese Eigenschaft ist nützlich zum Auflösen eines relativen Pfads, der für eine XSL-Datei (mithilfe der XslPath-Eigenschaft), einer Zuordnungsschemadatei (mithilfe der SchemaPath-Eigenschaft) oder einer externen Schemareferenz in einer XML-Vorlage angegeben ist (angegeben mithilfe der `mapping-schema` -Attribut).  
  
 OutputEncoding  
 Gibt die Codierung für den Datenstrom an, der zurückgegeben wird, wenn der Befehl ausgeführt wird. Diese Eigenschaft ist nützlich, um eine bestimmte Codierung für den Datenstrom anzufordern, der zurückgegeben wird. Einige häufig verwendete Codierungen sind UTF-8, ANSI und Unicode. UTF-8 ist der Standard-Codierung.  
  
 Namespaces  
 Ermöglicht die Ausführung von XPath-Abfragen, die Namespaces verwenden. Weitere Informationen zu XPath-Abfragen mit Namespaces finden Sie unter [Ausführen von XPath-Abfragen mit Namespaces &#40;verwaltete SQLXML-Klassen&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md). Ein Arbeitsbeispiel finden Sie unter [Ausführen von XPath-Abfragen &#40;verwaltete SQLXML-Klassen&#41;](executing-xpath-queries-sqlxml-managed-classes.md).  
  
 RootTag  
 Stellt das einzelne Stammelement für von der Befehlsausführung generiertes XML bereit. Ein gültiges XML-Dokument erfordert ein einzelnes Tag auf der Stammebene. Wenn der ausgeführte Befehl ein XML-Fragment generiert (ohne einzelnes Element höchster Ebene), können Sie ein Stammelement für das zurückgebende XML angeben. Ein Arbeitsbeispiel finden Sie unter [Anwenden einer XSL-Transformation &#40;verwaltete SQLXML-Klassen&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 CommandText  
 Der Text des Befehls. Diese Eigenschaft wird zum Angeben des Texts des Befehls verwendet, den Sie ausführen möchten. Ein Arbeitsbeispiel finden Sie unter [SQL-Abfragen ausführen &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 CommandStream  
 Der Befehlsdatenstrom. Diese Eigenschaft ist nützlich, wenn Sie einen Befehl aus einer Datei ausführen möchten (z. B. aus einer XML-Vorlage). Bei Verwendung CommandStream, nur **"Template"**, **"UpdateGram"** und **"DiffGram" CommandType** Werte werden unterstützt. Ein Arbeitsbeispiel finden Sie unter [Ausführen von Vorlagendateien mit der ' CommandStream '-Eigenschaft](executing-template-files-by-using-the-commandstream-property.md).  
  
 CommandType  
 Gibt den Befehlstyp an. Diese Eigenschaft wird zum Angeben des Typs des Befehls verwendet, den Sie ausführen möchten. Die Werte in der folgenden Tabelle bestimmen den Typ des Befehls. Ein Arbeitsbeispiel finden Sie unter [zugreifen auf SQLXML-Funktionalität in der .NET-Umgebung](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
|value|Description|  
|-----------|-----------------|  
|SqlXmlCommandType.Sql|Führt einen SQL-Befehl aus (z. B. `SELECT * FROM Employees FOR XML AUTO`).|  
|SqlXmlCommandType.XPath|Führt einen XPath-Befehl aus (z. B. `Employees[@EmployeeID=1]`).|  
|SqlXmlCommandType.Template|Führt eine XML-Vorlage aus.|  
|SqlXmlCommandType.TemplateFile|Führt eine Vorlagendatei im angegebenen Pfad aus.|  
|SqlXmlCommandType.UpdateGram|Führt ein Updategram aus.|  
|SqlXmlCommandType.Diffgram|Führt ein DiffGram aus.|  
  
## <a name="see-also"></a>Siehe auch  
 [SqlXmlParameter-Objekt &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)   
 [SqlXmlAdapter-Objekt &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
