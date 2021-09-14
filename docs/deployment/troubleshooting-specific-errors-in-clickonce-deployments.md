---
title: Risoluzione degli errori (ClickOnce distribuzione)
description: Questo articolo descrive gli errori comuni che possono verificarsi quando si distribuisce un'applicazione ClickOnce e illustra i passaggi per risolvere ogni problema.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4cfbfa1c13a6006303b1fd0fa164d78c7f4e6b9f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709886"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Risoluzione di errori specifici nelle distribuzioni ClickOnce
Questo articolo elenca gli errori comuni seguenti che possono verificarsi quando si distribuisce un'applicazione e illustra [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i passaggi per risolvere ogni problema.

## <a name="general-errors"></a>Errori generali

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Quando si tenta di individuare un file dell'applicazione, non si verifica nulla o viene eseguito il rendering XML in Internet Explorer oppure viene visualizzata la finestra di dialogo Esegui o Salva con nome
 Questo errore è probabilmente causato dal fatto che i tipi di contenuto (noti anche come tipi MIME) non vengono registrati correttamente nel server o nel client.

 Assicurarsi prima di tutto che il server sia configurato per associare l'estensione *.application* al tipo di contenuto "application/x-ms-application".

 Se il server è configurato correttamente, verificare che il .NET Framework 2.0 sia installato nel computer. Se è installato .NET Framework 2.0 e il problema persiste, provare a disinstallare e reinstallare .NET Framework 2.0 per registrare nuovamente il tipo di contenuto nel client.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Il messaggio di errore indica che non è possibile recuperare l'applicazione. File mancanti nella distribuzione" o "Il download dell'applicazione è stato interrotto, verificare la presenza di errori di rete e riprovare più tardi"
 Questo messaggio indica che non è possibile scaricare uno o più file a cui fanno riferimento [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i manifesti. Il modo più semplice per eseguire il debug di questo errore è provare a scaricare l'URL che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] indica che non è possibile eseguire il download. Ecco alcune possibili cause:

- Se il file di log indica "(403) Accesso negato" o "(404) Non trovato", verificare che il server Web sia configurato in modo che non blocchi il download di questo file. Per altre informazioni, vedere [Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

- Se il file *.config* viene bloccato dal server, vedere la sezione "Errore di download quando si tenta di installare un'applicazione con un file .config" più avanti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in questo articolo.

- Determinare se questo errore si è verificato perché l'URL nel manifesto della distribuzione punta a un percorso diverso da quello usato `deploymentProvider` per l'attivazione.

- Verificare che tutti i file siano presenti nel server. il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] log dovrebbe indicare quale file non è stato trovato.

- Verificare se sono presenti problemi di connettività di rete. È possibile ricevere questo messaggio se il computer client è passato offline durante il download.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Errore di download quando si tenta di installare un'ClickOnce con un file .config
 Per impostazione predefinita, un'Visual Basic Windows basata su criteri include un file App.config. Si verifica un problema quando un utente tenta di eseguire l'installazione da un server Web che usa Windows Server 2003, perché tale sistema operativo blocca l'installazione dei file *.config* per motivi di sicurezza. Per abilitare *l'.config* file di pubblicazione, fare clic su Usa **estensione di file ".deploy"** nella finestra di dialogo **Opzioni** di pubblicazione .

 È inoltre necessario impostare i tipi di contenuto (noti anche come tipi MIME) in modo appropriato per i file con estensione application, manifest e deploy. Per altre informazioni, vedere la documentazione del server Web.

 Per altre informazioni, vedere "Windows Server 2003: Tipi di contenuto bloccati" in Problemi di configurazione di server e [client ClickOnce distribuzione](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Messaggio di errore: "L'applicazione non è formattata correttamente;" Il file di log contiene "La firma XML non è valida"
 Assicurarsi di aver aggiornato il file manifesto e di aver firmato di nuovo il file. Ripubblicare l'applicazione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando o Mage per firmare nuovamente l'applicazione.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>L'applicazione è stata aggiornata nel server, ma il client non scarica l'aggiornamento
 Questo problema può essere risolto completando una delle attività seguenti:

- Esaminare `deploymentProvider` l'URL nel manifesto della distribuzione. Assicurarsi di aggiornare i bit nella stessa posizione a cui `deploymentProvider` punta .

- Verificare l'intervallo di aggiornamento nel manifesto della distribuzione. Se questo intervallo è impostato su un intervallo periodico, ad esempio una volta ogni sei ore, non eseguirà l'analisi della ricerca di un aggiornamento fino al termine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'intervallo. È possibile modificare il manifesto per cercare un aggiornamento a ogni avvio dell'applicazione. La modifica dell'intervallo di aggiornamento è un'opzione utile durante la fase di sviluppo per verificare l'installazione degli aggiornamenti, ma rallenta l'attivazione dell'applicazione.

- Provare ad avviare nuovamente l'applicazione nel menu Start. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] potrebbe aver rilevato l'aggiornamento in background, ma verrà richiesto di installare i bit alla successiva attivazione.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Durante l'aggiornamento viene visualizzato un errore con la voce di log seguente: "Il riferimento nella distribuzione non corrisponde all'identità definita nel manifesto dell'applicazione"
 Questo errore può verificarsi perché la distribuzione e i manifesti dell'applicazione sono stati modificati manualmente e la descrizione dell'identità di un assembly in un manifesto non è più sincronizzata con l'altra. L'identità di un assembly è costituita da nome, versione, impostazioni cultura e token di chiave pubblica. Esaminare le descrizioni delle identità nei manifesti e correggere eventuali differenze.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>La prima attivazione dal disco locale o da CD-ROM ha esito positivo, ma l'attivazione successiva dal menu Start non riesce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usa l'URL del provider di distribuzione per ricevere gli aggiornamenti per l'applicazione. Verificare che il percorso a cui punta l'URL sia corretto.

#### <a name="error-cannot-start-the-application"></a>Errore: "Impossibile avviare l'applicazione"
 Questo messaggio di errore indica in genere che si è verificato un problema durante l'installazione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nell'archivio. L'applicazione presenta un errore o l'archivio è danneggiato. Il file di log potrebbe indicare dove si è verificato l'errore.

 Eseguire le operazioni seguenti:

- Verificare che l'identità del manifesto della distribuzione, l'identità del manifesto dell'applicazione e l'identità del file EXE dell'applicazione principale siano univoche.

- Verificare che i percorsi dei file non siano più lunghi di 100 caratteri. Se l'applicazione contiene percorsi di file troppo lunghi, è possibile superare le limitazioni del percorso massimo che è possibile archiviare. Provare ad abbreviare i percorsi e reinstallare.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Le impostazioni PrivatePath nel file di configurazione dell'applicazione non vengono rispettate
 Per usare PrivatePath (percorsi di probe Fusion), l'applicazione deve richiedere l'autorizzazione di attendibilità totale. Provare a modificare il manifesto dell'applicazione per richiedere l'attendibilità totale, quindi riprovare.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Durante la disinstallazione viene visualizzato un messaggio che indica che non è stato possibile disinstallare l'applicazione
 Questo messaggio indica in genere che l'applicazione è già stata rimossa o che l'archivio è danneggiato. Dopo aver fatto **clic su OK,** la voce **Aggiungi/Rimuovi** programma verrà rimossa.

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Durante l'installazione, viene visualizzato un messaggio che indica che le dipendenze della piattaforma non sono installate
 Manca un prerequisito nella GLOBALC (Global Assembly Cache) richiesta dall'applicazione per l'esecuzione.

## <a name="publishing-with-visual-studio"></a>Pubblicazione con Visual Studio

#### <a name="publishing-in-visual-studio-fails"></a>La pubblicazione in Visual Studio ha esito negativo
 Assicurarsi di avere il diritto di pubblicare nel server di destinazione. Ad esempio, se si è connessi a un computer server terminal come utente normale, non come amministratore, probabilmente non si avranno i diritti necessari per pubblicare nel server Web locale.

 Se si esegue la pubblicazione con un URL, assicurarsi che nel computer di destinazione sia Estensioni del server di FrontPage abilitata.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Messaggio di errore: Impossibile creare il sito Web ' \<site> '. I componenti per la comunicazione con Estensioni del server di FrontPage non sono installati.
 Assicurarsi che il componente Microsoft Visual Studio web authoring sia installato nel computer da cui si sta pubblicando. Per gli utenti express, questo componente non è installato per impostazione predefinita. Per altre informazioni, vedere [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Messaggio di errore: Impossibile trovare il file 'Microsoft. Windows. Common-Controls, Version=6.0.0.0, Culture=*, PublicKeyToken=6595b64144ccf1df, ProcessorArchitecture= \* , Type=win32'
 Questo messaggio di errore viene visualizzato quando si tenta di pubblicare un'applicazione WPF con gli stili di visualizzazione abilitati. Per risolvere questo problema, vedere [Procedura: Pubblicare un'applicazione WPF con stili di visualizzazione abilitati.](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)

## <a name="using-mage"></a>Uso di Mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Si è provato a firmare con un certificato nell'archivio certificati e una finestra di messaggio vuota ricevuta
 Nella finestra **di** dialogo Firma è necessario:

- Selezionare **Firma con un certificato archiviato** e

- Selezionare un certificato dall'elenco. Il primo certificato non è la selezione predefinita.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Facendo clic sul pulsante "Don't Sign" (Non firmare) viene generata un'eccezione
 Questo problema è un bug noto. Tutti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i manifesti devono essere firmati. È sufficiente selezionare una delle opzioni di firma e quindi fare clic su **OK.**

## <a name="additional-errors"></a>Errori aggiuntivi
 La tabella seguente illustra alcuni messaggi di errore comuni che un utente del computer client può ricevere quando l'utente installa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione. Ogni messaggio di errore viene elencato accanto a una descrizione della causa più probabile dell'errore.

| Messaggio di errore | Descrizione |
| - | - |
| Impossibile avviare l'applicazione. Contattare l'autore dell'applicazione.<br /><br /> Impossibile avviare l'applicazione. Contattare il fornitore dell'applicazione per assistenza. | Si tratta di messaggi di errore generici che si verificano quando non è possibile avviare l'applicazione e non è possibile trovare altri motivi specifici. Spesso ciò significa che l'applicazione è in qualche modo danneggiata o che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'archivio è danneggiato. |
| Impossibile continuare. L'applicazione non è formattata correttamente. Per assistenza, contattare l'autore dell'applicazione.<br /><br /> La convalida dell'applicazione non è riuscita. Impossibile continuare.<br /><br /> Impossibile recuperare i file dell'applicazione. File danneggiati nella distribuzione. | Uno dei file manifesto nella distribuzione non è sintatticamente valido o contiene un hash che non può essere riconciliato con il file corrispondente. Questo errore può anche indicare che il manifesto incorporato in un assembly è danneggiato. Ricompilare la distribuzione e ricompilare l'applicazione oppure trovare e correggere manualmente gli errori nei manifesti. |
| Impossibile recuperare l'applicazione. Errore di autenticazione.<br /><br /> L'installazione dell'applicazione non è riuscita. Impossibile individuare i file delle applicazioni nel server. Per assistenza, contattare l'autore dell'applicazione o l'amministratore. | Impossibile scaricare uno o più file nella distribuzione perché non si dispone dell'autorizzazione per accedervi. Ciò può essere causato da un errore 403 Accesso negato restituito da un server Web, che può verificarsi se uno dei file nella distribuzione termina con un'estensione che fa in modo che il server Web lo tratti come un file protetto. Inoltre, una directory che contiene uno o più file dell'applicazione potrebbe richiedere un nome utente e una password per accedere. |
| Impossibile scaricare l'applicazione. Nell'applicazione mancano i file necessari. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema. | Impossibile trovare uno o più file elencati nel manifesto dell'applicazione nel server. Verificare di aver caricato tutti i file dipendenti della distribuzione e riprovare. |
| Il download dell'applicazione non è riuscito. Controllare la connessione di rete o contattare l'amministratore di sistema o il provider di servizi di rete. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non è in grado di stabilire una connessione di rete al server. Esaminare la disponibilità del server e lo stato della rete. |
| URLDownloadToCacheFile non riuscito con HRESULT ' \<number> '. Si è verificato un errore durante il tentativo di scaricare ' \<file> '. | Se un utente ha impostato l'opzione di sicurezza avanzata "Avvisa se si modifica la modalità protetta e non protetta" nel computer di destinazione della distribuzione e se l'URL di installazione dell'applicazione ClickOnce da installare viene reindirizzato da un sito non sicuro a un sito protetto (o viceversa), l'installazione avrà esito negativo perché l'avviso Internet Explorer la interrompe. Internet Explorer<br /><br /> Per risolvere questo errore, è possibile eseguire una delle attività seguenti:<br /><br /> - Deselezionare l'opzione di sicurezza.<br />- Assicurarsi che l'URL di configurazione non sia reindirizzato in modo da modificare le modalità di sicurezza.<br />- Rimuovere completamente il reindirizzamento e puntare all'URL di configurazione effettivo. |
| Si è verificato un errore durante la scrittura sul disco rigido. Lo spazio disponibile sul disco potrebbe essere insufficiente. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema. | Ciò può indicare spazio su disco insufficiente per l'archiviazione dell'applicazione, ma può anche indicare un errore di I/O più generale quando si tenta di salvare i file dell'applicazione nell'unità. |
| Impossibile avviare l'applicazione. Lo spazio disponibile sul disco non è sufficiente. | Il disco rigido è pieno. Liberare spazio e provare a eseguire di nuovo l'applicazione. |
| Troppe attivazioni distribuite stanno tentando di caricarsi contemporaneamente. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] limita il numero di applicazioni diverse che possono essere avviate contemporaneamente. Si tratta in gran parte di una protezione da tentativi dannosi di istigazione di attacchi Denial of Service contro il servizio locale. Gli utenti che tentano di avviare ripetutamente la stessa applicazione, in rapida successione, finiranno solo con una singola istanza [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. |
| I collegamenti non possono essere attivati in rete. | I collegamenti a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione possono essere avviati solo sul disco rigido locale. Non possono essere avviati aprendo un URL che punta a un file di collegamento in un server remoto. |
| L'applicazione è troppo grande per essere eseguita online con attendibilità parziale. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema. | Un'applicazione eseguita in attendibilità parziale non può essere superiore alla metà delle dimensioni della quota dell'applicazione online, che per impostazione predefinita è di 250 MB. |

## <a name="see-also"></a>Vedi anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Visual Studio risoluzione dei problemi](/troubleshoot/visualstudio/welcome-visual-studio/)