---
title: "Errore: Microsoft Visual Studio Remote Debugging Monitor nel computer remoto non dispone dell'autorizzazione per connettersi al computer | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, Windows version error
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a62f20afc5ba57da64205491a3c5dfeabd75daf
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590445"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Errore: Microsoft Visual Studio Remote Debugging Monitor sul computer remoto non dispone dell'autorizzazione per connettersi al computer.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errori: The Microsoft Visual Studio Remote Debugging Monitor nel computer remoto non dispone dell'autorizzazione per connettersi al computer](https://docs.microsoft.com/visualstudio/debugger/error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer).  
  
Questo errore si verifica quando l'utente che tenta di eseguire Visual Studio Remote Debugging Monitor (msvsmon) non dispone di un account nel computer locale.  
  
### <a name="to-fix-this-problem"></a>Per risolvere il problema  
  
-   Aggiungere un account utente al computer host del debugger di Visual Studio, con lo stesso nome e password dell'account utente che esegue msvsmon nel computer remoto.  
  
     \- oppure -  
  
-   Eseguire msvsmon utilizzando un account utente che dispone dell'autorizzazione per l'invio di chiamate nel computer locale, ovvero di un account utente configurato come utente di dominio e amministratore nel computer in cui è in esecuzione msvsmon. L'account utente per l'esecuzione di msvsmon può essere specificato in due diversi modi:  
  
    -   Fare doppio clic sull'icona di msvsmon e scegliere **runas** menu di scelta rapida  
  
     \- oppure -  
  
    -   Al prompt dei comandi, digitare `runas.exe`.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto tra domini](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)



