---
title: Programmieren von AMO-Sicherheitsobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- programming [AMO]
- Analysis Management Objects, security
- AMO, security
ms.assetid: 5d963721-6e6e-46eb-bc9b-18724dd0b751
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e110e71630a43d30f29be89cd56197ab8f18fd7b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197950"
---
# <a name="programming-amo-security-objects"></a>Programmieren von AMO-Sicherheitsobjekten
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], Programmieren von Sicherheitsobjekten und das Ausführen von Anwendungen, die AMO-Sicherheitsobjekte verwenden, Mitglied der Gruppe der Serveradministratoren oder Datenbankadministratoren voraus. Serveradministrator und Datenbankadministrator sind Ebenen von bereitgestellten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 In [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wird der Benutzerzugriff auf beliebige Objekte durch eine Kombination aus Rollen und Berechtigungen gewährt, die dem jeweiligen Objekt zugewiesen werden. Weitere Informationen finden Sie unter [AMO-Sicherheitsklassen](amo-security-classes.md).  
  
## <a name="role-and-permission-objects"></a>Role- und Berechtigungsobjekte  
 Serverrollen enthalten nur eine Rolle in der Auflistung: die des Administrators. Neue Rollen können der Serverrollenauflistung nicht hinzugefügt werden. Die Rolle eines Administrators ermöglicht den vollständigen Zugriff auf jedes Objekt auf dem Server.  
  
 <xref:Microsoft.AnalysisServices.Role>-Objekte werden auf Datenbankebene erstellt. Die Rollenverwaltung erfordert lediglich das Hinzufügen oder Entfernen von Mitgliedern zu oder aus einer Rolle sowie das Hinzufügen oder Löschen von Rollen zum oder aus dem <xref:Microsoft.AnalysisServices.Database>-Objekt. Eine Rolle kann nicht gelöscht werden, wird eine etwaige <xref:Microsoft.AnalysisServices.Permission> Objekt, das der Rolle zugeordnet. Um eine Rolle zu löschen alle <xref:Microsoft.AnalysisServices.Permission> Objekte in der <xref:Microsoft.AnalysisServices.Database> Objekte durchsucht werden müssen, und die <xref:Microsoft.AnalysisServices.Role> Berechtigungen, bevor daraus die <xref:Microsoft.AnalysisServices.Role> können gelöscht werden, aus der <xref:Microsoft.AnalysisServices.Database>.  
  
 Berechtigungen definieren die aktivierten Aktionen des Objekts, für das die Berechtigung erteilt wird. Berechtigungen für die folgenden Objekte angegeben werden: <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MiningStructure>, und <xref:Microsoft.AnalysisServices.MiningModel>. Die Berechtigungsverwaltung schließt das Gewähren oder Widerrufen von aktiviertem Zugriff durch die entsprechende Zugriffseigenschaft ein. Für jeden aktivierten Zugriff gibt es eine Eigenschaft, die auf die gewünschte Zugriffsstufe festgelegt werden kann. Der Zugriff kann für die folgenden Vorgänge definiert werden: Verarbeiten, ReadDefinition, Lesen, Schreiben und Verwalten. Verwalten der Zugriff wird nur definiert, auf die <xref:Microsoft.AnalysisServices.Database> Objekt. Die Datenbankadministratorsicherheitsstufe wird erteilt, wenn die Rollenmitgliedschaft gemeinsam mit der Datenbankberechtigung für die Verwaltung gewährt wird.  
  
 Im folgenden Beispiel werden vier Rollen erstellt: Database Administrators (Datenbankadministratoren), Processors (Verarbeiter), Writers (Schreiber) und Readers (Leser).  
  
 Datenbankadministratoren können die angegebene Datenbank verwalten.  
  
 Verarbeiter können alle Objekte in einer Datenbank verarbeiten und Ergebnisse überprüfen. Um Ergebnisse zu überprüfen, muss der Lesezugriff auf das Datenbankobjekt explizit für den angegebenen Cube aktiviert werden, da die Leseberechtigung nicht für alle untergeordneten Objekte gilt.  
  
 Schreiber können vom angegebenen Cube lesen und darin schreiben. Der Zellzugriff ist in der Kundendimension auf die USA begrenzt.  
  
 Leser können vom angegebenen Cube lesen. Der Zellzugriff ist in der Kundendimension auf die USA begrenzt.  
  
```  
static public void CreateRolesAndPermissions(Database db, Cube cube)  
{  
    Role role;  
    DatabasePermission dbperm;  
    CubePermission cubeperm;  
  
    #region Create the Database Administrators role  
  
    // Create the Database Administrators role.  
    role = db.Roles.Add("Database Administrators");  
    role.Members.Add(new RoleMember("")); // e.g. domain\user  
    role.Update();  
  
    // Assign administrative permissions to this role.  
    // Members of this role can perform any operation within the database.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Administer = true;  
    dbperm.Update();  
  
    #endregion  
  
    #region Create the Processors role  
  
    // Create the Processors role.  
    role = db.Roles.Add("Processors");  
    role.Members.Add(new RoleMember("")); // e.g. myDomain\johndoe  
    role.Update();  
  
    // Assign Read and Process permissions to this role.  
    // Members of this role can process objects in the database and query them to verify results.  
    // Process permission applies to all contained objects, i.e. all dimensions and cubes.  
    // Read permission does not apply to contained objects, so we must assign the permission explicitly on the cubes.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Process = true;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    cubeperm.Update();  
  
    #endregion  
  
    #region Create the Writers role  
  
    // Create the Writers role.  
    role = db.Roles.Add("Writers");  
    role.Members.Add(new RoleMember("")); // e.g. redmond\johndoe  
    role.Update();  
  
    // Assign Read and Write permissions to this role.  
    // Members of this role can discover, query and writeback to the Adventure Works cube.  
    // However cell access and writeback is restricted to the United States (in the Customer dimension).  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    cubeperm.Write = WriteAccess.Allowed;  
    cubeperm.CellPermissions.Add(new CellPermission(CellPermissionAccess.Read, "[Customer].[Country-Region].CurrentMember is [Customer].[Country-Region].[Country-Region].&[United States]"));  
    cubeperm.CellPermissions.Add(new CellPermission(CellPermissionAccess.ReadWrite, "[Customer].[Country-Region].CurrentMember is [Customer].[Country-Region].[Country-Region].&[United States]"));  
    cubeperm.Update();  
  
    #endregion  
  
    #region Create the Readers role  
  
    // Create the Readers role.  
    role = db.Roles.Add("Readers");  
    role.Members.Add(new RoleMember("")); // e.g. redmond\johndoe  
    role.Update();  
  
    // Assign Read permissions to this role.  
    // Members of this role can discover and query the Adventure Works cube.  
    // However the Customer dimension is restricted to the United States.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    Dimension dim = db.Dimensions.GetByName("Customer");  
    DimensionAttribute attr = dim.Attributes.GetByName("Country-Region");  
    CubeDimensionPermission cubedimperm = cubeperm.DimensionPermissions.Add(dim.ID);  
    cubedimperm.Read = ReadAccess.Allowed;  
    AttributePermission attrperm = cubedimperm.AttributePermissions.Add(attr.ID);  
    attrperm.AllowedSet = "{[Customer].[Country-Region].[Country-Region].&[United States]}";  
    cubeperm.Update();  
  
    #endregion  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices>   
 [Einführung in AMO-Klassen](amo-classes-introduction.md)   
 [Programmieren von AMO-Sicherheitsobjekten](programming-amo-security-objects.md)   
 [Berechtigungen und Zugriffsrechte &#40;Analysis Services – mehrdimensionale Daten&#41;](https://msdn.microsoft.com/library/ms174786(v=sql.120).aspx)   
 [Sichern von Analysis Services-Instanz](https://technet.microsoft.com/library/ms175663\(v=sql.110\).aspx)   
 [Logische Architektur &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Datenbankobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
