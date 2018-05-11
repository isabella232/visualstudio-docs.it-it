---
title: "Errore: Microsoft Visual Studio Remote Debugging Monitor nel computer remoto non dispone dell'autorizzazione per connettersi al computer | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 266a301bca4953066621d759518c1754052dfeb2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Errore: Microsoft Visual Studio Remote Debugging Monitor sul computer remoto non dispone dell'autorizzazione per connettersi al computer.
Questo errore si verifica quando l'utente che tenta di eseguire Visual Studio Remote Debugging Monitor (msvsmon) non dispone di un account nel computer locale.  
  
### <a name="to-fix-this-problem"></a>Per risolvere il problema  
  
-   Aggiungere un account utente al computer host del debugger di Visual Studio, con lo stesso nome e password dell'account utente che esegue msvsmon nel computer remoto.  
  
     \- oppure -  
  
-   Eseguire msvsmon utilizzando un account utente che dispone dell'autorizzazione per l'invio di chiamate nel computer locale, ovvero di un account utente configurato come utente di dominio e amministratore nel computer in cui è in esecuzione msvsmon. L'account utente per l'esecuzione di msvsmon può essere specificato in due diversi modi:  
  
    -   Fare clic sull'icona di msvsmon e scegliere **runas** menu di scelta rapida  
  
     \- oppure -  
  
    -   Al prompt dei comandi, digitare `runas.exe`.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)