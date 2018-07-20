---
title: Server e problemi di configurazione Client nelle distribuzioni ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65929ec5b58e0629b3f52e31299f670543b3cd08
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154385"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemi di configurazione server e client nelle distribuzioni ClickOnce
Se si usa Internet Information Services (IIS) in Windows Server, e la distribuzione contiene un tipo di file che Windows non riconosce, ad esempio un file di Microsoft Word, IIS non le consentirà nemmeno la trasmissione del file e la distribuzione non riuscirà.  
  
 Inoltre, alcuni server Web e Web software applicativo, ad esempio [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contengono un elenco di file e tipi di file che non è possibile scaricare. Ad esempio, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] impedisce il download di tutte le *Web. config* file. Questi file possono contenere informazioni riservate, ad esempio nomi utente e password.  
  
 Anche se questa restrizione non dovrebbe causare problemi per il download dei core [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file, ad esempio assembly e manifesti, questa restrizione potrebbe impedire il download dei file di dati inclusi come parte di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. In [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], è possibile correggere l'errore rimuovendo il gestore che impedisce il download di questi file da Gestione configurazione di IIS. Vedere la documentazione di server IIS per altri dettagli.  
  
 Alcuni server Web potrebbero bloccare i file con estensioni, ad esempio *. dll*, *config*, e *mdf*. Le applicazioni basate su Windows in genere includono i file con alcune di queste estensioni. Se un utente tenta di eseguire un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che accede a un file bloccato in un server Web, verrà generato un errore. Invece di tutte le estensioni di file, sblocco [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pubblica ogni file dell'applicazione con un *deploy* estensione di file per impostazione predefinita. Pertanto, solo l'amministratore deve configurare il server Web per sbloccare le estensioni di tre file seguenti:  
  
-   *. Application*  
  
-   *manifest*  
  
-   *Deploy* 
  
 Tuttavia, è possibile disabilitare questa opzione deselezionando le **, l'estensione di file ". deploy"** opzione il [Publish Options Dialog Box](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), nel qual caso è necessario configurare il server Web per sbloccare tutte le estensioni di file utilizzato nell'applicazione.  
  
 È necessario configurare *manifest*, *Application*, e *deploy*, ad esempio, se si usa IIS in cui non è stato installato il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o se si è utilizzo di un altro server Web (ad esempio Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>Secure Sockets Layer (SSL) e ClickOnce  
 Oggetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione funziona correttamente tramite SSL, tranne in Internet Explorer genera una richiesta sul certificato SSL. La richiesta può essere generata quando si è verificato un problema con il certificato, ad esempio quando i nomi dei siti non corrispondono o il certificato è scaduto. Per rendere [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funziona solo su una connessione SSL, assicurarsi che il certificato sia aggiornato e che i dati del certificato corrispondano ai dati del sito.  
  
## <a name="clickonce-and-proxy-authentication"></a>Autenticazione proxy e ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornisce il supporto per l'autenticazione di Windows integrata proxy a partire da .NET Framework 3.5. Nessun direttive Machine. config specifico sono necessari. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non fornisce supporto per altri protocolli di autenticazione, ad esempio di base o Digest.  
  
 È anche possibile applicare un hotfix per .NET Framework 2.0 per abilitare questa funzionalità. Per altre informazioni, vedere http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Per altre informazioni, vedere [ \<defaultProxy > (impostazioni di rete)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>Compatibilità del browser Web e ClickOnce  
 Attualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installazioni verranno avviato solo se l'URL del manifesto di distribuzione viene aperta utilizzando Internet Explorer. Una distribuzione il cui URL è avviato da un'altra applicazione, ad esempio Microsoft Office Outlook, verrà avviato correttamente solo se Internet Explorer viene impostato come il Web browser predefinito.  
  
> [!NOTE]
>  Mozilla Firefox è supportato se il provider di distribuzione non è vuoto o è installata l'estensione di Microsoft .NET Framework Assistant. Questa estensione è inclusa in .NET Framework 3.5 SP1. Per il supporto di applicazioni XBAP, il plug-in NPWPF viene attivato quando necessario.  
  
## <a name="activate-clickonce-applications-through-browser-scripting"></a>Attivare le applicazioni ClickOnce tramite la creazione di script di browser  
 Se è stata sviluppata una pagina Web personalizzata che consente di avviare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione usando lo script attivo, è probabile che l'applicazione non verrà avviate in alcuni computer. Internet Explorer contiene un'impostazione denominata **richiesta di conferma automatica per il download di file**, che influisce su questo comportamento. Questa impostazione è disponibile nel **sicurezza** scheda relativo **opzioni** menu che influisce su questo comportamento. Viene chiamato **richiesta di conferma automatica per il file di download**, e viene elencato sotto il **Scarica** categoria. La proprietà è impostata su **abilitare** per impostazione predefinita per le pagine Web intranet e al **disabilitare** per impostazione predefinita per le pagine Web di Internet. Quando questa impostazione è impostata su **disabilitare**, qualsiasi tentativo di attivare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione a livello di codice (ad esempio, assegnando il relativo URL per il `document.location` proprietà) verranno bloccati. In questa circostanza, gli utenti possono avviare applicazioni cloud solo tramite un download avviato dall'utente, ad esempio, facendo clic su un collegamento ipertestuale impostato per l'URL dell'applicazione.  
  
## <a name="additional-server-configuration-issues"></a>Problemi di configurazione del server aggiuntivi  
  
##### <a name="administrator-permissions-required"></a>Autorizzazioni di amministratore necessarie  
 Se esegue la pubblicazione tramite HTTP, è necessario disporre delle autorizzazioni di amministratore nel server di destinazione. IIS richiede questo livello di autorizzazioni. Se non si esegue la pubblicazione tramite HTTP, è necessario scrivere solo delle autorizzazioni nel percorso di destinazione.  
  
##### <a name="server-authentication-issues"></a>Problemi di autenticazione server  
 Durante la pubblicazione in un server remoto con "L'accesso anonimo" disattivata, si riceverà l'avviso seguente:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  È possibile configurare l'autenticazione NTLM (NT challenge-response) modo se il sito richiede le credenziali diverse dalle credenziali predefinite e, nella finestra di dialogo di sicurezza, si fa clic su **OK** quando viene chiesto se si desidera salvare l'oggetto fornito credenziali per le sessioni future. Tuttavia, questa soluzione alternativa non funzioneranno per l'autenticazione di base.  
  
## <a name="use-third-party-web-servers"></a>Usare i server Web di terze parti  
 Se si distribuisce un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione da un server Web diversi da IIS, si verifichi un problema se il server restituisce il tipo di contenuto non corretto per la chiave [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file, ad esempio il manifesto di distribuzione e il manifesto dell'applicazione. Per risolvere questo problema, vedere la Guida del server Web documentazione su come aggiungere nuovi tipi di contenuto al server e assicurarsi che tutti i mapping dei estensione del nome di file elencati nella tabella seguente sono presenti.  
  
|Estensione di file|Tipo di contenuto|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>Le unità mappate e ClickOnce  
 Se si usa Visual Studio per pubblicare un'applicazione ClickOnce, è possibile specificare un'unità mappata come il percorso di installazione. Tuttavia, è possibile modificare l'applicazione ClickOnce per l'installazione da un'unità mappata utilizzando il generatore di manifesti ed Editor (Mage.exe e MageUI.exe). Per altre informazioni, vedere [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) e [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocollo FTP non è supportato per l'installazione di applicazioni  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] supporta l'installazione di applicazioni da qualsiasi server Web HTTP 1.1 o un file server. FTP, il File Transfer Protocol, non è supportato per l'installazione di applicazioni. È possibile utilizzare FTP per la pubblicazione solo le applicazioni. Queste differenze sono riepilogate nella tabella seguente:  
  
|Tipo di URL|Descrizione|  
|--------------|-----------------|  
|FTP: / /|È possibile pubblicare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo.|  
|http://|È possibile installare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo.|  
|https://|È possibile installare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo.|  
|file://|È possibile installare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Firewall  
 Per impostazione predefinita, Windows XP SP2 Abilita il Firewall di Windows. Se si sviluppa l'applicazione in un computer in cui è installato Windows XP, si è ancora in grado di pubblicare ed eseguire [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni dal server locale che esegue IIS. Tuttavia, è possibile accedere il server che esegue IIS da un altro computer, a meno che si apre il Firewall di Windows. Per istruzioni su come la gestione di Windows Firewall, vedere la Guida di Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Abilitare le estensioni del server di FrontPage  
 Estensioni del Server di FrontPage di Microsoft è necessaria per la pubblicazione di applicazioni in un server Web di Windows che usa il protocollo HTTP.  
  
 Per impostazione predefinita, Windows Server non dispone di estensioni del Server di FrontPage installate. Se si desidera utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per pubblicare in un server Web di Windows Server che utilizza il protocollo HTTP con le estensioni del Server di FrontPage, è necessario installare prima le estensioni del Server di FrontPage. È possibile eseguire l'installazione usando lo strumento di amministrazione di gestione Server in Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: Tipi di contenuto bloccata  
 IIS in [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] Blocca tutti i tipi di file, ad eccezione di alcuni tipi di contenuto noti (ad esempio, *htm*, *. HTML*, *txt*e così via). Per abilitare la distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni che utilizzano questo server, è necessario modificare le impostazioni di IIS per consentire il download dei file di tipo *Application*, *manifest*e qualsiasi altro tipo di file personalizzato usato dall'applicazione.  
  
 Se si distribuisce tramite un server IIS, eseguire *inetmgr.exe* e aggiungere nuovi tipi di File per la pagina Web predefinita:  
  
-   Per il *Application* e *manifest* estensioni, il tipo MIME deve essere "application/x-ms-application". Per altri tipi di file, il tipo MIME deve essere "application/octet-stream".  
  
-   Se si crea un tipo MIME con l'estensione "*" e "application/octet-stream" il tipo MIME, consentirà di sbloccare i file di tipo da scaricare. (Tuttavia, bloccate, ad esempio i tipi di file *. aspx* e *asmx* non possono essere scaricati.)  
  
 Per istruzioni specifiche sulla configurazione dei tipi MIME in Windows Server, vedere l'articolo della Microsoft Knowledge Base KB326965, "IIS 6.0 non fornisce tipi MIME sconosciuti" nella [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Mapping dei tipi di contenuto  
 Durante la pubblicazione tramite HTTP, il tipo di contenuto (detto anche tipo MIME) per il *Application* file deve essere "application/x-ms-application". Se hai [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] installato nel server, questo verrà impostato automaticamente automaticamente. Se questo non è installato, quindi è necessario creare un'associazione ai tipi MIME per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vroot applicazione (o l'intero server).  
  
 Se si distribuisce tramite un server IIS, eseguire *inetmgr.* file exe e aggiungere un nuovo tipo di contenuto di "application/x-ms-application" per il *Application* estensione.  
  
## <a name="http-compression-issues"></a>Problemi relativi alla compressione HTTP  
 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è possibile eseguire il download Usa la compressione HTTP, una tecnologia di server Web che usa l'algoritmo GZIP per comprimere un flusso di dati prima dell'invio nel flusso al client. Il client, in questo caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]: decomprime il flusso prima di leggere i file.  
  
 Se si utilizza IIS, è possibile abilitare facilmente la compressione HTTP. Tuttavia, quando si abilita la compressione HTTP, è abilitata solo per determinati tipi di file, vale a dire, file HTML e testo. Per abilitare la compressione per gli assembly (*. dll*), XML (*. XML*), i manifesti della distribuzione (*Application*) e i manifesti dell'applicazione (*manifest*), è necessario aggiungere questi tipi all'elenco dei tipi per IIS per la compressione di file. Fino a quando non si aggiungono i tipi di file per la distribuzione, verranno compressi solo file di testo e HTML.  
  
 Per istruzioni dettagliate per IIS, vedere [come specificare i tipi di documenti aggiuntive per la compressione HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Vedere anche  
 [Risolvere i problemi di distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)