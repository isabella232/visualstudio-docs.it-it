---
title: Risoluzione dei problemi relativi a errori specifici nelle distribuzioni ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 121171dc71746f2c9f91df32b103be8292cce3fa
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153599"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Risolvere errori specifici nelle distribuzioni ClickOnce
Questo articolo elenca i seguenti errori comuni che possono verificarsi quando si distribuisce un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione e viene descritta la procedura per risolvere ogni problema.  
  
## <a name="general-errors"></a>Errori generali  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Quando si tenta di individuare un file dell'applicazione, non accade nulla o XML esegue il rendering di Internet Explorer o viene visualizzata una finestra di dialogo Esegui o Salva con nome  
 Questo errore è probabilmente causato dai tipi di contenuto (noto anche come tipi MIME) non registrati correttamente nel server o nel client.  
  
 In primo luogo, assicurarsi che il server è configurato per associare il *Application* estensione con contenuto di tipo "application/x-ms-application".  
  
 Se il server sia configurato correttamente, verificare che il [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] è installato nel computer. Se il [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] è installato, e viene comunque visualizzato questo problema, provare a disinstallare e reinstallare il [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] per registrare nuovamente il tipo di contenuto nel client.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Viene visualizzato il messaggio di errore, "Impossibile recuperare l'applicazione. I file mancanti nella distribuzione"o"download dell'applicazione è stata interrotta, verificare la presenza di errori di rete e riprovare più tardi."  
 Questo messaggio indica che uno o più file cui fatto riferimento il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti non possono essere scaricati. Il modo più semplice per eseguire il debug di questo errore consiste nel provare a scaricare l'URL che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è non è possibile eseguire il download. Ecco alcune possibili cause:  
  
-   Se il file di log indica "(403) accesso negato" o "(404) non trovata", verificare che il server Web sia configurato in modo che non blocca il download di questo file. Per altre informazioni, vedere [Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Se il *config* file è bloccato dal server, vedere la sezione "errore di Download quando si prova a installare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che dispone di un file con estensione config" più avanti in questo articolo.  
  
-   Determinare se questo errore si è verificato perché la `deploymentProvider` URL nel manifesto di distribuzione fa riferimento a un percorso diverso rispetto all'URL utilizzato per l'attivazione.  
  
-   Assicurarsi che tutti i file siano presenti sul server. il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] log dovrebbero essere il file non trovato.  
  
-   Verificare se sono presenti problemi di connettività di rete; è possibile ricevere questo messaggio se il computer client era offline durante il download.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Errore di download quando si prova a installare un'applicazione ClickOnce che dispone di un file con estensione config  
 Per impostazione predefinita, un'applicazione basata su Visual Basic Windows include un file app. config. Esisterà un problema quando un utente prova a installare da un server Web che usa Windows Server 2003, poiché tale sistema operativo blocca l'installazione di *config* file per motivi di sicurezza. Per abilitare la *config* file per l'installazione, fare clic su **, l'estensione di file ". deploy"** nel **Publish Options** nella finestra di dialogo.  
  
 È anche necessario impostare i tipi di contenuto (noto anche come tipi MIME) in modo appropriato per i file. deploy. Application e manifest. Per altre informazioni, vedere la documentazione del server Web.  
  
 Per altre informazioni, vedere "Windows Server 2003: tipi di contenuti bloccati" nella [problemi di configurazione Server e client nelle distribuzioni ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Messaggio di errore: "Applicazione non è formattata"; File di log contiene "firma XML non valido"  
 Assicurarsi di aver aggiornato il file manifesto e averlo nuovamente firmato. Ripubblicare l'applicazione usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o usare Mage per firmare nuovamente l'applicazione.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>È stato aggiornato l'applicazione nel server, ma il client non scarica l'aggiornamento  
 Questo problema potrebbe essere risolto eseguendo una delle attività seguenti:  
  
-   Esaminare il `deploymentProvider` URL nel manifesto di distribuzione. Assicurarsi che si siano aggiornando i bit nello stesso percorso che `deploymentProvider` punta a.  
  
-   Verificare l'intervallo di aggiornamento nel manifesto di distribuzione. Se questo intervallo è impostato a intervalli periodici, ad esempio una volta ogni sei ore, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non analizza per un aggiornamento prima che sia trascorso questo intervallo. È possibile modificare il manifesto per cercare un aggiornamento ogni volta che viene avviata l'applicazione. Modifica dell'intervallo di aggiornamento è un'opzione utile durante la fase di sviluppo per verificare gli aggiornamenti vengono installati, ma rallenta l'attivazione dell'applicazione.  
  
-   Provare ad avviare nuovamente l'applicazione nel menu Start. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sia stato rilevato l'aggiornamento in background, ma verrà richiesto di installare i bit alla successiva attivazione.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Durante l'aggiornamento viene visualizzato un errore con la voce di log seguente: "il riferimento nella distribuzione non corrisponde all'identità definita nel manifesto dell'applicazione"  
 Questo errore può verificarsi perché è stata modificata manualmente i manifesti dell'applicazione e della distribuzione e hanno causato la descrizione dell'identità di un assembly in un manifesto di perdere la sincronizzazione con le altre. L'identità di un assembly è costituito da nome, versione, impostazioni cultura e token di chiave pubblica. Esaminare le descrizioni di identità nei manifesti e correggere eventuali differenze.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Prima attivazione da CD-ROM o un disco locale viene eseguita correttamente, ma quella successive dal Menu di avvio non riesce.  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizza l'URL del Provider di distribuzione per ricevere gli aggiornamenti dell'applicazione. Verificare che il percorso che fa riferimento l'URL sia corretto.  
  
#### <a name="error-cannot-start-the-application"></a>Errore: "Impossibile avviare l'applicazione"  
 Questo messaggio di errore indica in genere che vi sia un problema durante l'installazione dell'applicazione nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archiviare. L'applicazione presenta un errore o l'archivio è danneggiato. Il file di log potrebbe indicare la posizione dell'errore.  
  
 È consigliabile eseguire le operazioni seguenti:  
  
-   Verificare che l'identità del manifesto della distribuzione, il manifesto dell'applicazione e identità dell'applicazione principale. EXE siano tutti univoci.  
  
-   Verificare che i percorsi dei file non sono più di 100 caratteri. Se l'applicazione contiene i percorsi di file che sono troppo lunghi, si possono superare le limitazioni relative al percorso massimo che è possibile archiviare. Provare ad abbreviare i percorsi e reinstallare.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Attributo PrivatePath impostazioni nel file di configurazione dell'applicazione non vengono rispettate  
 Per usare PrivatePath (percorsi di sondaggio di Fusion), l'applicazione deve richiedere l'autorizzazione di attendibilità totale. Provare a modificare il manifesto dell'applicazione per richiedere l'attendibilità totale e quindi riprovare.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Durante la disinstallazione viene visualizzato un messaggio per segnalare che "Non è stato possibile disinstallare l'applicazione"  
 Questo messaggio indica in genere che l'applicazione è già stata rimossa o è danneggiato nell'archivio. Dopo aver fatto clic **OK**, il **programma di installazione** voce verrà rimossa.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Durante l'installazione, viene visualizzato un messaggio indicante che le dipendenze di piattaforma non sono installate  
 Manca un prerequisito nella GAC (cache di assembly globale) necessarie per eseguire l'applicazione.  
  
## <a name="publishing-with-visual-studio"></a>Pubblicazione con Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>La pubblicazione in Visual Studio non riesce  
 Assicurarsi di avere il diritto di pubblicare il server di destinazione. Ad esempio, se è connessi a un computer di terminal server come utente normale, non come amministratore, è probabile che non avrà i diritti necessari per la pubblicazione nel server Web locale.  
  
 Se esegue la pubblicazione con un URL, verificare che il computer di destinazione abbia estensioni del Server abilitata.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Messaggio di errore: Impossibile creare il sito Web '\<sito >'. Non sono installati i componenti per la comunicazione con le estensioni del Server di FrontPage.  
 Assicurarsi di disporre di Microsoft Visual Studio Authoring componente Web installato nel computer in cui si esegue la pubblicazione da. Per gli utenti di Express, questo componente non è installato per impostazione predefinita. Per altre informazioni, vedere [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Messaggio di errore: Impossibile trovare il file ' Common-controlli, versione = 6.0.0.0, Culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, tipo = win32'  
 Questo messaggio di errore viene visualizzato quando si prova a pubblicare un'applicazione WPF con gli stili visuali abilitati. Per risolvere questo problema, vedere [procedura: pubblicare un'applicazione WPF con abilitato gli stili Visual](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Utilizzo di Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Si è tentato di accedere con un certificato nell'archivio dei certificati e una casella ricevuto alcun messaggio  
 Nel **firma** finestra di dialogo, è necessario:  
  
-   Selezionare **firma con un certificato archiviato**, e  
  
-   Selezionare un certificato dall'elenco. il primo certificato non è selezionata l'impostazione predefinita.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Fare clic sul pulsante "Sign non" genera un'eccezione  
 Questo problema è un bug noto. Tutti i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i manifesti sono deve essere firmato. Selezionare una delle opzioni di firma e quindi fare clic su **OK**.  
  
## <a name="additional-errors"></a>Sono presenti altri errori  
 La tabella seguente illustra alcuni messaggi di errore comuni che un utente di computer client che venga visualizzato quando l'utente installa un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Ogni messaggio di errore è elencato accanto a una descrizione della causa più probabile dell'errore.  
  
|Messaggio di errore|Descrizione|  
|-------------------|-----------------|  
|Impossibile avviare l'applicazione. Contattare l'autore dell'applicazione.<br /><br /> Impossibile avviare l'applicazione. Per assistenza, contattare il fornitore dell'applicazione.|Si tratta di messaggi di errore generico che si verificano quando non è possibile avviare l'applicazione e non sono disponibili altri motivi specifici. Spesso questo significa che l'applicazione è danneggiata in qualche modo, o che il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'archivio è danneggiato.|  
|Non può continuare. L'applicazione non è formattata. Per assistenza, contattare l'editore dell'applicazione.<br /><br /> Convalida dell'applicazione non è riuscita. Impossibile continuare.<br /><br /> Impossibile recuperare i file dell'applicazione. File danneggiati nella distribuzione.|Uno dei file manifesto della distribuzione è sintatticamente non valido o contiene un hash che non può essere coincida con il file corrispondente. Questo errore potrebbe indicare anche che il manifesto incorporato all'interno di un assembly è danneggiato. Creare nuovamente la distribuzione e ricompilare l'applicazione, o trovare e correggere gli errori manualmente nei manifesti.|  
|Impossibile recuperare l'applicazione. Errore di autenticazione.<br /><br /> Installazione dell'applicazione non è riuscita. Impossibile individuare il file delle applicazioni nel server. Per assistenza, contattare l'autore dell'applicazione o l'amministratore.|Uno o più file nella distribuzione non possono essere scaricati perché non si dispone delle autorizzazioni per accedervi. Ciò può dipendere da un errore 403 accesso negato viene restituito da un server Web, che può verificarsi se uno dei file nella distribuzione termina con un'estensione che consente al server Web di considerarlo come un file protetto. Inoltre, una directory che contiene uno o più file dell'applicazione richieda un nome utente e una password per poter accedere.|  
|Non è possibile scaricare l'applicazione. L'applicazione mancante i file necessari. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema.|Impossibile trovare uno o più file elencati nel manifesto dell'applicazione nel server. Verificare che è stato caricato tutti i file di distribuzione dipendenti e ripetere l'operazione.|  
|Download dell'applicazione non è riuscita. Verificare la connessione di rete o contattare l'amministratore di sistema o un provider di servizi di rete.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non è possibile stabilire una connessione di rete al server. Esaminare la disponibilità del server e lo stato della rete.|  
|URLDownloadToCacheFile non riuscita con HRESULT '\<numero >'. Si è verificato un errore durante il download di '\<file >'.|Se un utente ha impostato opzione sicurezza avanzata di Internet Explorer "Avvisa se si passa tra sicura e modalità non protetta" nel computer di destinazione di distribuzione e l'URL di installazione dell'applicazione ClickOnce in corso l'installazione viene reindirizzato dal non protetta a un sito protetto (o viceversa), l'installazione avrà esito negativo poiché interrotta l'avviso di Internet Explorer.<br /><br /> Per risolvere questo errore, è possibile eseguire una delle seguenti attività:<br /><br /> -Deselezionare l'opzione di sicurezza.<br />-Verificare che l'URL di installazione non viene reindirizzata in modo tale che modifica le modalità di sicurezza.<br />-Rimuovere completamente il reindirizzamento e scegliere l'URL di installazione effettivo.|  
|Si è verificato un errore di scrittura sul disco rigido. Potrebbero esserci spazio insufficiente disponibile su disco. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema.|Questo può indicare lo spazio su disco insufficiente per l'archiviazione dell'applicazione, ma si sia verificato un errore dei / o più generale quando si tenta di salvare i file dell'applicazione nell'unità.|  
|Impossibile avviare l'applicazione. Non c'è spazio sufficiente disponibile sul disco.|Il disco rigido è pieno. Cancellare lo spazio e provare a eseguire nuovamente l'applicazione.|  
|Troppe applicazioni distribuite tenta di caricare in una sola volta.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Limita il numero delle diverse applicazioni che possono essere avviati nello stesso momento. Si tratta fondamentalmente per proteggersi da tentativi di provocare attacchi denial of service contro locale [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ; gli utenti che tenta di avviare più volte, la stessa applicazione in rapida successione, solo finirà con una singola istanza del servizio di applicazione.|  
|Tasti di scelta rapida non può essere attivati in rete.|Tasti di scelta rapida per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione può essere avviata solo sul disco rigido locale. È Impossibile avviare aprendo un URL che punta a un file di scelta rapida in un server remoto.|  
|L'applicazione è troppo grande per essere eseguita in linea in attendibilità parziale. Per assistenza, contattare il fornitore dell'applicazione o l'amministratore di sistema.|Un'applicazione che viene eseguita in attendibilità parziale non può essere maggiore della metà delle dimensioni della quota online delle applicazioni, che per impostazione predefinita è pari a 250 MB.|  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione e protezione ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Risolvere i problemi di distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)