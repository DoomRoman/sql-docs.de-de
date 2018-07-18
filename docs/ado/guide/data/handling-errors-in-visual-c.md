---
title: Behandeln von Fehlern in Visual C++ | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68ce5fb8cc94b130de5171a45b65743e86eec3da
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271689"
---
# <a name="handling-errors-in-visual-c"></a>Behandeln von Fehlern in Visual C++
In COM geben die meisten Vorgänge einen HRESULT-Rückgabecode, der angibt, ob eine Funktion wurde erfolgreich abgeschlossen. Die #import-Direktive Wrappercode um jede "unformatiert" Methode oder Eigenschaft generiert und überprüft das zurückgegebene HRESULT. Wenn das HRESULT Fehler weist darauf hin, löst der Wrappercode einen COM-Fehler vom aufrufenden _com_issue_errorex() mit dem HRESULT-Rückgabecode als Argument an. COM-Fehlerobjekte abgefangen werden können, einem **Try-Catch-** Block. (Aus Gründen der Effizienz fangen Sie einen Verweis auf ein _com_error-Objekt).  
  
 Beachten Sie, dass dies die ADO-Fehler sind: von der ADO-Vorgangsfehler führt. Der zugrunde liegende Anbieter zurückgegebene Fehler werden als **Fehler** Objekte in der **Verbindung** des Objekts **Fehler** Auflistung.  
  
 Die #import-Direktive erstellt nur Fehlerbehandlungsroutinen für Methoden und Eigenschaften, die in der ADO-DLL deklariert. Allerdings können Sie diese gleichen Fehlerbehandlungsmechanismus nutzen durch Ihre eigene Überprüfung von Fehlern Makro oder zur Inlinefunktion-Funktion schreiben. Finden Sie im Visual C++®-Erweiterungen für Beispiele.
