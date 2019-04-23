---
title: 'Errore: Impossibile avviare il debug sul Server Web | Microsoft Docs'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048762"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Errore: Impossibile avviare il debug sul server Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si tenta di eseguire il debug di un'applicazione ASP.NET in esecuzione in un server Web, è possibile ottenere questo messaggio di errore: Impossibile avviare il debug sul server Web.
  
In molti casi, questo errore si verifica perché IIS non è configurato correttamente.

## <a name="vxtbshttpservererrorsthingstocheck"></a> Controllare la configurazione di IIS

Dopo l'esecuzione di passaggi per risolvere un problema descritto qui e prima di riprovare a eseguire il debug, è necessario anche reimpostare IIS. È possibile farlo aprendo un prompt dei comandi di amministratore e digitando `iisreset`, oppure è possibile eseguire questa operazione in Gestione IIS. 

* Arrestare e riavviare il pool di applicazioni, quindi riprovare.

    Il Pool di applicazioni può aver interrotto da un'altra modifica della configurazione apportate può richiedere arrestare e riavviare il Pool di applicazioni.
    
    > [!NOTE]
    > Se il Pool di applicazioni continua ad arrestarsi, si potrebbe essere necessario disinstallare il modulo URL Rewrite dal Pannello di controllo e quindi reinstallarlo utilizzando il programma di installazione piattaforma Web (WPI). Potrebbe trattarsi di un problema, dopo un aggiornamento di sistema significative.

* Controllare la configurazione del Pool di applicazioni, correggere l'errore se necessario e quindi riprovare.

    Se le credenziali di password sono state modificate, devi aggiornarle nel Pool di applicazioni. Inoltre, se è stato recentemente installato ASP.NET, il Pool di applicazioni potrebbe essere configurato per la versione errata di ASP.NET. Risolvere il problema e riavviare il Pool di applicazioni.
    
* Verificare che la cartella dell'applicazione Web abbia le autorizzazioni appropriate.

    Assicurarsi di assegnare IIS_IUSRS o IUSR (o l'utente specifico associato al Pool di applicazioni) di lettura ed esecuzione dei diritti per la cartella dell'applicazione Web. Risolvere il problema e riavviare il Pool di applicazioni.

* Se si usa un file host con gli indirizzi locali, provare a utilizzare l'indirizzo di loopback anziché l'indirizzo IP del computer.

* Visualizzare la pagina localhost nel browser.

     Se IIS non è installato correttamente, dovrebbero essere visualizzati degli errori quando si digita `http://localhost` in un browser.
     
     Per informazioni sulla distribuzione in IIS, vedere [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o, per ASP.NET Core [la pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Assicurarsi che sia installata la versione corretta di ASP.NET in IIS.  Visualizzare [distribuire un'applicazione ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) o, per ASP.NET Core [la pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Creare un'applicazione ASP.NET sul server.

     Se non è possibile ottenere le app di interagire con il debugger, provare a creare un'applicazione ASP.NET in locale nel server e provare a eseguire il debug di app di base. Se è possibile eseguire il debug di un'app di base, che può consentire di identificare ciò che è diverso tra le due configurazioni.
  
* Risolvere gli errori di autenticazione se si usa solo l'indirizzo IP

     Per impostazione predefinita, gli indirizzi IP vengono considerati indirizzi Internet e l'autenticazione NTLM non viene eseguita su Internet. Se il sito web è configurata in IIS per richiedere l'autenticazione, l'autenticazione avrà esito negativo. Per risolvere questo problema, è possibile specificare il nome del computer remoto anziché l'indirizzo IP.
     
## <a name="other-causes"></a>Altre cause

Se si usa una versione precedente di Visual Studio:

- Riavviare Visual Studio con privilegi elevati e riprovare.

    Un bug nelle versioni precedenti (fissato in un secondo momento) necessaria di privilegi elevati in alcuni scenari di debug di ASP.NET.
    
- Se si eseguono più istanze di Visual Studio, aprire nuovamente il progetto in un'unica istanza di Visual Studio e riprovare.

## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
