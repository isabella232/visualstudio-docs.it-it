---
title: Impossibile eseguire la connessione a Microsoft Visual Studio Remote Debugging Monitor
description: Informazioni sul significato di "Impossibile Connessione alla Microsoft Visual Studio Remote Debugging Monitor", alle possibili cause e alle soluzioni.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 04/14/2020
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8b7c3954bde20a328276503aa36db6e6ba47d743
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635919"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Impossibile eseguire la connessione a Microsoft Visual Studio Remote Debugging Monitor
Questo messaggio può verificarsi perché il monitoraggio del debug remoto non è configurato correttamente nel computer remoto o il computer remoto non è accessibile a causa di problemi di rete o della presenza di un firewall.

> [!IMPORTANT]
> Se si ritiene di aver ricevuto questo messaggio a causa di un bug del prodotto, segnalare [questo problema](../ide/how-to-report-a-problem-with-visual-studio.md) Visual Studio. Per altre informazioni, vedere [Developer Community](https://developercommunity.visualstudio.com/home) per informazioni su come contattare Microsoft.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Qual è il messaggio di errore dettagliato?

Il `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` messaggio è generico. In genere, nella stringa di errore viene incluso un messaggio più specifico che può essere utile per identificare la causa del problema o cercare una correzione più esatta. Ecco alcuni dei messaggi di errore più comuni aggiunti al messaggio di errore principale:

- [Il debugger non può connettersi al computer remoto. Il debugger non è riuscito a risolvere il nome computer specificato](#cannot_connect)
- [Richiesta di connessione rifiutata dal debugger remoto](#rejected)
- [La connessione con l'endpoint remoto è stata terminata](#connection_terminated)
- [Accesso non valido al percorso di memoria](#invalid_access)
- [Non esiste alcun server in base al nome specificato in esecuzione nel computer remoto](#no_server)
- [Il nome richiesto era valido, ma non sono stati trovati dati del tipo richiesto](#valid_name)
- [Il Visual Studio Remote Debugger nel computer di destinazione non è in grado di connettersi al computer](#cant_connect_back)
- [Accesso negato](#access_denied)
- [Si è verificato un errore specifico del pacchetto di sicurezza](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a> Il debugger non può connettersi al computer remoto. Il debugger non è riuscito a risolvere il nome computer specificato

Provare questi passaggi:

1. Assicurarsi di immettere un nome di computer  e un numero di porta validi nella finestra di dialogo Collega a processo o nelle proprietà del progetto .Per impostare le proprietà, vedere [questi passaggi.](#server_incorrect) Il formato del nome del computer deve essere il seguente:

    `computername:port`

    > [!NOTE]
    > Il numero di porta deve corrispondere [al numero di porta del debugger remoto,](../debugger/remote-debugger-port-assignments.md)che deve essere in *esecuzione* nel computer di destinazione.

2. Se il nome del computer non funziona, provare invece l'indirizzo IP e il numero di porta.

3. Assicurarsi che la versione del debugger remoto in esecuzione nel computer di destinazione corrisponda alla versione di Visual Studio. Per ottenere la versione corretta del debugger remoto, vedere [Debug remoto](../debugger/remote-debugging.md).

    > [!TIP]
    > Se ci si connette al processo e ci si connette correttamente ma non viene visualizzato il processo desiderato, selezionare la casella di controllo Mostra processi **di tutti gli utenti**. Verranno visualizzati i processi se si è connessi con un account utente diverso.

4. Se questi passaggi non risolvono l'errore, vedere [Il computer remoto non è raggiungibile.](#dns)

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a> Richiesta di connessione rifiutata dal debugger remoto

Nella finestra **di dialogo** Collega a processo o nelle proprietà del progetto assicurarsi che il nome del computer remoto e il numero di porta corrispondano al nome e al numero di porta visualizzati nella finestra del debugger remoto. Se non è corretto, correggere e riprovare.

Se questi valori sono corretti e il messaggio indica Windows **modalità** di autenticazione, verificare che il debugger remoto sia nella modalità di autenticazione corretta ( Strumenti **> Opzioni**).

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a> La connessione con l'endpoint remoto è stata terminata

Se si esegue il debug di un Servizio app di Azure app, provare a usare il comando Collega [debugger](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) da Cloud Explorer o Esplora server invece di **Collega a processo**.

Se si usa Collega **a processo per eseguire il** debug:

- Nella finestra **di dialogo** Collega a processo o nelle proprietà del progetto assicurarsi che il nome del computer remoto e il numero di porta corrispondano al nome e al numero di porta visualizzati nella finestra del debugger remoto. Se non è corretto, correggere e riprovare.

- Se si sta tentando di connettersi usando un nome host, provare a usare un indirizzo IP.

- Controllare il registro applicazioni nel server (Visualizzatore eventi in Windows) per informazioni più dettagliate per risolvere il problema.

- In caso contrario, provare a Visual Studio con privilegi di amministratore e quindi riprovare.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a> Accesso non valido al percorso di memoria

An internal error occurred. Riavviare Visual Studio e riprovare.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a> Non esiste alcun server in base al nome specificato in esecuzione nel computer remoto

Visual Studio non è stato possibile connettersi al debugger remoto. Questo messaggio può verificarsi per diversi motivi:

- Il debugger remoto potrebbe essere in esecuzione con un account utente diverso. Vedere [questi passaggi](#user_accounts)

- La porta è bloccata nel firewall. Assicurarsi che il firewall non [blocchi la richiesta,](#firewall)soprattutto se si usa un firewall di terze parti.

- La versione del debugger remoto non corrisponde a Visual Studio. Per ottenere la versione corretta del debugger remoto, vedere [Debug remoto](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a> Il nome richiesto era valido, ma non sono stati trovati dati del tipo richiesto

Il computer remoto esiste, ma Visual Studio non è stato possibile connettersi al debugger remoto. Questo messaggio può verificarsi per diversi motivi:

- Un problema DNS impedisce la connessione. Vedere [questi passaggi.](#dns)

- Il debugger remoto potrebbe essere in esecuzione con un account utente diverso. Seguire [questa procedura.](#user_accounts)

- La porta è bloccata nel firewall. Assicurarsi che il firewall non [blocchi la richiesta,](#firewall)soprattutto se si usa un firewall di terze parti.

- La versione del debugger remoto non corrisponde a Visual Studio. Per ottenere la versione corretta del debugger remoto, vedere [Debug remoto](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>Il Visual Studio Remote Debugger nel computer di destinazione non è in grado di connettersi al computer

Il debugger remoto potrebbe essere in esecuzione con un account utente diverso. Nel debugger remoto aprire Strumenti > **autorizzazioni** per aggiungere l'utente alle autorizzazioni del debugger remoto. Per altre informazioni, vedere [Il debugger remoto è in esecuzione con un account utente diverso.](#user_accounts)

Se il messaggio di errore menziona anche un firewall, il firewall nel computer locale potrebbe impedire la comunicazione dal computer remoto a Visual Studio. Vedere [questi passaggi.](#firewall)

## <a name="access-denied"></a><a name="access_denied"></a> Accesso negato

Questo errore può essere visualizzato se si tenta di eseguire il debug in un computer remoto a 64 bit da un computer a 32 bit (non supportato).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a> Si è verificato un errore specifico del pacchetto di sicurezza

Potrebbe trattarsi di un problema legacy specifico di Windows XP e Windows 7. Vedere queste [informazioni.](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)

## <a name="causes-and-recommendations"></a>Cause e raccomandazioni

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> Il computer remoto non è raggiungibile

Se non è possibile connettersi usando il nome del computer remoto, provare a usare l'indirizzo IP. È possibile usare `ipconfig` in una riga di comando nel computer remoto per ottenere l'indirizzo IPv4. Se si usa un file HOSTS, verificare che sia configurato correttamente.

In caso di errore, verificare che il computer remoto sia accessibile in rete[(eseguire il ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) del computer remoto). Il debug remoto tramite Internet non è supportato, ad eccezione di alcuni Microsoft Azure scenari.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a> Il nome del server non è corretto o il software di terze parti interferisce con il debugger remoto

In Visual Studio esaminare le proprietà del progetto e verificare che il nome del server sia corretto. Vedere gli argomenti [per C# e Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) e [C++.](../debugger/remote-debugging-cpp.md#remote_cplusplus) Per ASP.NET, aprire **Proprietà/Web/Server** o **Proprietà/Debug** a seconda del tipo di progetto.

> [!NOTE]
> Se ci si connette al processo, le impostazioni remote nelle proprietà del progetto non vengono usate.

Se il nome del server è corretto, il software antivirus o un firewall di terze parti potrebbe bloccare il debugger remoto. Quando si esegue il debug in locale, ciò può verificarsi perché Visual Studio è un'applicazione a 32 bit, quindi usa la versione a 64 bit del debugger remoto per eseguire il debug di applicazioni a 64 bit. I processi a 32 e 64 bit comunicano usando la rete locale all'interno del computer locale. Il traffico di rete resta all'interno del computer, ma è possibile che un software per la sicurezza di terze parti blocchi la comunicazione.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a> Il debugger remoto è in esecuzione con un account utente diverso

Per impostazione predefinita, il debugger remoto accetterà solo le connessioni dell'utente che ha avviato il debugger remoto e i membri del gruppo Administrators. Agli utenti aggiuntivi devono essere concesse autorizzazioni in modo esplicito.

Per risolvere il problema, usare uno dei metodi seguenti:

- Aggiungere il Visual Studio utente alle autorizzazioni del debugger remoto (nella finestra del debugger remoto scegliere Strumenti > **autorizzazioni**).

- Nel computer remoto riavviare il debugger remoto con lo stesso account utente e la stessa password in uso nel computer Visual Studio remoto.

    > [!NOTE]
    > Se si esegue il debugger remoto in un server remoto, fare clic con il pulsante destro del mouse sull'app Debugger remoto e scegliere Esegui come amministratore **.** In caso contrario, è possibile eseguire il debugger remoto come servizio. Se non è in esecuzione in un server remoto, è sufficiente avviarlo normalmente.

- È possibile avviare il debugger remoto dalla riga di comando con **il parametro \<username> /allow:** `msvsmon /allow <username@computer>` .

- In alternativa, è possibile consentire a qualsiasi utente di eseguire il debug remoto. Nella finestra del debugger remoto passare alla finestra di dialogo **Strumenti > Opzioni**. Se si seleziona   **Nessuna autenticazione**, è possibile selezionare **Consenti debug da parte di qualsiasi utente**. È tuttavia consigliabile provare questa opzione solo se le altre opzioni hanno esito negativo o se si è in una rete privata.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a> Il firewall nel computer remoto non consente le connessioni in ingresso al debugger remoto
 Il firewall nel computer Visual Studio e il firewall nel computer remoto devono essere configurati per consentire la comunicazione tra Visual Studio e il debugger remoto. Per informazioni sulle porte usate dal debugger remoto, vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Per informazioni sulla configurazione del firewall di Windows, vedere [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La versione del debugger remoto non corrisponde alla versione di Visual Studio
 La versione di Visual Studio in esecuzione in locale deve corrispondere alla versione di Remote Debugging Monitor in esecuzione nel computer remoto. Per risolvere questo problema, scaricare e installare la versione corrispondente di Remote Debugging Monitor. Per ottenere la versione corretta del debugger remoto, vedere [Debug remoto.](../debugger/remote-debugging.md)

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Il computer locale e quello remoto hanno modalità di autenticazione diverse
 Il computer locale e quello remoto devono usare la stessa modalità di autenticazione. Per risolvere questo problema, assicurarsi che entrambi i computer usino la stessa modalità di autenticazione. È possibile modificare la modalità di autenticazione. Nella finestra del debugger remoto passare alla finestra di **dialogo Strumenti > opzioni.**

 Per altre informazioni sulle modalità di autenticazione, vedere [Panoramica di Autenticazione di Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Il software antivirus sta bloccando le connessioni
 Il software antivirus di Windows consente le connessioni del debugger remoto, mentre altri software antivirus di terze parti potrebbero bloccarle. Controllare la documentazione del software antivirus per scoprire come consentire queste connessioni.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>I criteri di sicurezza di rete bloccano la comunicazione tra il computer remoto e Visual Studio
 Esaminare la sicurezza della rete per assicurarsi che non blocchi la comunicazione. Per altre informazioni sui criteri Windows sicurezza di rete, vedere Impostazioni [dei criteri di sicurezza.](/windows/device-security/security-policy-settings/security-policy-settings)

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>La rete è troppo occupata per supportare il debug remoto
 Provare a eseguire il debug remoto in un altro momento oppure pianificare il lavoro sulla rete per un altro orario.

## <a name="more-help"></a>Altre informazioni
 Per ottenere altre informazioni della Guida sul debugger remoto, aprire la pagina della Guida del debugger remoto (Guida per **>'utilizzo** nel debugger remoto).

## <a name="see-also"></a>Vedi anche
- [Debug remoto](../debugger/remote-debugging.md)
