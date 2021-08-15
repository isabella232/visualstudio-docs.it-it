---
description: Quando si tenta di eseguire il debug di un'applicazione ASP.NET in esecuzione in un server Web, è possibile che venga visualizzato il messaggio di errore Impossibile avviare il debug nel server Web."
title: Impossibile avviare il debug nel server Web | Microsoft Docs
ms.date: 05/23/2018
ms.topic: error-reference
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: be368bf085347e6a91a34bb6f3aee38442811fe86df666e426d8d00c473f200a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121311570"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Errore: impossibile avviare il debug sul server Web

Quando si tenta di eseguire il debug di ASP.NET'applicazione in esecuzione in un server Web, è possibile che venga visualizzato il messaggio di errore seguente: `Unable to start debugging on the Web server` .

Spesso questo errore si verifica perché si è verificato un errore o una modifica della configurazione che richiede un aggiornamento dei pool di applicazioni, una reimpostazione di IIS o entrambe. È possibile reimpostare IIS aprendo un prompt dei comandi con privilegi elevati e digitando `iisreset` .

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Qual è il messaggio di errore dettagliato?

Il `Unable to start debugging on the Web server` messaggio è generico. In genere, nella stringa di errore viene incluso un messaggio più specifico che può essere utile per identificare la causa del problema o per cercare una correzione più esatta. Ecco alcuni dei messaggi di errore più comuni che vengono aggiunti al messaggio di errore principale:

- [IIS non elenca un sito Web che corrisponde all'URL di avvio](#IISlist)
- [Il server Web non è configurato in modo corretto](#web_server_config)
- [Impossibile connettersi al server Web](#unabletoconnect)
- [Il server Web non ha risposto in modo corretto](#webservertimeout)
- [Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) non sembra essere in esecuzione sul computer remoto](#msvsmon)
- [Il server remoto ha restituito un errore](#server_error)
- [Impossibile avviare il ASP.NET debug](#aspnet)
- [Il debugger non è in grado di connettersi al computer remoto](#cannot_connect)
- [Per verificare gli errori di configurazione comuni, consultare la Guida. Esecuzione della pagina Web all'esterno del debugger può fornire ulteriori informazioni.](#see_help)
- [Operazione non supportata. Errore sconosciuto: *errornumber*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a> IIS non elenca un sito Web che corrisponde all'URL di avvio

- Riavviare Visual Studio come amministratore e ripetere il debug. Alcuni scenari ASP.NET di debug richiedono privilegi elevati.

    È possibile configurare Visual Studio per l'esecuzione sempre come amministratore facendo clic con il pulsante destro del mouse sull'icona del collegamento Visual Studio, scegliendo Proprietà **> Avanzate** e quindi scegliendo Esegui sempre come amministratore.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> Il server Web non è configurato correttamente

- Vedere [Errore: Il server Web non è configurato correttamente.](../debugger/error-the-web-server-is-not-configured-correctly.md)

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> Impossibile connettersi al server Web

- Si sta eseguendo Visual Studio e il server Web nello stesso computer e si esegue il debug usando **F5** (anziché **Collega a** processo )? Aprire le proprietà del progetto e assicurarsi che il progetto sia configurato per connettersi al server Web corretto e avviare l'URL. Aprire **Proprietà > server web > o** Proprietà > **debug** a seconda del tipo di progetto. Per un Web Forms, aprire Pagine **delle proprietà > opzioni di avvio > Server.**

- In caso contrario, riavviare il pool di applicazioni e quindi reimpostare IIS. Per altre informazioni, vedere [Controllare la configurazione di IIS.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> Il server Web non ha risposto in modo corretto

- Reimpostare IIS e ripetere il debug. Al processo IIS possono essere collegate più istanze del debugger. Una reimpostazione li termina. Per altre informazioni, vedere [Controllare la configurazione di IIS.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) non sembra essere in esecuzione nel computer remoto

- Se si esegue il debug in un computer remoto, assicurarsi di aver [installato e di eseguire il debugger remoto](../debugger/remote-debugging.md). Se il messaggio indica un firewall, assicurarsi che le porte corrette nel [firewall](../debugger/remote-debugger-port-assignments.md) siano aperte, soprattutto se si usa un firewall di terze parti.
- Se si usa un file HOSTS, assicurarsi che sia configurato correttamente. Ad esempio, se si esegue il debug con **F5** (anziché Collega a processo **),** il file HOSTS deve includere lo stesso URL di progetto delle proprietà del progetto, Proprietà **> Server Web >** o Proprietà > Debug **,** a seconda del tipo di progetto.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> Il server remoto ha restituito un errore

Controllare il [file di log](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) di IIS per i sottocodice di errore e altre informazioni e questo post di blog [di](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)IIS 7 .

Di seguito sono inoltre riportati alcuni codici di errore comuni e alcuni suggerimenti.
- 403 - Accesso negato. Esistono molte possibili cause di questo errore, quindi controllare il file di log e le impostazioni di sicurezza IIS per il sito Web. Assicurarsi che l'oggetto del server web.config `debug=true` nell'elemento di compilazione. Assicurarsi che la cartella applicazione Web abbia le autorizzazioni appropriate e che la configurazione del pool di applicazioni sia corretta (è possibile che sia stata modificata una password). Vedere [Controllare la configurazione di IIS.](#vxtbshttpservererrorsthingstocheck) Se queste impostazioni sono già corrette e si esegue il debug in locale, verificare anche che ci si connetta al tipo di server e all'URL **corretti (in** Proprietà > Server Web > o Proprietà **> Debug**, a seconda del tipo di progetto).
- (503) Server non disponibile. Il pool di applicazioni potrebbe essere stato arrestato a causa di un errore o di una modifica della configurazione. Riavviare il pool di applicazioni.
- (404) Non trovato. Assicurarsi che il pool di applicazioni sia configurato per la versione corretta di ASP.NET.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a>Impossibile avviare il ASP.NET debug

- Riavviare il pool di applicazioni e reimpostare IIS. Per altre informazioni, vedere [Controllare la configurazione di IIS.](#vxtbshttpservererrorsthingstocheck)
- Se si stanno eseguendo riscrittura URL, testare un web.config di base senza riscrittura URL. Vedere la **nota sul** modulo di riscrittura URL in Controllare la configurazione [di IIS.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> Il debugger non è in grado di connettersi al computer remoto

Se si esegue il debug in locale, aprire le proprietà del progetto in Visual Studio e assicurarsi che il progetto sia configurato per la connessione al server Web e all'URL corretti. Aprire **Proprietà > server Web > o** Proprietà > **debug** a seconda del tipo di progetto.

Questo errore può verificarsi durante il debug in locale perché Visual Studio è un'applicazione a 32 bit, quindi usa la versione a 64 bit del debugger remoto per eseguire il debug delle applicazioni a 64 bit. Controllare il pool di app in IIS per assicurarsi che Abilita applicazioni a **32 bit** sia impostato su `true` , riavviare IIS e riprovare.

Inoltre, se si usa un file HOSTS, assicurarsi che sia configurato correttamente. Ad esempio, il file HOSTS deve includere lo stesso URL di progetto delle proprietà del progetto, Proprietà **> server Web >** o Proprietà > **Debug**, a seconda del tipo di progetto.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> Vedere la Guida per gli errori di configurazione comuni. L'esecuzione della pagina Web all'esterno del debugger può fornire altre informazioni.

- Si esegue Visual Studio e il server Web nello stesso computer? Aprire le proprietà del progetto e assicurarsi che il progetto sia configurato per connettersi al server Web corretto e avviare l'URL. Aprire **Proprietà > server Web > o** Proprietà > **debug** a seconda del tipo di progetto.

- Se non funziona o si esegue il debug in modalità remota, seguire la procedura descritta in [Controllare la configurazione di IIS.](#vxtbshttpservererrorsthingstocheck)

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> Operazione non supportata. Errore sconosciuto: *errornumber*

Se si stanno eseguendo riscrittura URL, testare un web.config di base senza riscrittura URL. Vedere la **nota sul** modulo di riscrittura URL in Controllare la configurazione [di IIS.](#vxtbshttpservererrorsthingstocheck)

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Controllare la configurazione di IIS

Dopo aver seguito i passaggi descritti qui per risolvere il problema e prima di riprovare a eseguire il debug, potrebbe anche essere necessario reimpostare IIS. A tale scopo, aprire un prompt dei comandi con privilegi elevati e digitare `iisreset` .

* Arrestare e riavviare i pool di applicazioni IIS, quindi riprovare.

    Il pool di applicazioni potrebbe essere stato arrestato a causa di un errore. Oppure, un'altra modifica alla configurazione apportata potrebbe richiedere l'arresto e il riavvio del pool di applicazioni.

    > [!NOTE]
    > Se il pool di applicazioni viene interrotto, potrebbe essere necessario disinstallare URL Rewrite Module dal Pannello di controllo. È possibile reinstallarlo usando l'Installazione installazione piattaforma Web (WebPI). Questo problema può verificarsi dopo un aggiornamento significativo del sistema.

* Controllare la configurazione del pool di applicazioni, correggerla se necessario, quindi riprovare.

    Il pool di applicazioni può essere configurato per una versione di ASP.NET che non corrisponde al Visual Studio progetto. Aggiornare la ASP.NET nel pool di applicazioni e riavviarla. Per informazioni dettagliate, vedere [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Inoltre, se le credenziali della password sono state modificate, potrebbe essere necessario aggiornarle nel pool di applicazioni o nel sito Web.  Nel pool di applicazioni aggiornare le credenziali in **Advanced Impostazioni > Process Model > Identity**. Per il sito Web, aggiornare le credenziali in **Basic Impostazioni > Connessione come...**. Riavviare il pool di applicazioni.

* Verificare che la cartella Dell'applicazione Web abbia le autorizzazioni appropriate.

    Assicurarsi di assegnare a IIS_IUSRS, IUSR o all'utente specifico associato al [pool](/iis/manage/configuring-security/application-pool-identities) di applicazioni i diritti di lettura ed esecuzione per la cartella applicazione Web. Risolvere il problema e riavviare il pool di applicazioni.

* Assicurarsi che sia installata la versione corretta ASP.NET in IIS.

    Le versioni non corrispondenti ASP.NET in IIS e nel progetto Visual Studio possono causare questo problema. Potrebbe essere necessario impostare la versione del framework in web.config. Per installare ASP.NET in IIS, usare Installazione guidata piattaforma [Web (WebPI).](https://www.microsoft.com/web/downloads/platform.aspx) Vedere anche [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5 (Iis 8.0 Using ASP.NET 3.5 and ASP.NET 4.5 (Iis 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) or, for ASP.NET Core, [Host on Windows with IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Risolvere gli errori di autenticazione se si usa solo l'indirizzo IP

     Per impostazione predefinita, gli indirizzi IP vengono considerati indirizzi Internet e l'autenticazione NTLM non viene eseguita su Internet. Se il sito Web è configurato in IIS per richiedere l'autenticazione, l'autenticazione non riesce. Per risolvere il problema, è possibile specificare il nome del computer remoto anziché l'indirizzo IP.

## <a name="other-causes"></a>Altre cause

Se il problema non è causato dalla configurazione di IIS, provare a seguire questa procedura:

- Riavviare Visual Studio con privilegi di amministratore e riprovare.

    Alcuni ASP.NET di debug, ad esempio l'uso Distribuzione Web richiedono privilegi elevati per Visual Studio.

- Se sono in esecuzione più istanze Visual Studio, riaprire il progetto in un'istanza di Visual Studio (con privilegi di amministratore) e riprovare.

- Se si usa un file HOSTS con indirizzi locali, provare a usare l'indirizzo di loopback anziché l'indirizzo IP del computer.

    Se non si usano indirizzi locali, assicurarsi che il file HOSTS includa lo stesso URL di progetto delle proprietà del progetto, Proprietà **> Server Web >** o Proprietà > **Debug**, a seconda del tipo di progetto.

## <a name="more-troubleshooting-steps"></a>Altri passaggi per la risoluzione dei problemi

* Visualizzare la pagina localhost nel browser nel server.

     Se IIS non è installato correttamente, dovrebbero essere visualizzati degli errori quando si digita `http://localhost` in un browser.

     Per altre informazioni sulla distribuzione [in IIS, vedere IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) and, for ASP.NET Core, [Host on Windows with IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Creare un'ASP.NET di base nel server (o usare un file di web.config base).

    Se non è possibile fare in modo che l'app funzioni con il debugger, provare a creare un'applicazione ASP.NET di base in locale nel server e provare a eseguire il debug dell'app di base. È possibile usare il modello MVC ASP.NET predefinito. Se è possibile eseguire il debug di un'app di base, ciò può aiutare a identificare le differenze tra le due configurazioni. Cercare le differenze nelle impostazioni nel file web.config, ad esempio le regole di riscrittura URL.

## <a name="see-also"></a>Vedi anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
