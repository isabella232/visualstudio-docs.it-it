---
title: Risoluzione di errori specifici nelle distribuzioni ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66a98a822cd9aac6d93b4964e2e8bdadc98972e5
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381899"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Risoluzione di errori specifici nelle distribuzioni ClickOnce
In questo articolo vengono elencati gli errori comuni seguenti che possono verificarsi durante la distribuzione di un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione e vengono descritti i passaggi per risolvere ogni problema.

## <a name="general-errors"></a>Errori generali

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Quando si tenta di individuare un file di applicazione, non viene eseguita alcuna operazione o viene eseguito il rendering XML in Internet Explorer oppure si riceve una finestra di dialogo Esegui o Salva con nome
 Questo errore è probabilmente causato da tipi di contenuto (noti anche come tipi MIME) che non vengono registrati correttamente sul server o sul client.

 Assicurarsi prima di tutto che il server sia configurato per associare l'estensione *dell'applicazione* con il tipo di contenuto "Application/x-ms-application".

 Se il server è configurato correttamente, verificare che nel computer sia installato il .NET Framework 2,0. Se è stato installato il .NET Framework 2,0 e il problema persiste, provare a disinstallare e reinstallare il .NET Framework 2,0 per registrare nuovamente il tipo di contenuto nel client.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Messaggio di errore: "Impossibile recuperare l'applicazione. File mancanti nella distribuzione "o" download dell'applicazione interrotto, verificare la presenza di errori di rete e riprovare più tardi "
 Questo messaggio indica che non è possibile scaricare uno o più file a cui viene fatto riferimento dai [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti. Il modo più semplice per eseguire il debug di questo errore è provare a scaricare l'URL che indica che non è [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] possibile scaricarlo. Di seguito sono riportate alcune possibili cause:

- Se il file di log indica "(403) Forbidden" o "(404) non trovato", verificare che il server Web sia configurato in modo da non bloccare il download del file. Per altre informazioni, vedere [Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

- Se il file *config* è bloccato dal server, vedere la sezione "errore di download quando si tenta di installare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione con un file con estensione config" più avanti in questo articolo.

- Determinare se l'errore si è verificato perché l' `deploymentProvider` URL nel manifesto della distribuzione fa riferimento a una posizione diversa rispetto all'URL usato per l'attivazione.

- Verificare che tutti i file siano presenti nel server. il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] log deve indicare quale file non è stato trovato.

- Verificare se sono presenti problemi di connettività di rete. è possibile ricevere questo messaggio se il computer client è stato offline durante il download.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Errore di download quando si tenta di installare un'applicazione ClickOnce con un file con estensione config
 Per impostazione predefinita, un Visual Basic applicazione basata su Windows include un file di App.config. Si verifica un problema quando un utente tenta di eseguire l'installazione da un server Web che usa Windows Server 2003, perché il sistema operativo blocca l'installazione dei file con *estensione config* per motivi di sicurezza. Per abilitare l'installazione del file *. config* , fare clic su **Usa estensione di file ". deploy"** nella finestra di dialogo **Opzioni di pubblicazione** .

 È anche necessario impostare i tipi di contenuto (noti anche come tipi MIME) in modo appropriato per i file. Application,. manifest e. deploy. Per ulteriori informazioni, vedere la documentazione del server Web.

 Per ulteriori informazioni, vedere "Windows Server 2003: tipi di contenuto bloccati" nei [problemi di configurazione del server e del client nelle distribuzioni ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Messaggio di errore: "l'applicazione non è formattata correttamente;" Il file di log contiene "firma XML non valida"
 Verificare che il file manifesto sia stato aggiornato e che sia stato firmato nuovamente. Ripubblicare l'applicazione usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o usare Mage per firmare di nuovo l'applicazione.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>L'applicazione è stata aggiornata sul server, ma il client non Scarica l'aggiornamento
 Questo problema può essere risolto completando una delle attività seguenti:

- Esaminare l' `deploymentProvider` URL nel manifesto della distribuzione. Assicurarsi di aggiornare i bit nella stessa posizione `deploymentProvider` a cui punta.

- Verificare l'intervallo di aggiornamento nel manifesto della distribuzione. Se questo intervallo è impostato su un intervallo periodico, ad esempio una volta ogni sei ore, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non esegue l'analisi di un aggiornamento fino a quando non viene superato questo intervallo. È possibile modificare il manifesto per analizzare un aggiornamento ogni volta che l'applicazione viene avviata. La modifica dell'intervallo di aggiornamento è un'opzione utile durante la fase di sviluppo per verificare l'installazione degli aggiornamenti, ma rallenta l'attivazione dell'applicazione.

- Provare a riavviare l'applicazione dal menu Start. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]è possibile che l'aggiornamento sia stato rilevato in background, ma verrà richiesto di installare i bit alla successiva attivazione.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Durante l'aggiornamento viene visualizzato un errore con la seguente voce di log: "il riferimento nella distribuzione non corrisponde all'identità definita nel manifesto dell'applicazione"
 Questo errore può verificarsi perché sono stati modificati manualmente i manifesti della distribuzione e dell'applicazione e la descrizione dell'identità di un assembly in un manifesto potrebbe non essere sincronizzata con l'altra. L'identità di un assembly è costituita dal nome, dalla versione, dalle impostazioni cultura e dal token di chiave pubblica. Esaminare le descrizioni delle identità nei manifesti e correggere eventuali differenze.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>L'attivazione per la prima volta dal disco locale o CD-ROM ha esito positivo, ma l'attivazione successiva dal menu Start non riesce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Usa l'URL del provider di distribuzione per ricevere gli aggiornamenti per l'applicazione. Verificare che il percorso a cui punta l'URL sia corretto.

#### <a name="error-cannot-start-the-application"></a>Errore: "Impossibile avviare l'applicazione"
 Questo messaggio di errore indica in genere che si è verificato un problema durante l'installazione dell'applicazione nell' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivio. Si è verificato un errore nell'applicazione oppure l'archivio è danneggiato. Il file di log potrebbe indicare dove si è verificato l'errore.

 Eseguire le operazioni seguenti:

- Verificare che l'identità del manifesto di distribuzione, l'identità del manifesto dell'applicazione e l'identità del file EXE dell'applicazione principale siano univoche.

- Verificare che i percorsi di file non superino i 100 caratteri. Se l'applicazione contiene percorsi di file troppo lunghi, è possibile che vengano superate le limitazioni relative al percorso massimo che è possibile archiviare. Provare ad abbreviare i percorsi e reinstallare.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Le impostazioni di PrivatePath nel file di configurazione dell'applicazione non sono rispettate
 Per usare PrivatePath (percorsi di sondaggio Fusion), l'applicazione deve richiedere l'autorizzazione di attendibilità totale. Provare a modificare il manifesto dell'applicazione in modo da richiedere l'attendibilità totale, quindi riprovare.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Durante la disinstallazione viene visualizzato un messaggio che indica che non è stato possibile disinstallare l'applicazione
 Questo messaggio indica in genere che l'applicazione è già stata rimossa o che l'archivio è danneggiato. Dopo aver fatto clic su **OK**, la voce **Aggiungi/Rimuovi programma** verrà rimossa.

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Durante l'installazione viene visualizzato un messaggio che indica che le dipendenze della piattaforma non sono installate
 Manca un prerequisito nella GAC (Global Assembly Cache) necessario per l'esecuzione dell'applicazione.

## <a name="publishing-with-visual-studio"></a>Pubblicazione con Visual Studio

#### <a name="publishing-in-visual-studio-fails"></a>Errore di pubblicazione in Visual Studio
 Assicurarsi di avere il diritto di pubblicare nel server di destinazione. Se, ad esempio, si è connessi a un computer Terminal Server come utente normale, non come amministratore, è probabile che non si disponga dei diritti necessari per la pubblicazione nel server Web locale.

 Se si sta pubblicando con un URL, verificare che nel computer di destinazione sia abilitato Estensioni del server di FrontPage.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Messaggio di errore: Impossibile creare il sito Web ' \<site> '. I componenti per la comunicazione con Estensioni del server di FrontPage non sono installati.
 Verificare che il Microsoft Visual Studio Web Authoring Component sia installato nel computer da cui si esegue la pubblicazione. Per gli utenti Express, questo componente non è installato per impostazione predefinita. Per altre informazioni, vedere [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Messaggio di errore: Impossibile trovare il file ' Microsoft. Windows. Common-Controls, Version = 6.0.0.0, culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture = \* , Type = Win32'
 Questo messaggio di errore viene visualizzato quando si tenta di pubblicare un'applicazione WPF con gli stili di visualizzazione abilitati. Per risolvere questo problema, vedere [procedura: pubblicare un'applicazione WPF con stili di visualizzazione abilitati](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).

## <a name="using-mage"></a>Uso di Mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Si è tentato di firmare con un certificato nell'archivio certificati e una finestra di messaggio ricevuta vuota
 Nella finestra di dialogo **firma** è necessario:

- Selezionare **firma con un certificato archiviato**e

- Selezionare un certificato dall'elenco; il primo certificato non è la selezione predefinita.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Se si fa clic sul pulsante "non firmare", viene generata un'eccezione
 Questo problema è un bug noto. Tutti i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti devono essere firmati. È sufficiente selezionare una delle opzioni di firma e quindi fare clic su **OK**.

## <a name="additional-errors"></a>Errori aggiuntivi
 Nella tabella seguente vengono illustrati alcuni messaggi di errore comuni che possono essere ricevuti da un utente del computer client quando l'utente installa un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. Ogni messaggio di errore viene visualizzato accanto a una descrizione della più probabile cause dell'errore.

| Messaggio di errore | Descrizione |
| - | - |
| Impossibile avviare l'applicazione. Contattare l'autore dell'applicazione.<br /><br /> Impossibile avviare l'applicazione. Per assistenza, contattare il fornitore dell'applicazione. | Si tratta di messaggi di errore generici che si verificano quando non è possibile avviare l'applicazione e non sono stati trovati altri motivi specifici. Spesso ciò significa che l'applicazione è in qualche modo danneggiata o che l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivio è danneggiato. |
| Impossibile continuare. L'applicazione non è formattata correttamente. Per assistenza, contattare l'autore dell'applicazione.<br /><br /> Convalida dell'applicazione non riuscita. Impossibile continuare.<br /><br /> Impossibile recuperare i file dell'applicazione. File danneggiati nella distribuzione. | Uno dei file manifesto della distribuzione non è sintatticamente valido o contiene un hash che non può essere riconciliato con il file corrispondente. Questo errore può anche indicare che il manifesto incorporato all'interno di un assembly è danneggiato. Ricreare la distribuzione e ricompilare l'applicazione oppure trovare e correggere gli errori manualmente nei manifesti. |
| Impossibile recuperare l'applicazione. Errore di autenticazione.<br /><br /> L'installazione dell'applicazione non è riuscita. Impossibile individuare i file delle applicazioni nel server. Per assistenza, contattare l'autore dell'applicazione o l'amministratore. | Non è possibile scaricare uno o più file nella distribuzione perché non si è autorizzati ad accedervi. Ciò può essere causato da un errore 403 non consentito restituito da un server Web, che può verificarsi se uno dei file nella distribuzione termina con un'estensione che rende il server Web considerato come un file protetto. Inoltre, una directory che contiene uno o più file dell'applicazione potrebbe richiedere un nome utente e una password per accedere a. |
| Non è possibile scaricare l'applicazione. Nell'applicazione mancano i file necessari. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema. | Impossibile trovare nel server uno o più file elencati nel manifesto dell'applicazione. Verificare che siano stati caricati tutti i file dipendenti della distribuzione, quindi riprovare. |
| Il download dell'applicazione non è riuscito. Controllare la connessione di rete o contattare l'amministratore di sistema o il provider di servizi di rete. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Impossibile stabilire una connessione di rete al server. Esaminare la disponibilità del server e lo stato della rete. |
| URLDownloadToCacheFile non riuscito con HRESULT ' \<number> '. Si è verificato un errore durante il tentativo di scaricare ' \<file> '. | Se un utente ha impostato l'opzione di sicurezza avanzata di Internet Explorer "Avvisa se si passa dalla modalità protetta alla modalità non protetta" nel computer di destinazione della distribuzione e se l'URL di installazione dell'applicazione ClickOnce da installare viene reindirizzato da un sito non protetto a un sito sicuro (o viceversa), l'installazione avrà esito negativo perché l'avviso viene interrotto da Internet Explorer.<br /><br /> Per correggere l'errore, è possibile eseguire una delle attività seguenti:<br /><br /> -Deselezionare l'opzione sicurezza.<br />-Assicurarsi che l'URL di installazione non venga reindirizzato in modo da modificare le modalità di sicurezza.<br />-Rimuovere completamente il reindirizzamento e puntare all'URL di installazione effettivo. |
| Si è verificato un errore durante la scrittura sul disco rigido. Lo spazio disponibile sul disco potrebbe non essere sufficiente. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema. | Questo può indicare una quantità di spazio su disco insufficiente per l'archiviazione dell'applicazione, ma può anche indicare un errore di I/O più generale quando si tenta di salvare i file dell'applicazione nell'unità. |
| Impossibile avviare l'applicazione. Lo spazio disponibile sul disco non è sufficiente. | Il disco rigido è pieno. Cancellare lo spazio e provare a eseguire di nuovo l'applicazione. |
| È in corso un tentativo di caricamento di un numero eccessivo di attivazioni distribuite in una sola volta. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]limita il numero di applicazioni diverse che possono essere avviate allo stesso tempo. Questo è in gran parte utile per la protezione da tentativi dannosi di istigare attacchi Denial of Service contro il servizio locale. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gli utenti che tentano di avviare la stessa applicazione ripetutamente, in rapida successione, finiranno solo con una singola istanza dell'applicazione. |
| Non è possibile attivare i collegamenti sulla rete. | I collegamenti a un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione possono essere avviati solo sul disco rigido locale. Non possono essere avviati aprendo un URL che punta a un file di collegamento in un server remoto. |
| L'applicazione è troppo grande per l'esecuzione online in attendibilità parziale. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema. | Un'applicazione che viene eseguita con attendibilità parziale non può essere maggiore della metà delle dimensioni della quota dell'applicazione online, che per impostazione predefinita è 250 MB. |

## <a name="see-also"></a>Vedi anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)