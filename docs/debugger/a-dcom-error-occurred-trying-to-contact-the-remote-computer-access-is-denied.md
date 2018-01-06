---
title: "Si è verificato un errore DCOM durante il tentativo di contattare il computer remoto. Accesso negato. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e0d64aef8fd571032959eb8c3ea2e622a8233620
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Si è verificato un errore DCOM durante il tentativo di contattare il computer remoto. Accesso negato.
Il debug remoto usa DCOM per la comunicazione tra i computer locale e remoto nelle situazioni seguenti:  
  
-   Il debugger è impostato su **modalità di compatibilità nativa** o **modalità di compatibilità gestita** viene archiviato il **strumenti > Opzioni > debug** pagina  
  
-   Si esegue il debug di codice C++ (C++ /CLI) gestito.  
  
-   In Visual Studio 2013, quando **abilitare native modifica e continuazione** viene archiviato il **strumenti > Opzioni > debug** pagina  
  
-   Alcuni scenari di debug di terze parti  
  
 Questo errore si verifica quando il processo di Visual Studio non è in grado di autenticarsi (o le credenziali fornite sono ritenute insufficienti) rispetto al processo del debugger remoto su DCOM. Una o più delle soluzioni seguenti possono risolvere il problema:  
  
-   Disattivare  **Usa modalità di compatibilità nativa** e **Modalità di compatibilità gestita**.  
  
-   In Visual Studio 2013 disattivare **Abilita Modifica e continuazione nativo**.  
  
-   Riavviare entrambi i computer.  
  
-   Se il debug remoto richiede l'immissioni di credenziali, selezionare l'opzione per salvarle.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)