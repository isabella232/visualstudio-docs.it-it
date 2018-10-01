---
title: 'Errore: Autenticazione Kerberos non riesce. | Microsoft Docs'
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
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c18053f9-9074-4bc3-a8bf-13e4acbea921
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed475ecf2ac0bd62dd710832540d599cb367aedc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527333"
---
# <a name="error-kerberos-authentication-failed"></a>Errore: autenticazione Kerberos non riuscita
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errore: errore di autenticazione Kerberos](https://docs.microsoft.com/visualstudio/debugger/error-kerberos-authentication-failed).  
  
Quando si tenta di eseguire il debug remoto, è possibile che venga visualizzato il messaggio di errore seguente:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos auythentication failed.  
```  
  
 L'errore si verifica quando Visual Studio Remote Debugging Monitor è in esecuzione con l'account di sistema locale o l'account del servizio di rete. Utilizzando uno di questi account, il debugger remoto deve stabilire una connessione di autenticazione Kerberos allo scopo di inviare comunicazioni al computer host del debugger Visual Studio.  
  
 L'autenticazione Kerberos non è disponibile nei seguenti casi:  
  
-   Il computer di destinazione o il computer host del debugger si trova in un gruppo di lavoro anziché in un dominio.  
  
     \- oppure -  
  
-   Kerberos è stato disabilitato sul controller di dominio.  
  
 Se l'autenticazione Kerberos non è disponibile, modificare l'account utilizzato per l'esecuzione di Visual Studio Remote Debugging Monitor. Per istruzioni, vedere [errori: servizio di Visual Studio Remote Debugger nel computer di destinazione non può connettersi al computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
 Se il messaggio di errore viene visualizzato nonostante entrambi i computer siano connessi allo stesso dominio, verificare che il nome del computer host del debugger venga risolto correttamente dal DNS del computer di destinazione. Attenersi alla procedura indicata di seguito.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Per verificare la corretta risoluzione del nome del computer host del debugger da parte del DNS del computer di destinazione  
  
1.  Nel computer di destinazione, aprire il **avviare** dal menu **Accessori** e quindi fare clic su **prompt dei comandi**.  
  
2.  Nel **prompt dei comandi** finestra, digitare:  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3.  Nella prima riga della risposta `ping` viene indicato il nome completo del computer e l'indirizzo IP restituito dal DNS per il computer specificato.  
  
4.  Nel computer host del debugger, aprire una **prompt dei comandi** finestra ed eseguire `ipconfig`.  
  
5.  Confrontare i valori degli indirizzi IP.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)



