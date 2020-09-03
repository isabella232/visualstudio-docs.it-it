---
title: 'Errore: Impossibile avviare il debug sul server Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185479"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Errore: impossibile avviare il debug sul server Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si prova a eseguire il debug di un'applicazione ASP.NET in esecuzione in un server Web, potrebbe essere visualizzato questo messaggio di errore: Impossibile avviare il debug sul server Web.
  
In molti casi, questo errore si verifica perché IIS non è configurato correttamente.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Controllare la configurazione di IIS

Dopo aver eseguito i passaggi per risolvere un problema descritto qui e prima di riprovare a eseguire il debug, potrebbe essere necessario reimpostare IIS. A tale scopo, aprire un prompt dei comandi dell'amministratore e digitare `iisreset` oppure è possibile eseguire questa operazione in Gestione IIS. 

* Arrestare e riavviare i pool di applicazioni, quindi riprovare.

    È possibile che il pool di applicazioni sia stato interrotto o che un'altra modifica di configurazione effettuata potrebbe richiedere l'arresto e il riavvio del pool di applicazioni.
    
    > [!NOTE]
    > Se il pool di applicazioni continua a arrestarsi, potrebbe essere necessario disinstallare il modulo URL Rewrite dal pannello di controllo e quindi reinstallarlo usando l'installazione guidata piattaforma Web (WPI). Potrebbe trattarsi di un problema dopo un aggiornamento del sistema significativo.

* Controllare la configurazione del pool di applicazioni, correggerla, se necessario, quindi riprovare.

    Se le credenziali della password sono state modificate, potrebbe essere necessario aggiornarle nel pool di applicazioni. Inoltre, se ASP.NET è stato installato di recente, il pool di applicazioni potrebbe essere configurato per la versione errata di ASP.NET. Risolvere il problema e riavviare il pool di applicazioni.
    
* Verificare che la cartella dell'applicazione Web disponga delle autorizzazioni appropriate.

    Assicurarsi di assegnare a IIS_IUSRS o IUSR (o all'utente specifico associato al pool di applicazioni) i diritti di lettura ed esecuzione per la cartella dell'applicazione Web. Risolvere il problema e riavviare il pool di applicazioni.

* Se si usa un file host con indirizzi locali, provare a usare l'indirizzo di loopback anziché l'indirizzo IP del computer.

* Visualizzare la pagina localhost nel browser.

     Se IIS non è installato correttamente, dovrebbero essere visualizzati degli errori quando si digita `http://localhost` in un browser.
     
     Per informazioni sulla distribuzione in IIS, vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o, for ASP.NET Core, [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Verificare che in IIS sia installata la versione corretta di ASP.NET.  Vedere [distribuire un'applicazione ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) o, per ASP.NET Core, [pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Creare un'applicazione ASP.NET di base sul server.

     Se non è possibile fare in modo che l'app funzioni con il debugger, provare a creare un'applicazione ASP.NET di base localmente nel server e provare a eseguire il debug dell'app di base. Se è possibile eseguire il debug di un'app di base, può essere utile per identificare le differenze tra le due configurazioni.
  
* Risolvere gli errori di autenticazione se si usa solo l'indirizzo IP

     Per impostazione predefinita, gli indirizzi IP vengono considerati indirizzi Internet e l'autenticazione NTLM non viene eseguita su Internet. Se il sito Web è configurato in IIS per richiedere l'autenticazione, l'autenticazione avrà esito negativo. Per risolvere il problema, è possibile specificare il nome del computer remoto anziché l'indirizzo IP.
     
## <a name="other-causes"></a>Altre cause

Se si usa una versione precedente di Visual Studio:

- Riavviare Visual Studio con privilegi elevati e riprovare.

    Un bug nelle versioni precedenti (risolto in seguito) richiede privilegi elevati in alcuni scenari di debug di ASP.NET.
    
- Se sono in esecuzione più istanze di Visual Studio, riaprire il progetto in un'istanza di Visual Studio e riprovare.

## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
