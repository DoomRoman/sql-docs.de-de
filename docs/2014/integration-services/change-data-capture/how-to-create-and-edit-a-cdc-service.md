---
title: Erstellen und Bearbeiten eines CDC Service | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 1b3d47a5-dc89-482d-bbc7-fff04f194c43
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4fdd0df76d4b61896abd3c0478472f20384b05c8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153412"
---
# <a name="how-to-create-and-edit-a-cdc-service"></a>Erstellen und Bearbeiten eines CDC Service
  In diesen Verfahren wird beschrieben, wie Sie über die CDC Service Configuration Console einen neuen Oracle CDC Service erstellen und bearbeiten.  
  
 Für dieses Verfahren ist ein Windows-Benutzer mit Administratorrechten für den Computer erforderlich, auf dem der Oracle CDC Service konfiguriert wird.  
  
### <a name="to-create-a-new-cdc-service"></a>So erstellen Sie einen neuen CDC-Dienst  
  
1.  Wählen Sie im Menü **Start** die Option **CDC Service Configuration for Oracle**.  
  
2.  Klicken im linken Bereich mit der rechten Maustaste auf Local CDC Services und wählen Sie Neuer Dienst aus.  
  
     Sie können auch im **Aktionsbereich** auf **Neuer Dienst** klicken.  
  
3.  Geben Sie die erforderlichen Informationen im Dialogfeld New Oracle CDC Service ein. Informationen zum Eingeben von Informationen im Dialogfeld New Oracle CDC Service finden Sie unter [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) .  
  
     Die im Dialogfeld New Oracle CDC Service angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen werden vom Oracle CDC Service verwendet, wenn der Dienst ausgeführt wird. Diese Anmeldung muss lediglich Mitglied der festen Serverrolle public sein. Es sind keine weiteren Berechtigungen erforderlich. Nachdem neue Oracle CDC-Instanzen hinzugefügt wurden, wird über diese Anmeldung der **db_owner** -Zugriff auf die zugeordneten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC-Datenbanken gewährt.  
  
4.  Klicken Sie auf **OK**, nachdem Sie die erforderlichen Informationen eingegeben haben.  
  
     Zum Erstellen der Definition des Oracle CDC-Windows-Diensts benötigt das Programm Aktualisierungszugriff auf die MSXDBCDC-Datenbank in der zugeordneten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz. Wenn Sie auf **OK**klicken, wird der Benutzer in einem Dialogfeld aufgefordert, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen mit Aktualisierungszugriff auf die MSXDBCDC-Datenbank einzugeben.  
  
     Informationen zu den Daten, die Sie im Dialogfeld Verbindung mit SQL Server herstellen eingeben müssen, finden Sie unter [Connection to SQL Server](connection-to-sql-server.md).  
  
5.  Klicken Sie auf **OK** , um das Dialogfeld New Oracle CDC Service zu schließen.  
  
### <a name="to-edit-a-cdc-service"></a>So bearbeiten Sie einen CDC-Dienst  
  
1.  Wählen Sie im Menü **Start** die Option **CDC Service Configuration for Oracle**.  
  
2.  Wählen Sie im linken Bereich **Local CDC Services** , klicken Sie anschließend mit der rechten Maustaste auf den lokalen Dienst, den Sie bearbeiten möchten, und wählen Sie **Eigenschaften**.  
  
     Sie können den Dienst, den Sie verwenden möchten, auch im mittleren Bereich auswählen und dann im **Aktionsbereich** auf **Eigenschaften**klicken.  
  
3.  Geben Sie die erforderlichen Informationen im Dialogfeld CDC Service Properties ein. Informationen zum Eingeben von Informationen im Dialogfeld CDC Service Properties finden Sie unter [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) .  
  
4.  Klicken Sie nach dem Eingeben der erforderlichen Informationen auf **OK**, um das Dialogfeld Verbindung mit SQL Server herstellen zu öffnen.  
  
     Wenn mit einer Anmeldung ohne Schreibberechtigung für die MSXDBDCDC-Datenbank versucht wird, eine neue Oracle CDC-Instanz zu erstellen, wird eine Fehlermeldung angezeigt. Klicken Sie in diesem Dialogfeld auf **OK** , um das Dialogfeld Verbindung mit SQL Server herstellen anzuzeigen. In diesem Dialogfeld müssen Sie die Anmeldeinformationen für eine Anmeldung eingeben, die über die Schreibberechtigung für die MSXDBCDC-Datenbank verfügt, z.B. die Datenbankrolle **db_owner** .  
  
     Informationen zu den Daten, die Sie im Dialogfeld Verbindung mit SQL Server herstellen eingeben müssen, finden Sie unter [Connection to SQL Server](connection-to-sql-server.md).  
  
5.  Klicken Sie im Dialogfeld Verbindung mit Oracle herstellen auf **OK** . Beide Dialogfelder werden geschlossen, und der Dienst wird aktualisiert und registriert.  
  
## <a name="see-also"></a>Siehe auch  
 [Change Data Capture Designer für Oracle von Attunity](change-data-capture-designer-for-oracle-by-attunity.md)   
 [Erstellen und Bearbeiten eines Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md)  
  
  
