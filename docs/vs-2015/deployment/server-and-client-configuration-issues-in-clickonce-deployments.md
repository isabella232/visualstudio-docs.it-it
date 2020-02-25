---
title: Problemi di configurazione del server e del client nelle distribuzioni ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8e5054b4da0122c40c3ad62cfebcace973f7b20
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558016"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si usa Internet Information Services (IIS) in Windows Server e la distribuzione contiene un tipo di file non riconosciuto da Windows, ad esempio un file di Microsoft Word, IIS rifiuterà di trasmettere tale file e la distribuzione avrà esito negativo.  
  
 Inoltre, alcuni server Web e il software dell'applicazione Web, ad esempio [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], contengono un elenco di file e tipi di file che non è possibile scaricare. Ad esempio, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] impedisce il download di tutti i file Web. config. Questi file possono contenere informazioni riservate, ad esempio nomi utente e password.  
  
 Sebbene questa restrizione non causi problemi per il download di file di [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] principali, ad esempio manifesti e assembly, questa restrizione potrebbe impedire il download dei file di dati inclusi come parte dell'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. In [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], è possibile risolvere l'errore rimuovendo il gestore che impedisce il download di tali file da Gestione configurazione IIS. Per ulteriori informazioni, vedere la documentazione del server IIS.  
  
 Alcuni server Web potrebbero bloccare i file con estensioni, ad esempio dll, config e MDF. Le applicazioni basate su Windows in genere includono file con alcune di queste estensioni. Se un utente tenta di eseguire un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] che accede a un file bloccato in un server Web, viene generato un errore. Anziché sbloccare tutte le estensioni di file, per impostazione predefinita [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pubblica ogni file dell'applicazione con estensione di file ". deploy". Pertanto, l'amministratore deve solo configurare il server Web per sbloccare le tre estensioni di file seguenti:  
  
- .application  
  
- manifest  
  
- .deploy  
  
  Tuttavia, è possibile disabilitare questa opzione deselezionando l'opzione **"Distribuisci" estensione di file** nella finestra di [dialogo Opzioni di pubblicazione](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592). in questo caso, è necessario configurare il server Web per sbloccare tutte le estensioni di file utilizzate nell'applicazione.  
  
  È necessario configurare. manifest,. Application e. deploy, ad esempio se si usa IIS in cui non è stato installato il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]o se si usa un altro server Web (ad esempio, Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce e Secure Sockets Layer (SSL)  
 Un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] funzionerà correttamente rispetto a SSL, tranne quando Internet Explorer genera una richiesta sul certificato SSL. La richiesta può essere generata quando si verifica un problema con il certificato, ad esempio quando i nomi di sito non corrispondono o il certificato è scaduto. Per fare in modo che [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] funzioni su una connessione SSL, verificare che il certificato sia aggiornato e che i dati del certificato corrispondano ai dati del sito.  
  
## <a name="clickonce-and-proxy-authentication"></a>Autenticazione ClickOnce e proxy  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fornisce il supporto per l'autenticazione proxy integrata di Windows a partire da .NET Framework 3,5. Non sono necessarie direttive machine. config specifiche. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] non fornisce supporto per altri protocolli di autenticazione, ad esempio di base o digest.  
  
 Per abilitare questa funzionalità, è anche possibile applicare un hotfix a .NET Framework 2,0. Per ulteriori informazioni, vedere [correzione: messaggio di errore quando si tenta di installare un'applicazione ClickOnce creata nel .NET Framework 2,0 in un computer client configurato per l'utilizzo di un server proxy: "autenticazione proxy obbligatoria"](https://support.microsoft.com/en-in/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that). 
  
 Per ulteriori informazioni, vedere [\<elemento > defaultProxy (impostazioni di rete)](https://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>Compatibilità tra ClickOnce e browser Web  
 Attualmente, le installazioni di [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vengono avviate solo se l'URL del manifesto di distribuzione viene aperto utilizzando Internet Explorer. Una distribuzione il cui URL viene avviato da un'altra applicazione, ad esempio Microsoft Office Outlook, verrà avviata correttamente solo se Internet Explorer è impostato come Web browser predefinito.  
  
> [!NOTE]
> Mozilla Firefox è supportato se il provider di distribuzione non è vuoto o se è installata l'estensione Microsoft .NET Framework Assistant. Questa estensione è assemblata con .NET Framework 3,5 SP1. Per il supporto di XBAP, il plug-in NPWPF viene attivato quando necessario.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Attivazione di applicazioni ClickOnce tramite scripting del browser  
 Se è stata sviluppata una pagina Web personalizzata che avvia un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] utilizzando lo scripting attivo, è possibile che l'applicazione non venga avviata in alcuni computer. Internet Explorer contiene un'impostazione denominata **richiesta automatica di download di file**, che influiscono su questo comportamento. Questa impostazione è disponibile nella scheda **sicurezza** del menu **Opzioni** che influiscono su questo comportamento. Viene chiamato **prompt automatico per i download di file**ed è elencato sotto la categoria **Downloads** . Per impostazione predefinita, la proprietà è impostata su **Abilita** per le pagine Web Intranet e per la **disabilitazione** per le pagine Web Internet. Quando questa impostazione è impostata su **Disabilita**, qualsiasi tentativo di attivare un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a livello di codice (ad esempio, assegnando il relativo URL alla proprietà `document.location`) verrà bloccato. In questa circostanza, gli utenti possono avviare le applicazioni solo tramite un download avviato dall'utente, ad esempio facendo clic su un collegamento ipertestuale impostato sull'URL dell'applicazione.  
  
## <a name="additional-server-configuration-issues"></a>Problemi di configurazione del server aggiuntivi  
  
##### <a name="administrator-permissions-required"></a>Autorizzazioni di amministratore obbligatorie  
 È necessario disporre delle autorizzazioni di amministratore per il server di destinazione se si sta pubblicando con HTTP. IIS richiede questo livello di autorizzazioni. Se non si esegue la pubblicazione tramite HTTP, è necessaria solo l'autorizzazione di scrittura per il percorso di destinazione.  
  
##### <a name="server-authentication-issues"></a>Problemi di autenticazione server  
 Quando si esegue la pubblicazione in un server remoto in cui è disattivato l'accesso anonimo, verrà visualizzato l'avviso seguente:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> È possibile eseguire l'autenticazione NTLM (NT Challenge-Response) se il sito richiede credenziali diverse da quelle predefinite e, nella finestra di dialogo sicurezza, si fa clic su **OK** quando viene richiesto se si desidera salvare le credenziali fornite per le sessioni future. Questa soluzione alternativa non funzionerà tuttavia per l'autenticazione di base.  
  
## <a name="using-third-party-web-servers"></a>Uso di server Web di terze parti  
 Se si distribuisce un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] da un server Web diverso da IIS, potrebbe verificarsi un problema se il server restituisce il tipo di contenuto non corretto per i file [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] chiave, ad esempio il manifesto di distribuzione e il manifesto dell'applicazione. Per risolvere questo problema, vedere la documentazione della guida del server Web per informazioni su come aggiungere nuovi tipi di contenuto al server e assicurarsi che tutti i mapping dell'estensione di file elencati nella tabella seguente siano disponibili.  
  
|Estensione del nome di file|Tipo di contenuto|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce e unità mappate  
 Se si usa Visual Studio per pubblicare un'applicazione ClickOnce, non è possibile specificare un'unità mappata come percorso di installazione. Tuttavia, è possibile modificare l'applicazione ClickOnce per l'installazione da un'unità mappata usando il generatore di manifesti e l'editor (Mage. exe e MageUI. exe). Per ulteriori informazioni, vedere [Mage. exe (strumento per la generazione e la modifica di manifesti)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) e [MageUI. exe (strumento per la generazione e la modifica di manifesti, client grafico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocollo FTP non supportato per l'installazione di applicazioni  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] supporta l'installazione di applicazioni da qualsiasi server Web HTTP 1,1 o file server. FTP, il File Transfer Protocol, non è supportato per l'installazione di applicazioni. È possibile utilizzare FTP solo per pubblicare le applicazioni. Nella tabella seguente sono riepilogate queste differenze:  
  
|Tipo di URL|Descrizione|  
|--------------|-----------------|  
|ftp://|È possibile pubblicare un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usando questo protocollo.|  
|http://|È possibile installare un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usando questo protocollo.|  
|https://|È possibile installare un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usando questo protocollo.|  
|file://|È possibile installare un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usando questo protocollo.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Firewall  
 Per impostazione predefinita, Windows XP SP2 Abilita il Windows Firewall. Se si sviluppa l'applicazione in un computer in cui è installato Windows XP, è ancora possibile pubblicare ed eseguire [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni dal server locale che esegue IIS. Tuttavia, non è possibile accedere a tale server che esegue IIS da un altro computer, a meno che non si apra il Windows Firewall. Per istruzioni sulla gestione del Windows Firewall, vedere la Guida di Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: abilitare le estensioni del server di FrontPage  
 Estensioni del server di FrontPage di Microsoft è necessario per la pubblicazione di applicazioni in un server Web Windows che usa HTTP.  
  
 Per impostazione predefinita, in Windows Server non è installato Estensioni del server di FrontPage. Se si desidera utilizzare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per pubblicare in un server Web Windows Server che utilizza HTTP con Estensioni del server di FrontPage, è necessario installare prima Estensioni del server di FrontPage. È possibile eseguire l'installazione utilizzando lo strumento di amministrazione del server in Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: tipi di contenuto bloccati  
 IIS su [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] blocca tutti i tipi di file, ad eccezione di determinati tipi di contenuto noti, ad esempio htm, HTML, txt e così via. Per abilitare la distribuzione di applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usando questo server, è necessario modificare le impostazioni di IIS per consentire il download di file di tipo. Application,. manifest e di qualsiasi altro tipo di file personalizzato usato dall'applicazione.  
  
 Se si esegue la distribuzione tramite un server IIS, eseguire inetmgr. exe e aggiungere nuovi tipi di file per la pagina Web predefinita:  
  
- Per le estensioni. Application e. manifest, il tipo MIME deve essere "Application/x-ms-application". Per gli altri tipi di file, il tipo MIME deve essere "Application/ottetto-Stream".  
  
- Se si crea un tipo MIME con estensione "*" e il tipo MIME "Application/ottetto-Stream", sarà possibile scaricare i file del tipo di file non bloccato. Tuttavia, non è possibile scaricare i tipi di file bloccati, ad esempio. aspx e. asmx.  
  
  Per istruzioni specifiche sulla configurazione dei tipi MIME in Windows Server, vedere [come aggiungere un tipo MIME a un sito Web o a un'applicazione](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).  
  
## <a name="content-type-mappings"></a>Mapping dei tipi di contenuto  
 Quando si pubblica su HTTP, il tipo di contenuto (noto anche come tipo MIME) per il file. Application deve essere "Application/x-ms-application". Se nel server è installato [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], questo verrà impostato automaticamente. Se questo non è installato, è necessario creare un'associazione di tipo MIME per il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione vroot (o intero server).  
  
 Se si esegue la distribuzione tramite un server IIS, eseguire inetmgr. exe e aggiungere un nuovo tipo di contenuto "Application/x-ms-application" per l'estensione. Application.  
  
## <a name="http-compression-issues"></a>Problemi di compressione HTTP  
 Con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], è possibile eseguire download che usano la compressione HTTP, una tecnologia server Web che usa l'algoritmo GZIP per comprimere un flusso di dati prima di inviare il flusso al client. Il client, in questo caso [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], decomprime il flusso prima di leggere i file.  
  
 Se si utilizza IIS, è possibile abilitare facilmente la compressione HTTP. Tuttavia, quando si Abilita la compressione HTTP, questa viene abilitata solo per determinati tipi di file, ovvero file HTML e di testo. Per abilitare la compressione per gli assembly (con estensione dll), i file XML (XML), i manifesti della distribuzione (. Application) e i manifesti dell'applicazione (. manifest), è necessario aggiungere questi tipi di file all'elenco dei tipi per comprimere IIS. Fino a quando non si aggiungono i tipi di file alla distribuzione, verranno compressi solo i file di testo e HTML.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)
