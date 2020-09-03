---
title: Errore-Impossibile avviare il debug sul server Web | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00d27dafd5e44b058cff05b3c478322e45242b3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460039"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Errore: impossibile avviare il debug sul server Web

Quando si tenta di eseguire il debug di un'applicazione ASP.NET in esecuzione in un server Web, è possibile che venga ricevuto questo messaggio di errore: `Unable to start debugging on the Web server` .

Spesso questo errore si verifica a causa di un errore o di una modifica della configurazione che richiede un aggiornamento dei pool di applicazioni, una reimpostazione di IIS o entrambi. È possibile reimpostare IIS aprendo un prompt dei comandi con privilegi elevati e digitando `iisreset` .

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Qual è il messaggio di errore dettagliato?

Il `Unable to start debugging on the Web server` messaggio è generico. In genere, nella stringa di errore viene incluso un messaggio più specifico che può aiutare a identificare la causa del problema o a cercare una correzione più precisa. Di seguito sono riportati alcuni dei messaggi di errore più comuni aggiunti al messaggio di errore principale:

- [IIS non elenca un sito Web corrispondente all'URL di avvio](#IISlist)
- [Il server Web non è configurato in modo corretto](#web_server_config)
- [Non è possibile connettersi al server Web](#unabletoconnect)
- [Il server Web non ha risposto tempestivamente](#webservertimeout)
- [Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) non sembra essere in esecuzione sul computer remoto](#msvsmon)
- [Il server remoto ha restituito un errore](#server_error)
- [Non è stato possibile avviare il debug di ASP.NET](#aspnet)
- [Il debugger non è in grado di connettersi al computer remoto](#cannot_connect)
- [Per verificare gli errori di configurazione comuni, consultare la Guida. Esecuzione della pagina Web all'esterno del debugger può fornire ulteriori informazioni.](#see_help)
- [Operazione non supportata. Errore sconosciuto: *numero errore*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a> IIS non elenca un sito Web corrispondente all'URL di avvio

- Riavviare Visual Studio come amministratore e riprovare a eseguire il debug. Alcuni scenari di debug ASP.NET richiedono privilegi elevati.

    È possibile configurare Visual Studio in modo che venga sempre eseguito come amministratore facendo clic con il pulsante destro del mouse sull'icona di collegamento di Visual Studio, scegliendo **proprietà > avanzate**e scegliendo Esegui sempre come amministratore.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> Il server Web non è configurato correttamente

- Vedere [errore: il server Web non è configurato correttamente](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> Non è possibile connettersi al server Web

- Si eseguono Visual Studio e il server Web nello stesso computer e si esegue il debug con **F5** (anziché **Connetti a processo**)? Aprire le proprietà del progetto e assicurarsi che il progetto sia configurato per la connessione al server Web e all'URL di avvio corretti. (Aprire **proprietà > server > Web** o **Proprietà > eseguire il debug** a seconda del tipo di progetto. Per un progetto Web Form, aprire le **pagine delle proprietà > opzioni di avvio > server**.)

- In caso contrario, riavviare il pool di applicazioni e quindi reimpostare IIS. Per ulteriori informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> Il server Web non ha risposto tempestivamente

- Ripristinare IIS e riprovare a eseguire il debug. È possibile collegare più istanze del debugger al processo IIS; una reimpostazione la termina. Per ulteriori informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) non sembra essere in esecuzione nel computer remoto

- Se si esegue il debug in un computer remoto, verificare di aver [installato e che esegua il debugger remoto](../debugger/remote-debugging.md). Se il messaggio indica un firewall, assicurarsi che siano aperte le [porte corrette del firewall](../debugger/remote-debugger-port-assignments.md) , soprattutto se si usa un firewall di terze parti.
- Se si usa un file HOSTs, assicurarsi che sia configurato correttamente. Se, ad esempio, si esegue il debug con **F5** (anziché **Connetti a processo**), il file degli host deve includere lo stesso URL del progetto delle proprietà del progetto, **Proprietà > server > Web** o **Proprietà > debug**, a seconda del tipo di progetto.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> Il server remoto ha restituito un errore

Controllare il [file di registro IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) per i codici di errore e le informazioni aggiuntive e questo [post di Blog](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)su IIS 7.

Inoltre, di seguito sono riportati alcuni dei codici di errore comuni e alcuni suggerimenti.
- 403 - Accesso negato. Questo errore può essere causato da numerose cause, quindi controllare il file di log e le impostazioni di sicurezza di IIS per il sito Web. Verificare che il web.config del server includa `debug=true` nell'elemento di compilazione. Verificare che la cartella dell'applicazione Web disponga delle autorizzazioni appropriate e che la configurazione del pool di applicazioni sia corretta (è possibile che sia stata modificata una password). Vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck). Se queste impostazioni sono già corrette e si esegue il debug in locale, verificare anche di connettersi al tipo di server e all'URL corretti (in **proprietà > server > Web** o **Proprietà > debug**, a seconda del tipo di progetto).
- (503) Server non disponibile. Il pool di applicazioni potrebbe essere stato interrotto a causa di un errore o di una modifica della configurazione. Riavviare il pool di applicazioni.
- (404) Non trovato. Verificare che il pool di applicazioni sia configurato per la versione corretta di ASP.NET.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a> Non è stato possibile avviare il debug di ASP.NET

- Riavviare il pool di applicazioni e reimpostare IIS. Per ulteriori informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).
- Se si eseguono riscritture URL, testare un web.config di base senza riscritture URL. Vedere la **Nota** sul modulo URL Rewrite in [verificare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> Il debugger non è in grado di connettersi al computer remoto

Se si esegue il debug in locale, aprire le proprietà del progetto in Visual Studio e verificare che il progetto sia configurato per la connessione al server Web e all'URL corretti. (Aprire **proprietà > server > Web** o **Proprietà > eseguire il debug** a seconda del tipo di progetto.)

Questo errore può verificarsi quando si esegue il debug in locale perché Visual Studio è un'applicazione a 32 bit, quindi usa la versione a 64 bit del debugger remoto per eseguire il debug delle applicazioni a 64 bit. Controllare il pool di applicazioni in IIS per assicurarsi che l'opzione **Abilita applicazioni a 32 bit** sia impostata su `true` , riavviare IIS e riprovare.

Inoltre, se si utilizza un file HOSTs, assicurarsi che sia configurato correttamente. Il file HOSTs, ad esempio, deve includere lo stesso URL di progetto delle proprietà del progetto, **proprietà > server > Web** o **Proprietà > debug**, a seconda del tipo di progetto.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> Vedere la guida per gli errori di configurazione comuni. L'esecuzione della pagina Web all'esterno del debugger può fornire ulteriori informazioni.

- Si sta eseguendo Visual Studio e il server Web nello stesso computer? Aprire le proprietà del progetto e assicurarsi che il progetto sia configurato per la connessione al server Web e all'URL di avvio corretti. (Aprire **proprietà > server > Web** o **Proprietà > eseguire il debug** a seconda del tipo di progetto.)

- Se l'operazione non funziona o si sta eseguendo il debug in modalità remota, attenersi alla procedura descritta in [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> Operazione non supportata. Errore sconosciuto: *numero errore*

Se si eseguono riscritture URL, testare un web.config di base senza riscritture URL. Vedere la **Nota** sul modulo URL Rewrite in [verificare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Controllare la configurazione di IIS

Dopo aver eseguito i passaggi descritti qui per risolvere il problema e prima di riprovare a eseguire il debug, potrebbe essere necessario reimpostare IIS. Questa operazione può essere eseguita aprendo un prompt dei comandi con privilegi elevati e digitando `iisreset` .

* Arrestare e riavviare i pool di applicazioni IIS, quindi riprovare.

    È possibile che il pool di applicazioni sia stato interrotto in seguito a un errore. In alternativa, è possibile che sia necessario arrestare e riavviare il pool di applicazioni un'altra modifica apportata alla configurazione.

    > [!NOTE]
    > Se il pool di applicazioni continua a arrestarsi, potrebbe essere necessario disinstallare il modulo URL Rewrite dal pannello di controllo. È possibile reinstallarlo utilizzando l'installazione guidata piattaforma Web (WebPI). Questo problema può verificarsi dopo un aggiornamento del sistema significativo.

* Controllare la configurazione del pool di applicazioni, correggerla, se necessario, quindi riprovare.

    Il pool di applicazioni può essere configurato per una versione di ASP.NET che non corrisponde al progetto di Visual Studio. Aggiornare la versione di ASP.NET nel pool di applicazioni e riavviarla. Per informazioni dettagliate, vedere [IIS 8,0 con ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Inoltre, se le credenziali della password sono state modificate, potrebbe essere necessario aggiornarle nel pool di applicazioni o nel sito Web.  Nel pool di applicazioni aggiornare le credenziali in **Impostazioni avanzate > modello di processo > identità**. Per il sito Web, aggiornare le credenziali in **impostazioni di base > Connetti come...**. Riavviare il pool di applicazioni.

* Verificare che la cartella dell'applicazione Web disponga delle autorizzazioni appropriate.

    Assicurarsi di assegnare a IIS_IUSRS, IUSR o all'utente specifico associato al [pool di applicazioni](/iis/manage/configuring-security/application-pool-identities) i diritti di lettura ed esecuzione per la cartella dell'applicazione Web. Risolvere il problema e riavviare il pool di applicazioni.

* Verificare che in IIS sia installata la versione corretta di ASP.NET.

    La mancata corrispondenza delle versioni di ASP.NET in IIS e nel progetto di Visual Studio può causare questo problema. Potrebbe essere necessario impostare la versione del Framework in web.config. Per installare ASP.NET in IIS, usare l' [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Vedere anche [iis 8,0 con ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, per ASP.NET Core, [host in Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Risolvere gli errori di autenticazione se si usa solo l'indirizzo IP

     Per impostazione predefinita, gli indirizzi IP vengono considerati indirizzi Internet e l'autenticazione NTLM non viene eseguita su Internet. Se il sito Web è configurato in IIS per richiedere l'autenticazione, l'autenticazione ha esito negativo. Per risolvere il problema, è possibile specificare il nome del computer remoto anziché l'indirizzo IP.

## <a name="other-causes"></a>Altre cause

Se la configurazione di IIS non causa il problema, effettuare le seguenti operazioni:

- Riavviare Visual Studio con privilegi di amministratore e riprovare.

    Alcuni scenari di debug di ASP.NET, ad esempio l'uso di Distribuzione Web richiedono privilegi elevati per Visual Studio.

- Se sono in esecuzione più istanze di Visual Studio, riaprire il progetto in un'istanza di Visual Studio (con privilegi di amministratore) e riprovare.

- Se si usa un file host con indirizzi locali, provare a usare l'indirizzo di loopback anziché l'indirizzo IP del computer.

    Se non si usano indirizzi locali, assicurarsi che il file degli host includa lo stesso URL di progetto delle proprietà del progetto, le **proprietà > server > Web** o le **Proprietà > debug**, a seconda del tipo di progetto.

## <a name="more-troubleshooting-steps"></a>Ulteriori passaggi per la risoluzione dei problemi

* Visualizzare la pagina localhost nel browser sul server.

     Se IIS non è installato correttamente, dovrebbero essere visualizzati degli errori quando si digita `http://localhost` in un browser.

     Per ulteriori informazioni sulla distribuzione di in IIS, vedere [iis 8,0 con ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) e per ASP.NET Core [host in Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Creare un'applicazione ASP.NET di base sul server o usare un file di web.config di base).

    Se non è possibile fare in modo che l'app funzioni con il debugger, provare a creare un'applicazione ASP.NET di base localmente nel server e provare a eseguire il debug dell'app di base. (Potrebbe essere necessario usare il modello MVC ASP.NET predefinito). Se è possibile eseguire il debug di un'app di base, può essere utile per identificare le differenze tra le due configurazioni. Individuare le differenze nelle impostazioni nel file di web.config, ad esempio le regole di riscrittura URL.

## <a name="see-also"></a>Vedere anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)