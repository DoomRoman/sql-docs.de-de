---
title: Beispiel für einfache Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1807de415a5e9641ab431ca7fed123fb097eb90e
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279161"
---
# <a name="basic-data-types-sample"></a>Standarddatentypen - Beispiel
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] veranschaulicht, wie Werte von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Standarddatentypen mithilfe von Abrufmethoden für Resultsets abgerufen und wie diese Werte mithilfe von Updatemethoden für Resultsets aktualisiert werden.  
  
 Die Codedatei für dieses Beispiel heißt „BasicDT.java“ und befindet sich im folgenden Pfad:  
  
 \<*Installationsverzeichnis*> \sqljdbc_\<*Version*>\\<*Sprache*> \samples\datatypes  
  
## <a name="requirements"></a>Anforderungen  
 Wenn Sie diese Beispielanwendung ausführen möchten, müssen Sie die Datei „mssql-jdbc.jar“ in den Klassenpfad aufnehmen. Sie benötigen darüber hinaus Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
 Erstellen Sie in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank außerdem die folgende Tabelle mit den folgenden Beispieldaten:  
  
```sql
use AdventureWorks  
CREATE TABLE DataTypesTable   
   (Col1 int IDENTITY,   
    Col2 char,  
    Col3 varchar(50),   
    Col4 bit,  
    Col5 decimal(18, 2),  
    Col6 money,  
    Col7 datetime,  
    Col8 date,  
    Col9 time,  
    Col10 datetime2,  
    Col11 datetimeoffset  
    );  
  
INSERT INTO DataTypesTable   
VALUES ('A', 'Some text.', 0, 15.25, 10.00, '01/01/2006 23:59:59.991', '01/01/2006', '23:59:59', '01/01/2006 23:59:59.12345', '01/01/2006 23:59:59.12345 -1:00')  
```  
  
> [!NOTE]  
>  Der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zu der JAR-Datei auswählen, finden Sie unter [Systemanforderungen für JDBC Driver](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Beispiel  
 Der folgende Beispielcode stellt eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank her. Anschließend wird eine einzelne Datenzeile aus der DataTypesTable-Testtabelle abgerufen. Danach wird die benutzerdefinierte displayRow-Methode aufgerufen, um alle im Resultset enthaltenen Daten mithilfe der verschiedenen get\<Type>-Methoden der [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse anzuzeigen.  
  
 Anschließend werden die im Resultset enthaltenen Daten mithilfe der verschiedenen update\<Type>-Methoden der SQLServerResultSet-Klasse aktualisiert. Daraufhin wird die [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)-Methode aufgerufen, um die Daten in der Datenbank zu speichern.  
  
 Schließlich wird im Beispiel aktualisiert die Daten in das Resultset auf und ruft anschließend die benutzerdefinierte DisplayRow-Methode erneut aus, um es anzuzeigen.  
  
```java
import java.sql.Connection;
import java.sql.Date;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Time;
import java.sql.Timestamp;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

import microsoft.sql.DateTimeOffset;

public class BasicDT {
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);) {

            String SQL = "SELECT * FROM DataTypesTable";
            ResultSet rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("ORIGINAL DATA", rs);

            // Update the data in the result set.
            rs.updateString(2, "B");
            rs.updateString(3, "Some updated text.");
            rs.updateBoolean(4, true);
            rs.updateDouble(5, 77.89);
            rs.updateDouble(6, 1000.01);
            long timeInMillis = System.currentTimeMillis();
            Timestamp ts = new Timestamp(timeInMillis);
            rs.updateTimestamp(7, ts);
            rs.updateDate(8, new Date(timeInMillis));
            rs.updateTime(9, new Time(timeInMillis));
            rs.updateTimestamp(10, ts);

            // -480 indicates GMT - 8:00 hrs
            ((SQLServerResultSet) rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));

            rs.updateRow();

            // Get the updated data from the database and display it.
            rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("UPDATED DATA", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        System.out.println(rs.getInt(1) + " , " +                 // SQL integer type.
                rs.getString(2) + " , " +                         // SQL char type.
                rs.getString(3) + " , " +                         // SQL varchar type.
                rs.getBoolean(4) + " , " +                        // SQL bit type.
                rs.getDouble(5) + " , " +                         // SQL decimal type.
                rs.getDouble(6) + " , " +                         // SQL money type.
                rs.getTimestamp(7) + " , " +                      // SQL datetime type.
                rs.getDate(8) + " , " +                           // SQL date type.
                rs.getTime(9) + " , " +                           // SQL time type.
                rs.getTimestamp(10) + " , " +                     // SQL datetime2 type.
                ((SQLServerResultSet) rs).getDateTimeOffset(11)); // SQL datetimeoffset type.
        System.out.println();
    }
}
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Arbeiten mit Datentypen &#40;JDBC&#41;](../../../connect/jdbc/working-with-data-types-jdbc.md)  
  
  
