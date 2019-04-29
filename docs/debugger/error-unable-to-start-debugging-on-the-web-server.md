---
title: 'Errore: Impossibile avviare il debug sul Server Web | Microsoft Docs'
ms.date: 05/23/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53ffc893b63447ab75a439ea1e093ddaf4b75645
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850107"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Errore: Impossibile avviare il debug sul server Web

Quando si tenta di eseguire il debug di un'applicazione ASP.NET in esecuzione in un server Web, è possibile ottenere questo messaggio di errore: `Unable to start debugging on the Web server`.

Questo errore si verifica spesso, perché una modifica della configurazione o di errore si è verificato che è necessario aggiornare il pool di applicazioni, una reimpostazione di IIS o entrambi. È possibile reimpostare IIS, aprire un prompt dei comandi con privilegi elevati e digitare `iisreset`.

## <a name="specificerrors"></a>Che cos'è il messaggio di errore dettagliato?

Il `Unable to start debugging on the Web server` messaggio è generico. In genere, un messaggio più specifico è incluso nella stringa di errore e che può consentire di identificare la causa del problema o cercare una correzione più precisa. Ecco alcuni dei messaggi di errore più comuni che vengono aggiunte al messaggio di errore principale:

- [IIS non include un sito Web che corrisponde al lancio url](#IISlist)
- [Il server Web non è configurato in modo corretto](#web_server_config)
- [Impossibile connettersi al server Web](#unabletoconnect)
- [Il server web non ha risposto in modo tempestivo](#webservertimeout)
- [Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) non sembra essere in esecuzione sul computer remoto](#msvsmon)
- [Il server remoto ha restituito un errore](#server_error)
- [Non è possibile avviare il debug di ASP.NET](#aspnet)
- [Il debugger non può connettersi al computer remoto](#cannot_connect)
- [Vedere la Guida per gli errori di configurazione comuni. Esecuzione della pagina Web all'esterno del debugger può fornire ulteriori informazioni.](#see_help)

## <a name="IISlist"></a> IIS non include un sito Web che corrisponde al lancio url

- Riavviare Visual Studio come amministratore e ripetere il debug. (Alcuni scenari di debug di ASP.NET richiedono privilegi elevati).

    È possibile configurare Visual Studio per essere eseguita sempre come amministratore facendo clic sull'icona di scelta rapida di Visual Studio, scegliendo **proprietà > Avanzate**e quindi scegliendo essere eseguita sempre come amministratore.

## <a name="web_server_config"></a> Il server Web non è configurato in modo corretto

- Vedere [errore: Il server web non è configurato correttamente](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a> Impossibile connettersi al server Web

- Sono in esecuzione Visual Studio e il server Web nello stesso computer e il debug usando **F5** (anziché **Connetti a processo**)? Aprire le proprietà del progetto e assicurarsi che il progetto è configurato per la connessione al server Web corretto e URL di avvio. (Aprire **proprietà > Web > server** oppure **proprietà > eseguire il Debug** a seconda del tipo di progetto. Per un progetto di Web Form, aprire **pagine delle proprietà > Opzioni di avvio > Server**.)

- In caso contrario, riavviare il Pool di applicazioni e quindi reimpostare IIS. Per altre informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> Il server web non ha risposto in modo tempestivo

- Reimpostare IIS, quindi ripetere il debug. Più istanze del debugger possono essere collegate al processo IIS. una reimpostazione li interrompe. Per altre informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) non sembra essere in esecuzione sul computer remoto

- Se si esegue il debug in un computer remoto, assicurarsi di avere [installato ed eseguono il debugger remoto](../debugger/remote-debugging.md). Se il messaggio indica un firewall, assicurarsi che il [correggere le porte del firewall](../debugger/remote-debugger-port-assignments.md) aperti, in particolare se si usa un firewall di terze parti.
- Se si usa un file host, assicurarsi che sia configurato correttamente. Ad esempio, se il debug usando **F5** (anziché **Connetti a processo**), deve includere lo stesso URL di progetto come proprietà del progetto nel file HOSTS **proprietà > Web > server**  oppure **proprietà > Debug**, a seconda del tipo di progetto.

## <a name="server_error"></a> Il server remoto ha restituito un errore

Verificare i [file di log di IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) per codici secondari di errore e informazioni aggiuntive e questa IIS 7 [post di blog](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

Inoltre, ecco alcuni dei codici errore comuni e alcuni suggerimenti.
- (403) Non consentito. Esistono molte possibili cause di questo errore, controllare il file di log e le impostazioni di sicurezza IIS per il sito web. Assicurarsi che Web. config del server include `debug=true` nell'elemento di compilazione. Assicurarsi che la cartella dell'applicazione Web abbia le autorizzazioni corrette e che la configurazione di Pool di applicazioni sia corretta (la password sia stato modificato). Visualizzare [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck). Se queste impostazioni sono già corrette e si esegue il debug in locale, verificare anche che ci si connette al tipo di server e l'URL (in **proprietà > Web > server** oppure **proprietà > Debug**, a seconda del tipo di progetto).
- (503) Server non disponibile. Il Pool di applicazioni potrebbe aver arrestato a causa di una modifica della configurazione o di errore. Riavviare il Pool di applicazioni.
- (404) Non trovato. Assicurarsi che il Pool di applicazioni sia configurato per la versione corretta di ASP.NET.

## <a name="aspnet"></a> Non è possibile avviare il debug di ASP.NET

- Riavviare il Pool di applicazioni e reimpostare IIS. Per altre informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).
- Se si sta eseguendo l'operazione di riscrittura URL, testare una base file Web. config con alcuna operazione di riscrittura URL. Vedere le **nota** sull'URL Rewrite Module nella [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> Il debugger non può connettersi al computer remoto

Se si esegue il debug in locale, questo errore può verificarsi perché Visual Studio è un'applicazione a 32 bit, in modo che usa la versione a 64 bit del debugger remoto per il debug di applicazioni a 64 bit. Aprire le proprietà del progetto e assicurarsi che il progetto è configurato per la connessione per il server Web e l'URL corretto. (Aprire **proprietà > Web > server** oppure **proprietà > eseguire il Debug** a seconda del tipo di progetto.)

Inoltre, se si usa un file host, assicurarsi che sia configurato correttamente. Ad esempio, gli host file deve includere lo stesso URL di progetto come proprietà del progetto **proprietà > Web > server** oppure **proprietà > Debug**, a seconda del tipo di progetto.

## <a name="see_help"></a> Per verificare gli errori di configurazione comuni, consultare la Guida. Esecuzione della pagina Web all'esterno del debugger può fornire ulteriori informazioni.

- Si esegue Visual Studio e il server Web nello stesso computer? Aprire le proprietà del progetto e assicurarsi che il progetto è configurato per la connessione al server Web corretto e URL di avvio. (Aprire **proprietà > Web > server** oppure **proprietà > eseguire il Debug** a seconda del tipo di progetto.)

- Se il problema persiste o si esegue il debug in modalità remota, seguire i passaggi [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="vxtbshttpservererrorsthingstocheck"></a> Controllare la configurazione di IIS

Dopo aver valutato i passaggi descritti in questa sezione per risolvere il problema e prima di riprovare a eseguire il debug, è necessario anche reimpostare IIS. È possibile farlo aprendo un prompt dei comandi con privilegi elevati e digitando `iisreset`.

* Arrestare e riavviare il pool di applicazioni IIS, quindi riprovare.

    Il Pool di applicazioni potrebbe aver arrestato a causa di un errore. In alternativa, può richiedere un'altra modifica della configurazione apportate arrestare e riavviare il Pool di applicazioni.

    > [!NOTE]
    > Se il Pool di applicazioni continua ad arrestarsi, si potrebbe essere necessario disinstallare il modulo URL Rewrite dal Pannello di controllo. È possibile reinstallarlo utilizzando l'installazione guidata piattaforma Web (WebPI). Questo problema può verificarsi dopo un aggiornamento di sistema significative.

* Controllare la configurazione del Pool di applicazioni, correggere l'errore se necessario e quindi riprovare.

    Il Pool di applicazioni può essere configurato per una versione di ASP.NET che non corrisponda al progetto di Visual Studio. Aggiornare la versione di ASP.NET nel Pool di applicazioni e riavviarlo. Per informazioni dettagliate, vedere [IIS 8.0 Using ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Inoltre, se sono state modificate le credenziali di password, potrebbe essere necessario aggiornarle nel Pool di applicazioni o siti Web.  Nel Pool di applicazioni, aggiornare le credenziali nelle **impostazioni avanzate > modello di processo > identità**. Per il sito Web, aggiornare le credenziali in **le impostazioni di base > Connetti come...** . Riavviare il Pool di applicazioni.

* Verificare che la cartella dell'applicazione Web abbia le autorizzazioni appropriate.

    Assicurarsi che si concede IIS_IUSRS, IUSR, o l'utente specifico associato con il [Pool di applicazioni](/iis/manage/configuring-security/application-pool-identities) read ed execute diritti per la cartella dell'applicazione Web. Risolvere il problema e riavviare il Pool di applicazioni.

* Assicurarsi che sia installata la versione corretta di ASP.NET in IIS.

    Le versioni non corrispondenti di ASP.NET in IIS e nel progetto di Visual Studio possono causare questo problema. Si potrebbe essere necessario impostare la versione di framework nel file Web. config. Per installare ASP.NET in IIS, usare il [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Vedere anche [IIS 8.0 Using ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, per ASP.NET Core [Host in Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Risolvere gli errori di autenticazione se si usa solo l'indirizzo IP

     Per impostazione predefinita, gli indirizzi IP vengono considerati indirizzi Internet e l'autenticazione NTLM non viene eseguita su Internet. Se il sito web è configurata in IIS per richiedere l'autenticazione, l'autenticazione ha esito negativo. Per risolvere questo problema, è possibile specificare il nome del computer remoto anziché l'indirizzo IP.

## <a name="other-causes"></a>Altre cause

Se la configurazione di IIS non causa il problema, provare questi passaggi:

- Riavviare Visual Studio con privilegi di amministratore e riprovare.

    Alcuni scenari di debug di ASP.NET, ad esempio usando distribuzione Web richiedono privilegi elevati per Visual Studio.

- Se si eseguono più istanze di Visual Studio, riaprire il progetto in un'istanza di Visual Studio (con privilegi di amministratore) e ripetere l'operazione.

- Se si usa un file host con gli indirizzi locali, provare a utilizzare l'indirizzo di loopback anziché l'indirizzo IP del computer.

    Se non si usa gli indirizzi locali, verificare che il file HOSTS include lo stesso URL di progetto come proprietà del progetto **proprietà > Web > server** o **proprietà > Debug**, a seconda di tipo di progetto.

## <a name="more-troubleshooting-steps"></a>Ulteriori passaggi di risoluzione dei problemi

* Visualizzare la pagina localhost nel browser sul server.

     Se IIS non è installato correttamente, dovrebbero essere visualizzati degli errori quando si digita `http://localhost` in un browser.

     Per altre informazioni sulla distribuzione in IIS, vedere [IIS 8.0 Using ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) e, per ASP.NET Core [Host in Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Creare un'applicazione ASP.NET nel server (o usare un file Web. config di base).

    Se non è possibile ottenere le app di interagire con il debugger, provare a creare un'applicazione ASP.NET in locale nel server e provare a eseguire il debug di app di base. (Si potrebbe voler usare il modello MVC di ASP.NET predefinito). Se è possibile eseguire il debug di un'app di base, che può consentire di identificare ciò che è diverso tra le due configurazioni. Cercare le differenze nelle impostazioni nel file Web. config, ad esempio le regole di riscrittura dell'URL.

## <a name="see-also"></a>Vedere anche
- [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)