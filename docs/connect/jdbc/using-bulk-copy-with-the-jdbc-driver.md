---
title: Verwenden von Massenkopieren mit dem JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 21e19635-340d-49bb-b39d-4867102fb5df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8a936373f299530f4bd98f2873d10727c980cce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741758"
---
# <a name="using-bulk-copy-with-the-jdbc-driver"></a>Verwenden von Massenkopieren mit dem JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft SQL Server enthält ein beliebtes Befehlszeilen-Hilfsprogramm mit dem Namen **bcp** zum schnellen Massenkopieren großer Dateiumfänge in Tabellen oder Ansichten in SQL Server-Datenbanken. Die Klasse „SQLServerBulkCopy“ ermöglicht Ihnen das Schreiben von Codelösungen in Java, die eine ähnliche Funktionalität bereitstellen. Es gibt eine Reihe weiterer Verfahren, Daten in eine SQL Server-Tabelle zu laden (beispielsweise INSERT-Anweisungen), doch bietet „SQLServerBulkCopy“ ihnen gegenüber einen erheblichen Leistungsvorteil.  
  
Die Klasse „SQLServerBulkCopy“ kann nur verwendet werden, um Daten in SQL Server-Tabellen zu schreiben. Die Datenquelle ist aber nicht auf SQL Server beschränkt; jede beliebige Datenquelle kann verwendet werden, sofern die Daten mit einer Implementierung von „ResultSet“, „RowSet“ oder „ISQLServerBulkRecord“ gelesen werden können.  
  
Mithilfe der SQLServerBulkCopy-Klasse können Sie folgende Vorgänge ausführen:  
  
- Einen einzelnen Massenkopiervorgang  
  
- Mehrere Massenkopiervorgänge  
  
- Einen Massenkopiervorgang mit einer Transaktion  
  
> [!NOTE]  
> Wenn Sie den Microsoft JDBC-Treiber 4.1 für SQL Server (der die SQLServerBulkCopy-Klasse nicht unterstützt) oder eine frühere Version verwenden, können Sie stattdessen die SQL Server Transact-SQL-Anweisung „BULK INSERT“ ausführen.  
  
## <a name="bulk-copy-example-setup"></a>Einrichten des Massenkopierbeispiels  

Die Klasse „SQLServerBulkCopy“ kann nur verwendet werden, um Daten in SQL Server-Tabellen zu schreiben. Die in diesem Artikel gezeigten Codebeispiele verwenden die SQL Server-Beispieldatenbank „AdventureWorks“. Um eine Änderung der vorhandenen Codebeispiele zu vermeiden, schreiben die Codebeispiele Daten in Tabellen, die zuvor von Ihnen erstellt werden.  
  
Die Tabellen „BulkCopyDemoMatchingColumns“ und „BulkCopyDemoDifferentColumns“ basieren beide auf der Tabelle „AdventureWorks Production.Products“. In Codebeispielen, die diese Tabellen verwenden, werden Daten aus der Tabelle „Production.Products“ einer dieser Beispieltabellen hinzugefügt. Die Tabelle „BulkCopyDemoDifferentColumns“ wird verwendet, um im Beispiel zu veranschaulichen, wie Spalten aus den Quelldaten der Zieltabelle zugeordnet werden; für die meisten anderen Beispiele wird „BulkCopyDemoMatchingColumns“ verwendet.  
  
Einige der Codebeispiele zeigen, wie eine Klasse „SQLServerBulkCopy“ zum Schreiben in mehrere Tabellen verwendet werden kann. Für diese Beispiele werden die Tabellen „BulkCopyDemoOrderHeader“ und „BulkCopyDemoOrderDetail“ als Zieltabellen verwendet. Diese Tabellen basieren auf den Tabellen „Sales.SalesOrderHeader“ und „Sales.SalesOrderDetail“ in „AdventureWorks“.  
  
> [!NOTE]  
> Die Codebeispiele zu „SQLServerBulkCopy“ werden nur zur Verfügung gestellt, um die Syntax für die Verwendung von „SQLServerBulkCopy“ zu veranschaulichen. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT … SELECT“ zum Kopieren der Daten einfacher und schneller.  

### <a name="table-setup"></a>Tabelleneinrichtung  

Zum Erstellen der Tabellen, die für die ordnungsgemäße Ausführung der Codebeispiele erforderlich sind, müssen Sie die folgenden Transact-SQL-Anweisungen in einer SQL Server-Datenbank ausführen.  

```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobject
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
```

## <a name="single-bulk-copy-operations"></a>Einzelne Massenkopiervorgänge

Die einfachste Herangehensweise an einen SQL Server-Massenkopiervorgang ist das Durchführen eines einzelnen Vorgangs für eine Datenbank. Standardmäßig wird ein Massenkopiervorgang als isolierter Vorgang ausgeführt: Der Kopiervorgang erfolgt in nicht transaktionaler Weise, ohne Möglichkeit zum Rollback.  
  
> [!NOTE]  
> Wenn Sie für den Massenkopiervorgang beim Auftreten eines Fehlers einen teilweisen oder vollständigen Rollback ausführen müssen, können Sie entweder eine verwaltete SQLServerBulkCopy-Transaktion verwenden oder den Massenkopiervorgang innerhalb einer vorhandenen Transaktion ausführen.  
> Weitere Informationen finden Sie unter [Transaktion und Bulk-Kopiervorgänge](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TransactionBulk)  
  
 Dies sind die allgemeinen Schritte zum Durchführen eines Massenkopiervorgangs:  
  
1. Herstellen einer Verbindung mit dem Quellserver und Abrufen der zu kopierenden Daten. Daten können auch aus anderen Quellen stammen, sofern sie von einem ResultSet-Objekt oder einer ISQLServerBulkRecord-Implementierung abgerufen werden können.  
  
2. Herstellen einer Verbindung mit dem Zielserver (sofern **SQLServerBulkCopy** nicht die Verbindung für Sie herstellen soll).  
  
3. Erstellen eines SQLServerBulkCopy-Objekts und Festlegen aller erforderlichen Eigenschaften mithilfe von **setBulkCopyOptions**.  
  
4. Aufrufen der Methode **setDestinationTableName**, um die Zieltabelle für den Masseneinfügungsvorgang anzugeben.  
  
5. Aufruf einer der **writeToServer**-Methoden.  
  
6. Optional Aktualisieren der Eigenschaften mithilfe von **setBulkCopyOptions** und bei Bedarf erneuter Aufruf von **writeToServer**.  
  
7. Aufruf von **close** oder Umschließen der Massenkopiervorgänge durch eine try-with-resources-Anweisung.  
  
> [!CAUTION]  
> Wir empfehlen die Verwendung gleicher Datentypen für Quell- und Zielspalten. Wenn die Datentypen nicht übereinstimmen, versucht „SQLServerBulkCopy“, jeden Quellwert in den Zieldatentyp zu konvertieren. Konvertierungen wirken sich negativ auf die Leistung aus und können außerdem zu unerwarteten Fehlern führen. Beispielsweise kann ein Datentyp „double“ in den meisten Fällen in den Datentyp „decimal“ konvertiert werden, aber nicht immer.  
  
### <a name="example"></a>Beispiel

Die folgende Anwendung zeigt das Laden von Daten mithilfe der Klasse „SQLServerBulkCopy“. In diesem Beispiel wird ein „ResultSet“ verwendet, um Daten aus der Tabelle „Production.Product“ in der SQL Server AdventureWorks-Datenbank in eine ähnliche Tabelle in der gleichen Datenbank zu kopieren.  
  
> [!IMPORTANT]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup) beschrieben erstellt haben. Dieser Code wird nur bereitgestellt, um die Syntax für die Verwendung von „SQLServerBulkCopy“ zu demonstrieren. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT … SELECT“ zum Kopieren der Daten einfacher und schneller.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;

public class BulkCopySingle {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection)) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // In real world applications you would
            // not use SQLServerBulkCopy to move data from one table to the other
            // in the same database. This is for demonstration purposes only.

            // Set up the bulk copy object.
            // Note that the column positions in the source
            // table match the column positions in
            // the destination table so there is no need to
            // map columns.
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            bulkCopy.writeToServer(rsSourceData);

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="performing-a-bulk-copy-operation-using-transact-sql"></a>Ausführen eines Massenkopiervorgangs mithilfe von Transact-SQL

Das folgende Beispiel zeigt die Verwendung der Methode „executeUpdate“ zum Ausführen der Anweisung „BULK INSERT“.  
  
> [!NOTE]  
> Der Dateipfad für die Datenquelle ist relativ zum Server. Der Serverprozess muss Zugriff auf diesen Pfad besitzen, damit der Massenkopiervorgang erfolgreich ausgeführt werden kann.  

```java
try (Connection con = DriverManager.getConnection(connectionUrl);
        Statement stmt = con.createStatement()) {
    // Perform the BULK INSERT
    stmt.executeUpdate(
            "BULK INSERT Northwind.dbo.[Order Details] " + "FROM 'f:\\mydata\\data.tbl' " + "WITH ( FORMATFILE='f:\\mydata\\data.fmt' )");
}
```  

## <a name="multiple-bulk-copy-operations"></a>Mehrere Massenkopiervorgänge  

Mithilfe einer einzelnen Instanz einer SQLServerBulkCopy-Klasse können Sie mehrere Massenkopiervorgänge ausführen. Wenn sich die Parameter für den Vorgang zwischen den Ausführungen ändern (z. B. der Name der Zieltabelle), müssen Sie sie vor allen nachfolgenden Aufrufen einer der writeToServer-Methoden ändern, wie im folgenden Beispiel gezeigt. Sofern sie nicht explizit geändert werden, bleiben alle Eigenschaftswerte die gleichen wie beim letzten Massenkopiervorgang für eine bestimmte Instanz.  

> [!NOTE]  
> Das Ausführen mehrerer Massenkopiervorgänge mithilfe der gleichen Instanz von SQLServerBulkCopy ist normalerweise effizienter als die Verwendung einer separaten Instanz für jeden Vorgang.  
  
Wenn Sie mehrere Massenkopiervorgänge mithilfe des gleichen SQLServerBulkCopy-Objekts ausführen, bestehen normalerweise keine Einschränkungen hinsichtlich der Gleichheit oder Verschiedenheit der Quell- und Zielinformationen für die einzelnen Vorgänge. Sie müssen jedoch sicherstellen, dass die Informationen zur Spaltenzuordnung bei jedem Schreibvorgang auf dem Server ordnungsgemäß festgelegt sind.  
  
> [!IMPORTANT]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup) beschrieben erstellt haben. Dieser Code wird nur bereitgestellt, um die Syntax für die Verwendung von „SQLServerBulkCopy“ zu demonstrieren. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT … SELECT“ zum Kopieren der Daten einfacher und schneller.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyMultiple {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationHeaderTable = "dbo.BulkCopyDemoOrderHeader";
        String destinationDetailTable = "dbo.BulkCopyDemoOrderDetail";
        int countHeaderBefore, countDetailBefore, countHeaderAfter, countDetailAfter;
        ResultSet rsHeader, rsDetail;

        try (Connection sourceConnection1 = DriverManager.getConnection(connectionUrl);
                Connection sourceConnection2 = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection1.createStatement();
                PreparedStatement preparedStmt1 = sourceConnection1.prepareStatement(
                        "SELECT [SalesOrderID], [OrderDate], [AccountNumber] FROM [Sales].[SalesOrderHeader] WHERE [AccountNumber] = ?;");
                PreparedStatement preparedStmt2 = sourceConnection2.prepareStatement(
                        "SELECT [Sales].[SalesOrderDetail].[SalesOrderID], [SalesOrderDetailID], [OrderQty], [ProductID], [UnitPrice] FROM "
                                + "[Sales].[SalesOrderDetail] INNER JOIN [Sales].[SalesOrderHeader] ON "
                                + "[Sales].[SalesOrderDetail].[SalesOrderID] = [Sales].[SalesOrderHeader].[SalesOrderID] WHERE [AccountNumber] = ?;");
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(connectionUrl);) {

            // Empty the destination tables.
            stmt.executeUpdate("DELETE FROM " + destinationHeaderTable);
            stmt.executeUpdate("DELETE FROM " + destinationDetailTable);

            // Perform an initial count on the destination
            // table with matching columns.
            countHeaderBefore = getRowCount(stmt, destinationHeaderTable);

            // Perform an initial count on the destination
            // table with different column positions.
            countDetailBefore = getRowCount(stmt, destinationDetailTable);

            // Get data from the source table as a ResultSet.
            // The Sales.SalesOrderHeader and Sales.SalesOrderDetail
            // tables are quite large and could easily cause a timeout
            // if all data from the tables is added to the destination.
            // To keep the example simple and quick, a parameter is
            // used to select only orders for a particular account
            // as the source for the bulk insert.
            preparedStmt1.setString(1, "10-4020-000034");
            rsHeader = preparedStmt1.executeQuery();

            // Get the Detail data in a separate connection.
            preparedStmt2.setString(1, "10-4020-000034");
            rsDetail = preparedStmt2.executeQuery();

            // Create the SQLServerBulkCopySQLServerBulkCopy object.
            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setBulkCopyTimeout(100);
            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationHeaderTable);

            // Guarantee that columns are mapped correctly by
            // defining the column mappings for the order.
            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");
            bulkCopy.addColumnMapping("OrderDate", "OrderDate");
            bulkCopy.addColumnMapping("AccountNumber", "AccountNumber");

            // Write rsHeader to the destination.
            bulkCopy.writeToServer(rsHeader);

            // Set up the order details destination.
            bulkCopy.setDestinationTableName(destinationDetailTable);

            // Clear the existing column mappings
            bulkCopy.clearColumnMappings();

            // Add order detail column mappings.
            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");
            bulkCopy.addColumnMapping("SalesOrderDetailID", "SalesOrderDetailID");
            bulkCopy.addColumnMapping("OrderQty", "OrderQty");
            bulkCopy.addColumnMapping("ProductID", "ProductID");
            bulkCopy.addColumnMapping("UnitPrice", "UnitPrice");

            // Write rsDetail to the destination.
            bulkCopy.writeToServer(rsDetail);

            // Perform a final count on the destination
            // tables to see how many rows were added.
            countHeaderAfter = getRowCount(stmt, destinationHeaderTable);
            countDetailAfter = getRowCount(stmt, destinationDetailTable);

            System.out.println((countHeaderAfter - countHeaderBefore) + " rows were added to the Header table.");
            System.out.println((countDetailAfter - countDetailBefore) + " rows were added to the Detail table.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

## <a name="transaction-and-bulk-copy-operations"></a>Transaktionen und Massenkopiervorgänge

 Massenkopiervorgänge können als isolierte Vorgänge oder im Rahmen einer aus mehreren Schritten bestehenden Transaktion ausgeführt werden. Diese zweite Option ermöglicht Ihnen das Ausführen mehrerer Massenkopiervorgänge innerhalb der gleichen Transaktion sowie die Durchführung weiterer Datenbankvorgänge (wie etwa Einfüge-, Aktualisierungs- und Löschvorgänge), während die Möglichkeit zum Commit oder Rollback der gesamten Transaktion erhalten bleibt.  
  
 Standardmäßig wird ein Massenkopiervorgang als isolierter Vorgang ausgeführt. Der Massenkopiervorgang erfolgt nicht transaktional, ohne Möglichkeit zum Rollback. Wenn Sie für den Massenkopiervorgang beim Auftreten eines Fehlers einen teilweisen oder vollständigen Rollback ausführen müssen, können Sie eine verwaltete SQLServerBulkCopy-Transaktion verwenden oder den Massenkopiervorgang innerhalb einer vorhandenen Transaktion ausführen.  
  
### <a name="performing-a-non-transacted-bulk-copy-operation"></a>Ausführen eines nicht transaktionalen Massenkopiervorgangs

Die folgende Anwendung zeigt, was geschieht, wenn bei einem nicht transaktionalen Massenkopiervorgang nach teilweiser Ausführung ein Fehler auftritt.  
  
In dem Beispiel enthalten Quell- und Zieltabelle jeweils eine Identitätsspalte mit Namen **ProductID**. Der Code bereitet zunächst die Zieltabelle vor, indem er alle Zeilen löscht und dann eine einzelne Zeile einfügt, deren **ProductID** bekanntermaßen in der Quelltabelle vorhanden ist. Standardmäßig wird für die Spalte „Identity“ in der Zieltabelle für jede hinzugefügte Zeile ein neuer Wert generiert. In diesem Beispiel wird beim Öffnen der Verbindung eine Option festgelegt, die den Massenladevorgang zwingt, stattdessen die Identity-Werte aus der Quelltabelle zu verwenden.  
  
Der Massenkopiervorgang wird mit dem Wert „10“ für die Eigenschaft **BatchSize** ausgeführt. Wenn der Vorgang auf die ungültige Zeile trifft, wird eine Ausnahme ausgelöst. In diesem ersten Beispiel ist der Massenkopiervorgang nicht transaktional. Für alle bis zum Auftreten des Fehlers kopierten Batches wird ein Commit ausgeführt; für den Batch, der den doppelten Schlüssel enthält, wird ein Rollback ausgeführt, und der Massenkopiervorgang wird vor dem Verarbeiten weiterer Batches angehalten.  
  
> [!NOTE]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup) beschrieben erstellt haben. Dieser Code wird nur bereitgestellt, um die Syntax für die Verwendung von „SQLServerBulkCopy“ zu demonstrieren. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT … SELECT“ zum Kopieren der Daten einfacher und schneller.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyNonTransacted {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(connectionUrl)) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Add a single row that will result in duplicate key
            // when all rows from source are bulk copied.
            // Note that this technique will only be successful in
            // illustrating the point if a row with ProductID = 446
            // exists in the AdventureWorks Production.Products table.
            // If you have made changes to the data in this table, change
            // the SQL statement in the code to add a ProductID that
            // does exist in your version of the Production.Products
            // table. Choose any ProductID in the middle of the table
            // (not first or last row) to best illustrate the result.
            stmt.executeUpdate("SET IDENTITY_INSERT " + destinationTable + " ON;" + "INSERT INTO " + destinationTable
                    + "([ProductID], [Name] ,[ProductNumber]) VALUES(446, 'Lock Nut 23','LN-3416'); SET IDENTITY_INSERT " + destinationTable
                    + " OFF");

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // Set up the bulk copy object using the KeepIdentity option and BatchSize = 10.
            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setKeepIdentity(true);
            copyOptions.setBatchSize(10);

            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            // This should fail with a duplicate key error
            // after some of the batches have been copied.
            try {
                bulkCopy.writeToServer(rsSourceData);
            }
            catch (SQLException e) {
                e.printStackTrace();
            }

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="performing-a-dedicated-build-copy-operation-in-a-transaction"></a>Ausführen eines dedizierten Massenkopiervorgangs in einer Transaktion 

Standardmäßig stellt ein Massenkopiervorgang seine eigene Transaktion dar. Wenn Sie einen dedizierten Massenkopiervorgang ausführen möchten, erstellen Sie eine neue Instanz von „SQLServerBulkCopy“ mit einer Verbindungszeichenfolge. In diesem Szenario erstellt der Massenkopiervorgang die Transaktion, für die er dann einen Commit oder einen Rollback ausführt. Sie können explizit die Option **UseInternalTransaction** in **SQLServerBulkCopyOptions** angeben, um explizit die Ausführung eines Massenkopiervorgangs innerhalb einer eigenen Transaktion zu veranlassen, was dazu führt, dass jeder Batch des Massenkopiervorgangs in einer eigenen Transaktion ausgeführt wird.  
  
> [!NOTE]  
> Da verschiedene Batches in verschiedenen Transaktionen ausgeführt werden, wird für alle Zeilen im aktuellen Batch beim Auftreten eines Fehlers ein Rollback ausgeführt, die Zeilen aus vorhergehenden Batches verbleiben jedoch in der Datenbank.  
  
Bei Angabe der **UseInternalTransaction** option **BulkCopyNonTransacted**, ist der Massenkopiervorgang in einer größeren, externen Transaktion enthalten. Wenn der Fehler aufgrund des Primärschlüsselverstoßes auftritt, wird ein Rollback der gesamten Transaktion ausgeführt, und der Zieltabelle werden keine Zeilen hinzugefügt.

```java
SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
copyOptions.setKeepIdentity(true);
copyOptions.setBatchSize(10);
copyOptions.setUseInternalTransaction(true);
```

### <a name="using-existing-transactions"></a>Verwenden vorhandener Transaktionen

Sie können ein Verbindungsobjekt, für das Transaktionen aktiviert sind, als Parameter in einem SQLServerBulkCopy-Konstruktor übergeben. In dieser Situation wird der Massenkopiervorgang in einer vorhandenen Transaktion ausgeführt, und es tritt keine Änderung am Transaktionsstatus ein (d.h. für sie wird weder ein Commit noch ein Abbruch ausgeführt). Dies macht es möglich, dass Anwendungen den Massenkopiervorgang zusammen mit anderen Datenbankvorgängen in einer Transaktion einschließen. Ob Sie einen Rollback des gesamten Massenkopiervorgangs durchführen müssen, weil ein Fehler auftritt, oder ob die Massenkopie im Rahmen eines größeren Prozesses ausgeführt werden soll, für den ein Rollback durchgeführt werden kann, Sie können den Rollback für das Verbindungsobjekt zu jedem beliebigen Zeitpunkt nach dem Massenkopiervorgang ausführen.  
  
Die folgende Anwendung ähnelt **BulkCopyNonTransacted**, mit einer Ausnahme: in diesem Beispiel ist der Massenkopiervorgang in einer größeren, externen Transaktion enthalten. Wenn der Fehler aufgrund des Primärschlüsselverstoßes auftritt, wird ein Rollback der gesamten Transaktion ausgeführt, und der Zieltabelle werden keine Zeilen hinzugefügt.

> [!NOTE]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup) beschrieben erstellt haben. Dieser Code wird nur bereitgestellt, um die Syntax für die Verwendung von „SQLServerBulkCopy“ zu demonstrieren. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung „INSERT … SELECT“ zum Kopieren der Daten einfacher und schneller.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyExistingTransactions {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;
        SQLServerBulkCopyOptions copyOptions;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection);) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Add a single row that will result in duplicate key
            // when all rows from source are bulk copied.
            // Note that this technique will only be successful in
            // illustrating the point if a row with ProductID = 446
            // exists in the AdventureWorks Production.Products table.
            // If you have made changes to the data in this table, change
            // the SQL statement in the code to add a ProductID that
            // does exist in your version of the Production.Products
            // table. Choose any ProductID in the middle of the table
            // (not first or last row) to best illustrate the result.
            stmt.executeUpdate("SET IDENTITY_INSERT " + destinationTable + " ON;" + "INSERT INTO " + destinationTable
                    + "([ProductID], [Name] ,[ProductNumber]) VALUES(446, 'Lock Nut 23','LN-3416'); SET IDENTITY_INSERT " + destinationTable
                    + " OFF");

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // Set up the bulk copy object inside the transaction.
            destinationConnection.setAutoCommit(false);

            copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setKeepIdentity(true);
            copyOptions.setBatchSize(10);

            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            // This should fail with a duplicate key error.
            try {
                bulkCopy.writeToServer(rsSourceData);
                destinationConnection.commit();
            }
            catch (SQLException e) {
                e.printStackTrace();
            }

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        catch (Exception e) {
            // Handle any errors that may have occurred.
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="bulk-copy-from-a-csv-file"></a>Massenkopieren aus einer CSV-Datei  

 Die folgende Anwendung zeigt das Laden von Daten mithilfe der Klasse „SQLServerBulkCopy“. In diesem Beispiel wird eine CSV-Datei verwendet, um aus der Tabelle „Production.Product“ in der SQL Server AdventureWorks-Datenbank exportierte Daten in eine ähnliche Tabelle in der gleichen Datenbank zu kopieren.  
  
> [!IMPORTANT]  
> Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Tabelleneinrichtung](../../ssms/download-sql-server-management-studio-ssms.md) beschrieben erstellt haben, um es abzurufen.  
  
1. Öffnen Sie **SQL Server Management Studio**, und stellen Sie eine Verbindung mit dem SQL Server-Computer mit der AdventureWorks-Datenbank her.  
  
2. Erweitern Sie die Datenbanken, klicken Sie mit der rechten Maustaste auf die AdventureWorks-Datenbank, und wählen Sie **Aufgaben** und **Daten exportieren** aus.  
  
3. Wählen Sie als Datenquelle die **Datenquelle** aus, die Ihnen die Verbindung mit Ihrem SQL Server ermöglicht (z.B. SQL Server Native Client 11.0), überprüfen Sie die Konfiguration, und wählen Sie anschließend **Weiter** aus.  
  
4. Wählen Sie als Ziel das **Flatfileziel** aus, und geben Sie einen **Dateinamen** mit einem Zielspeicherort wie etwa „C:\Test\TestBulkCSVExample.csv“ ein. Überprüfen Sie, ob das **Format** „Mit Trennzeichen“, der **Textqualifizierer** „Ohne“ ist, und aktivieren Sie **Spaltennamen in der ersten Datenzeile**. Wählen Sie anschließend **Weiter** aus.  
  
5. Wählen Sie **Abfrage zum Abgeben der zu übertragenden Daten schreiben** und anschließend **Weiter** aus.  Geben Sie für die **SQL-Anweisung** SELECT ProductID, Name, ProductNumber FROM Production.Product und **Weiter** ein.  
  
6. Überprüfen Sie die Konfiguration: Sie können das Zeilentrennzeichen als {CR}{LF} und das Spaltentrennzeichen als Komma {,} belassen.  Wählen Sie **Zuordnungen bearbeiten** aus. und überprüfen Sie, ob der **Datentyp** für die einzelnen Spalten richtig ist (z.B. Integer für ProductID und Unicode-Zeichenfolge für die anderen).  
  
7. Überspringen Sie die weiteren Optionen bis zu **Fertig stellen**, und führen Sie den Exportvorgang aus.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCSVFileRecord;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;

public class BulkCopyCSV {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;

        // Get data from the source file by loading it into a class that implements ISQLServerBulkRecord.
        // Here we are using the SQLServerBulkCSVFileRecord implementation to import the example CSV file.
        try (Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = destinationConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection);
                SQLServerBulkCSVFileRecord fileRecord = new SQLServerBulkCSVFileRecord("C:\\Test\\TestBulkCSVExample.csv", true);) {

            // Set the metadata for each column to be copied.
            fileRecord.addColumnMetadata(1, null, java.sql.Types.INTEGER, 0, 0);
            fileRecord.addColumnMetadata(2, null, java.sql.Types.NVARCHAR, 50, 0);
            fileRecord.addColumnMetadata(3, null, java.sql.Types.NVARCHAR, 25, 0);

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Set up the bulk copy object.
            // Note that the column positions in the source
            // data reader match the column positions in
            // the destination table so there is no need to
            // map columns.
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            bulkCopy.writeToServer(fileRecord);

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```  

### <a name="bulk-copy-with-always-encrypted-columns"></a>Massenkopieren Sie mit Always Encrypted-Spalten  

Microsoft JDBC-Treiber 6.0 für SQL Server ab, wird das Massenkopieren mit Always Encrypted-Spalten unterstützt.  
  
Abhängig von der Bulk Kopieroptionen zu erhalten und die Verschlüsselung kann Typ der Quelle und Ziel Tabellen, die der JDBC-Treiber transparent entschlüsselt und Verschlüsseln der Daten, oder es kann, die verschlüsselten Daten gesendet werden. Z. B. entschlüsselt beim Massenkopieren von Daten aus einer verschlüsselten Spalte zu einer nicht verschlüsselten Spalte, der Treiber transparent Daten vor dem Senden an SQL Server. Auf ähnliche Weise verschlüsselt beim Massenkopieren von Daten aus einer nicht verschlüsselten Spalte (oder aus einer CSV-Datei), um eine verschlüsselte Spalte, der Treiber transparent Daten vor dem Senden an SQL Server. Wenn sowohl Quell- und Ziel verschlüsselt ist, klicken Sie dann je nach der **AllowEncryptedValueModifications** Massenimport Option zum Kopieren, der Treiber würden Daten senden, wie ist oder würden die Daten entschlüsseln und Verschlüsseln Sie ihn erneut, bevor Sie an SQL Server gesendet wird.  
  
Weitere Informationen finden Sie unter den **AllowEncryptedValueModifications** Massenimport der folgenden Option zum Kopieren und [Using Always Encrypted, mit dem JDBC-Treiber](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
> Die Einschränkung des Microsoft JDBC-Treiber 6.0 für SQL Server beim Massenkopieren von Daten aus einer CSV-Datei, die verschlüsselten Spalten:  
>
> Nur die Transact-SQL standardmäßige Format der Zeichenfolgenliterale ist für die Datums- und Uhrzeittypen unterstützt.  
>
> DateTime- und SMALLDATETIME-Datentypen werden nicht unterstützt.  
  
## <a name="bulk-copy-api-for-jdbc-driver"></a>Massenkopieren-API für JDBC Driver  
  
### <a name="sqlserverbulkcopy"></a>SQLServerBulkCopy 

Damit können Sie effizient eine SQL Server-Tabelle mit Massendaten aus einer anderen Quelle laden.  
  
Microsoft SQL Server enthält ein beliebtes Befehlszeilen-Hilfsprogramm namens bcp zum Verschieben von Daten aus einer Tabelle in eine andere, das auf einem einzelnen Server oder serverübergreifend ausgeführt werden kann. Die Klasse „SQLServerBulkCopy“ ermöglicht Ihnen das Erstellen von Codelösungen in Java, die eine ähnliche Funktionalität bereitstellen. Es gibt eine Reihe weiterer Verfahren, Daten in eine SQL-Server-Tabelle zu laden (beispielsweise INSERT-Anweisungen), doch bietet „SQLServerBulkCopy“ ihnen gegenüber einen erheblichen Leistungsvorteil.  
  
Die Klasse „SQLServerBulkCopy“ kann nur verwendet werden, um Daten in SQL Server-Tabellen zu schreiben. Die Datenquelle ist aber nicht auf SQL Server beschränkt; jede beliebige Datenquelle kann verwendet werden, sofern die Daten mit einer Instanz von „ResultSet“ oder einer Implementierung von „ISQLServerBulkRecord“ gelesen werden können.  
  
| Konstruktor                             | und Beschreibung                                                                                                                                                                                                                    |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| SQLServerBulkCopy(Connection)           | Initialisiert eine neue Instanz der Klasse „SQLServerBulkCopy“ mithilfe der angegebenen offenen Instanz von „SQLServerConnection“. Wenn für die Verbindung Transaktionen aktiviert sind, werden die Kopiervorgänge innerhalb der betreffenden Transaktion ausgeführt. |
| "Sqlserverbulkcopy" (Zeichenfolge ConnectionURL) | Initialisiert und öffnet basierend auf der übergebenen „connectionURL“ eine neue Instanz von „SQLServerConnection“. Der Konstruktor verwendet „SQLServerConnection“, um eine neue Instanz der Klasse „SQLServerBulkCopy“ zu initialisieren.                     |
  
| Eigenschaft                    | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Zeichenfolge DestinationTableName | Name der Zieltabelle auf dem Server.<br /><br /> Wenn „DestinationTableName“ beim Aufruf von „writeToServer“ nicht festgelegt ist, wird eine SQLServerException ausgelöst.<br /><br /> „DestinationTableName“ ist ein dreiteiliger Name (\<database>.\<owningschema>.\<name>). Sie können den Tabellennamen mit seiner Datenbank und dem besitzenden Schema qualifizieren, wenn Sie das wünschen. Wenn im Tabellennamen jedoch ein Unterstrich ("_") oder ein anderes Sonderzeichen vorkommt, müssen Sie den Namen in eckige Klammern einschließen. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation unter "Bezeichner". |
| ColumnMappings              | Spaltenzuordnungen definieren die Beziehungen zwischen Spalten in der Datenquelle und Spalten im Ziel.<br /><br /> Wenn keine Zuordnungen definiert sind, werden die Spalten implizit auf der Grundlage ihrer Ordinalposition zugeordnet. Damit dies funktioniert, müssen Quell- und Zielschema übereinstimmen. Ist dies nicht der Fall, wird eine Ausnahme ausgelöst.<br /><br /> Wenn die Zuordnung nicht leer ist, muss nicht jede in der Datenquelle vorhandene Spalte angegeben werden. Nicht zugeordnete Spalten werden ignoriert.<br /><br /> Sie können auf Quell- und Zielspalten über den Namen oder die Ordnungszahl verweisen.               |
  
| Methode                                                                | und Beschreibung                                                                                                                                                                |
| --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| "Void" AddColumnMapping ((SourceColumn von Int, Int DestinationColumn-Objekt)       | Fügt eine neue Spaltenzuordnung hinzu, und verwendet für die Angabe von Quell- und Zielspalten Ordnungszahlen.                                                                                  |
| "Void" AddColumnMapping ((Int SourceColumn-Wert, Zeichenfolge DestinationColumn-Objekt)   | Fügt eine neue Spaltenzuordnung hinzu und verwendet für die Quellspalte eine Ordnungszahl und für die Zielspalte den Spaltennamen.                                                            |
| "Void" AddColumnMapping ((Zeichenfolge SourceColumn-Wert, Int DestinationColumn-Objekt)   | Fügt eine neue Spaltenzuordnung hinzu und verwendet einen Spaltennamen zum Beschreiben der Quellspalte und eine Ordnungszahl zum Angeben der Zielspalte.                                             |
| "Void" AddColumnMapping (SourceColumn der Zeichenfolge, Zeichenfolge DestinationColumn-Objekt) | Fügt eine neue Spaltenzuordnung hinzu, und verwendet für die Angabe von Quell- und Zielspalten Spaltennamen.                                                                              |
| Void clearColumnMappings()                                            | Löscht den Inhalt der Spaltenzuordnungen.                                                                                                                                |
| "Void" close()                                                          | Schließt die SQLServerBulkCopy-Instanz.                                                                                                                                     |
| SQLServerBulkCopyOptions getBulkCopyOptions()                         | Ruft den aktuellen Satz von „SQLServerBulkCopyOptions“ ab.                                                                                                                     |
| String getDestinationTableName()                                      | Ruft den Namen der aktuellen Zieltabelle ab.                                                                                                                               |
| "Void" setBulkCopyOptions(SQLServerBulkCopyOptions copyOptions)         | Aktualisiert das Verhalten der SQLServerBulkCopy-Instanz gemäß den angegebenen Optionen.                                                                                  |
| "Void" setDestinationTableName(String tableName)                        | Legt den Namen der Zieltabelle fest.                                                                                                                                    |
| "Void" writeToServer(ResultSet sourceData)                              | Kopiert alle Zeilen im angegebenen ResultSet in eine durch die Eigenschaft „DestinationTableName“ des SQLServerBulkCopy-Objekts angegebene Zieltabelle.                           |
| "Void" writeToServer(RowSet sourceData)                                 | Kopiert alle Zeilen im angegebenen RowSet in eine durch die Eigenschaft „DestinationTableName“ des SQLServerBulkCopy-Objekts angegebene Zieltabelle.                              |
| "Void" writeToServer(ISQLServerBulkRecord sourceData)                   | Kopiert alle Zeilen in der angegebenen ISQLServerBulkRecord-Implementierung in eine durch die Eigenschaft „DestinationTableName“ des SQLServerBulkCopy-Objekts angegebene Zieltabelle. |
  
### <a name="sqlserverbulkcopyoptions"></a>SQLServerBulkCopyOptions  

 Eine Auflistung von Einstellungen, die steuern, wie sich die writeToServer-Methoden in einer Instanz von „SQLServerBulkCopy“ verhalten.  
  
| Konstruktor                | und Beschreibung                                                                                              |
| -------------------------- | -------------------------------------------------------------------------------------------------------- |
| SQLServerBulkCopyOptions() | Initialisiert eine neue Instanz der Klasse SQLServerBulkCopyOptions mit Standardwerten für alle Einstellungen. |
  
 Für die folgenden Optionen sind Getter und Setter vorhanden:  
  
| Option                                   | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Default                                                              |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Boolesche CheckConstraints                 | Überprüft Bedingungen während der Einfügung von Daten.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | False – keine Einschränkungen Überprüfung.                                   |
| Boolesche FireTriggers                     | Wenn der Wert angegeben wird, wird der Server veranlasst, die Einfügetrigger für die in die Datenbank eingefügten Zeilen auszulösen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | False – es werden keine Trigger ausgelöst                                        |
| Boolesche KeepIdentity                     | Die Identitätswerte der Quelltabelle werden beibehalten.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | False – die Identitätswerte werden vom Ziel zugewiesen              |
| Boolesche KeepNulls                        | NULL-Werte in der Zieltabelle werden beibehalten, unabhängig von der Einstellung für Standardwerte.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | False – NULL-Werte werden, falls anwendbar, durch Standardwerte ersetzt. |
| Boolesche TableLock                        | Für die Dauer des Massenimportvorgangs wird eine Sperre für Massenaktualisierung aktiviert.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | False – es werden Sperren auf Zeilenebene verwendet.                                          |
| Boolesche UseInternalTransaction           | Wenn angegeben, wird jeder Batch des Massenkopiervorgangs innerhalb einer Transaktion verarbeitet. Wenn „SQLServerBulkCopy“ eine vorhandene Verbindung verwendet, (wie im Konstruktor angegeben), tritt eine SQLServerException auf.  Wenn „SQLServerBulkCopy“ eine dedizierte Verbindung erstellt hat, wird eine Transaktion aktiviert.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | False – keine Transaktion                                               |
| Int BatchSize                            | Anzahl der Zeilen in jedem Batch. Am Ende jedes Batches werden die im Batch enthaltenen Zeilen an den Server gesendet.<br /><br /> Ein Batch ist abgeschlossen, wenn die Anzahl „BatchSize“ Zeilen verarbeitet wurde oder keine weiteren Zeilen zum Senden an die Zieldatenquelle mehr vorhanden sind.  Wenn die SQLServerBulkCopy-Instanz ohne aktive Option „UseInternalTransaction“ deklariert wurde, werden Zeilen zu jeweils „BatchSize“ zugleich an den Server gesendet, es wird jedoch keine transaktionsbezogene Aktion eingeleitet. Wenn „UseInternalTransaction“ aktiviert ist, wird jeder Batch Zeilen als separate Transaktion eingefügt.                                                                                                                                                                                                                                                                                                                                                                                                                                           | 0 – gibt an, dass jeder writeToServer-Vorgang ein einzelner Batch ist.    |
| Int BulkCopyTimeout                      | Anzahl der Sekunden für den Abschluss des Vorgangs, bevor ein Timeout eintritt. Der Wert „0“ bedeutet keine Einschränkung; der Massenkopiervorgang wartet unbegrenzt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 60 Sekunden.                                                          |
| Boolesche allowEncryptedValueModifications | Diese Option steht mit dem Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server.<br /><br /> Wenn angegeben, **AllowEncryptedValueModifications** ermöglicht Massenkopiervorgang von verschlüsselten Daten zwischen Tabellen oder Datenbanken ohne Entschlüsselung der Daten. In der Regel wird eine Anwendung Daten aus verschlüsselten Spalten aus einer Tabelle ohne Entschlüsselung der Daten (die app wird mit dem Schlüsselwort Spalte Encryption-Einstellung auf deaktiviert festgelegt, mit der Datenbank herstellen) wählen, und klicken Sie dann diese Option, um der masseneinfügung die Daten verwenden, Das ist noch immer verschlüsselt. Weitere Informationen finden Sie unter [Verwenden von Always Encrypted mit dem ODBC-Treiber](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).<br /><br /> Gehen Sie bei der Angabe von **AllowEncryptedValueModifications** mit Bedacht vor, da dies möglicherweise zu einer Beschädigung der Datenbank führen kann, da der Treiber nicht überprüft, ob die Daten tatsächlich verschlüsselt oder mit demselben Verschlüsselungstyp, Algorithmus und Schlüssel wie die Zielspalte ordnungsgemäß verschlüsselt wurden. |
  
 Getter und Setter:  
  
| Methoden                                                                            | und Beschreibung                                                                                                                                                                               |
| ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Boolesche isCheckConstraints()                                                       | Gibt an, ob Einschränkungen überprüft werden, während Daten oder nicht eingefügt werden.                                                                                                      |
| "Void" setCheckConstraints(Boolean checkConstraints)                                 | Legt fest, ob Einschränkungen überprüft werden, während Daten oder nicht eingefügt werden.                                                                                                           |
| Boolesche isFireTriggers()                                                           | Gibt an, wenn der Server die Insert-Trigger für die in die Datenbank eingefügten Zeilen ausgelöst werden soll.                                                                                    |
| "Void" setFireTriggers(Boolean fireTriggers)                                         | Legt fest, ob der Trigger für die in die Datenbank eingefügten Zeilen aus der Server festgelegt werden soll.                                                                                     |
| Boolesche isKeepIdentity()                                                           | Gibt an, ob jeder Quelle Identitätswerte beibehalten werden soll.                                                                                                                          |
| "Void" setKeepIdentity(Boolean keepIdentity)                                         | Legt fest, ob Identitätswerte beibehalten werden soll.                                                                                                                                          |
| Boolesche isKeepNulls()                                                              | Gibt an, ob null-Werte in der Zieltabelle unabhängig von den Einstellungen für Standardwerte beibehalten, oder wenn sie die Standardwerte (falls zutreffend) ersetzt werden soll. |
| "Void" setKeepNulls(Boolean keepNulls)                                               | Legt fest, ob null-Werte in der Zieltabelle unabhängig von den Einstellungen für Standardwerte beibehalten, oder wenn sie die Standardwerte (falls zutreffend) ersetzt werden soll.      |
| Boolesche isTableLock()                                                              | Gibt an, ob "sqlserverbulkcopy" eine Massenaktualisierungssperre für die Dauer des Massenkopiervorgangs abrufen soll.                                                                         |
| "Void" setTableLock(Boolean tableLock)                                               | Legt fest, ob es sich bei "sqlserverbulkcopy" eine Massenaktualisierungssperre für die Dauer des Massenkopiervorgangs abrufen soll.                                                                              |
| Boolesche isUseInternalTransaction()                                                 | Gibt an, ob jeder Batch des Massenkopiervorgangs innerhalb einer Transaktion verarbeitet wird.                                                                                                  |
| "Void" setUseInternalTranscation(Boolean useInternalTransaction)                     | Legt fest, ob jeder Batch des Massenkopiervorgangs innerhalb einer Transaktion verarbeitet wird.                                                                                               |
| Int getBatchSize()                                                                 | Ruft die Anzahl der Zeilen in jedem Batch ab. Am Ende jedes Batches werden die im Batch enthaltenen Zeilen an den Server gesendet                                                                             |
| "Void" setBatchSize(int batchSize)                                                   | Legt die Anzahl der Zeilen in jedem Batch fest. Am Ende jedes Batches werden die im Batch enthaltenen Zeilen an den Server gesendet.                                                                            |
| Int getBulkCopyTimeout()                                                           | Ruft die Anzahl der Sekunden für den Abschluss des Vorgangs ab, bevor ein Timeout eintritt.                                                                                                             |
| "Void" setBulkCopyTimeout(int timeout)                                              | Legt die Anzahl der Sekunden für den Abschluss des Vorgangs fest, bevor ein Timeout eintritt.                                                                                                             |
| Boolesche isAllowEncryptedValueModifications()                                       | Gibt an, ob AllowEncryptedValueModifications-Einstellung aktiviert oder deaktiviert ist.                                                                                                        |
| "void" setAllowEncryptedValueModifications(boolean allowEncryptedValueModifications) | Konfiguriert die AllowEncryptedValueModifications-Einstellung, die für das Massenkopieren mit Always Encrypted-Spalten verwendet wird.                                                                         |
  
### <a name="isqlserverbulkrecord"></a>ISQLServerBulkRecord  

 Die Schnittstelle „ISQLServerBulkRecord“ kann verwendet werden, um Klassen zu erstellen, die Daten aus jeder beliebigen Quelle (wie etwa einer Datei) einlesen und ermöglicht es einer SQLServerBulkCopy-Instanz, ein Massenladen einer SQL Server-Tabelle mit diesen Daten auszuführen.  
  
| Schnittstellenmethoden                   | und Beschreibung                                                                                                                                                                                                                                                                                            |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Legen Sie\<ganze Zahl > getColumnOrdinals()   | Ruft die Ordnungszahlen für jede der in diesem Datensatz enthaltenen Spalten ab.                                                                                                                                                                                                                              |
| Zeichenfolge getColumnName(int column)    | Ruft den Namen der angegebenen Spalte ab.                                                                                                                                                                                                                                                                      |
| Int GetColumnType (Int-Spalte)       | Ruft den JDBC-Datentyp der angegebenen Spalte ab.                                                                                                                                                                                                                                                            |
| Int GetPrecision (Int-Spalte)        | Ruft die Genauigkeit für die angegebene Spalte ab.                                                                                                                                                                                                                                                                |
| Objekt [] getRowData()               | Ruft die Daten für die aktuelle Zeile als Array von Objekten ab.<br /><br /> Jedes Objekt muss mit dem Java-Sprachtyp übereinstimmen, der zur Darstellung des angegebenen JDBC-Datentyps für die angegebene Spalte verwendet wird.  Weitere Informationen und die passenden Zuordnungen finden Sie unter „Grundlegendes zu den Datentypen in JDBC Driver“. |
| Int GetScale (Int-Spalte)            | Ruft die Dezimalstellen für die angegebene Spalte ab.                                                                                                                                                                                                                                                                    |
| Boolesche IsAutoIncrement (Int-Spalte) | Zeigt an, ob es sich bei der Spalte um eine Identitätsspalte handelt.                                                                                                                                                                                                                                            |
| Boolesche Next()"                      | Springt zur nächsten Datenzeile.                                                                                                                                                                                                                                                                         |
  
### <a name="sqlserverbulkcsvfilerecord"></a>SQLServerBulkCSVFileRecord  

Eine einfache Implementierung der ISQLServerBulkRecord-Schnittstelle, die zum Einlesen der einfachen Java-Datentypen aus einer Datei mit Trennzeichen verwendet werden kann, in der jede Zeile eine Datenzeile darstellt.  
  
Hinweise zur Implementierung und Einschränkungen:  
  
1. Die maximal in jeder vorhandenen Zeile zulässige Datenmenge ist durch den verfügbaren Arbeitsspeicher begrenzt, da die Daten zeilenweise gelesen werden.  
  
2. Das Streaming großer Datentypen, wie etwa „varchar(max)“, „varbinary(max)“, „nvarchar(max)“, „sqlxml“, „ntext“ wird nicht unterstützt.  
  
3. Das für die CSV-Datei verwendete Trennzeichen darf an keiner Stelle innerhalb der Daten auftreten und muss ordnungsgemäß escaped werden, wenn es in den regulären Java-Ausdrücken zu den eingeschränkten Zeichen gehört.  
  
4. In der CSV-Dateiimplementierung werden doppelte Anführungszeichen als Teil der Daten behandelt. Beispielsweise würde die Zeile Hallo,”Welt”,”Hallo,Welt” als aus vier Spalten mit den Werten Hallo, “Welt”, “Hallo und Welt” bestehend aufgefasst, wenn als Trennzeichen Komma verwendet wird.  
  
5. Zeilenvorschubzeichen werden als Zeilenendzeichen verwendet und dürfen an keiner Stelle in den Daten auftreten.  
  
| Konstruktor                                                                                                                                                                 | und Beschreibung                                                                                                                                                                                                                                                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SQLServerBulkCSVFileRecord (Zeichenfolge FileToParse zeichenfolgencodierung, Trennzeichen für Zeichenfolgen, booleschen FirstLineIsColumnNamesSQLServerBulkCSVFileRecord (String, String, String, Boolean) | Initialisiert eine neue Instanz der SQLServerBulkCSVFileRecord-Klasse, die jede Zeile in der zu analysierenden Datei „fileToParse“ mit dem angegebenen Trennzeichen und der angegebenen Codierung analysiert. Wenn „firstLineIsColumnNames“ auf „True“ festgelegt ist, wird der Inhalt der ersten Zeile der Datei als Spaltennamen analysiert.  Wenn die Codierung NULL ist, wird die Standardcodierung verwendet.            |
| SQLServerBulkCSVFileRecord (Zeichenfolge FileToParse, Zeichenfolgen, booleschen FirstLineIsColumnNamesSQLServerBulkCSVFileRecord (String, String, Boolean)                           | Initialisiert eine neue Instanz der SQLServerBulkCSVFileRecord-Klasse, die jede Zeile in der zu analysierenden Datei „fileToParse“ mit Komma als Trennzeichen und der angegebenen Codierung analysiert. Wenn „firstLineIsColumnNames“ auf „True“ festgelegt ist, wird der Inhalt der ersten Zeile der Datei als Spaltennamen analysiert.  Wenn die Codierung NULL ist, wird die Standardcodierung verwendet. |
| SQLServerBulkCSVFileRecord (Zeichenfolge FileToParse, booleschen FirstLineIsColumnNamesSQLServerBulkCSVFileRecord (String, Boolean)                                                    | Initialisiert eine neue Instanz der SQLServerBulkCSVFileRecord-Klasse, die jede Zeile in der zu analysierenden Datei „fileToParse“ mit Komma als Trennzeichen und der Standardcodierung analysiert. Wenn „firstLineIsColumnNames“ auf „True“ festgelegt ist, wird der Inhalt der ersten Zeile der Datei als Spaltennamen analysiert.                                                           |
  
| Methode                                                                                                 | und Beschreibung                                                                                         |
| ------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| "Void" AddColumnMetadata (Int PositionInFile, Zeichenfolge ColumnName, Int JdbcType, mit einfacher Genauigkeit Int, Int-Skalierung)  | Fügt Metadaten für die angegebene Spalte in der Datei hinzu.                                                     |
| "Void" close()                                                                                           | Gibt alle dem Dateileser zugeordneten Ressourcen frei.                                             |
| "Void" SetTimestampWithTimezoneFormat (DateTim eFormatter dateTimeFormatter                               | Legt das Format für die Analyse von Zeitstempeldaten aus der Datei auf „java.sql.Types.TIMESTAMP_WITH_TIMEZONE“ fest. |
| "Void" setTimestampWithTimezoneFormat(String dateTimeFormat)setTimeWithTimezoneFormat(DateTimeFormatter) | Legt das Format für die Analyse von Uhrzeitdaten aus der Datei auf „java.sql.Types.TIME_WITH_TIMEZONE“ fest.           |
| "Void" SetTimeWithTimezoneFormat (DateTimeForm unkte DateTimeFormatter)                                   | Legt das Format für die Analyse von Uhrzeitdaten aus der Datei auf „java.sql.Types.TIME_WITH_TIMEZONE“ fest.           |
| "Void" setTimeWithTimezoneFormat(String timeFormat)                                                      | Legt das Format für die Analyse von Uhrzeitdaten aus der Datei auf „java.sql.Types.TIME_WITH_TIMEZONE“ fest.           |
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
