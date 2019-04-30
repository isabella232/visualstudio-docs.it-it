---
title: Server e problemi di configurazione Client nelle distribuzioni ClickOnce | Microsoft Docs
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
ms.openlocfilehash: 90772785297b84a12cc98d6ce21a2cd2e65743f9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444977"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si usa Internet Information Services (IIS) in Windows Server, e la distribuzione contiene un tipo di file che Windows non riconosce, ad esempio un file di Microsoft Word, IIS non le consentirà nemmeno la trasmissione del file e la distribuzione non riuscirà.  
  
 Inoltre, alcuni server Web e Web software applicativo, ad esempio [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], contengono un elenco di file e tipi di file che non è possibile scaricare. Ad esempio, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] impedisce il download di tutti i file Web. config. Questi file possono contenere informazioni riservate, ad esempio nomi utente e password.  
  
 Anche se questa restrizione non dovrebbe causare problemi per il download dei core [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] file, ad esempio assembly e manifesti, questa restrizione potrebbe impedire il download dei file di dati inclusi come parte di [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione. In [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], è possibile correggere l'errore rimuovendo il gestore che impedisce il download di questi file da Gestione configurazione di IIS. Vedere la documentazione di server IIS per altri dettagli.  
  
 Alcuni server Web potrebbero bloccare i file con estensioni, ad esempio con estensione dll. config e file con estensione mdf. Le applicazioni basate su Windows in genere includono i file con alcune di queste estensioni. Se un utente tenta di eseguire un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione che accede a un file bloccato in un server Web, verrà generato un errore. Anziché lo sblocco di tutte le estensioni di file, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pubblica ogni file dell'applicazione con un'estensione di file ". deploy" per impostazione predefinita. Pertanto, solo l'amministratore deve configurare il server Web per sbloccare le estensioni di tre file seguenti:  
  
- .application  
  
- .manifest  
  
- .deploy  
  
  Tuttavia, è possibile disabilitare questa opzione deselezionando le **, l'estensione di file ". deploy"** opzione il [Publish Options Dialog Box](http://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), nel qual caso è necessario configurare il server Web per sbloccare tutte le estensioni di file utilizzato nell'applicazione.  
  
  È necessario configurare manifest, Application e deploy, ad esempio, se si usa IIS in cui non è stato installato il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], o se si usa un altro server Web (ad esempio Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>Secure Sockets Layer (SSL) e ClickOnce  
 Oggetto [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione funziona correttamente tramite SSL, tranne in Internet Explorer genera una richiesta sul certificato SSL. La richiesta può essere generata quando si è verificato un problema con il certificato, ad esempio quando i nomi dei siti non corrispondono o il certificato è scaduto. Per rendere [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] funziona solo su una connessione SSL, assicurarsi che il certificato sia aggiornato e che i dati del certificato corrispondano ai dati del sito.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce e l'autenticazione Proxy  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fornisce il supporto per l'autenticazione di Windows integrata proxy a partire da .NET Framework 3.5. Nessun direttive Machine. config specifico sono necessari. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] non fornisce supporto per altri protocolli di autenticazione, ad esempio di base o Digest.  
  
 È anche possibile applicare un hotfix per .NET Framework 2.0 per abilitare questa funzionalità. Per altre informazioni, vedere http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Per altre informazioni, vedere [ \<defaultProxy > (impostazioni di rete)](http://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>Compatibilità del Browser Web e ClickOnce  
 Attualmente, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installazioni verranno avviato solo se l'URL del manifesto di distribuzione viene aperta utilizzando Internet Explorer. Una distribuzione il cui URL è avviato da un'altra applicazione, ad esempio Microsoft Office Outlook, verrà avviato correttamente solo se Internet Explorer viene impostato come il Web browser predefinito.  
  
> [!NOTE]
> Mozilla Firefox è supportato se il provider di distribuzione non è vuoto o è installata l'estensione di Microsoft .NET Framework Assistant. Questa estensione è inclusa in .NET Framework 3.5 SP1. Per il supporto di applicazioni XBAP, il plug-in NPWPF viene attivato quando necessario.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Attivazione di applicazioni ClickOnce tramite la creazione di script di Browser  
 Se è stata sviluppata una pagina Web personalizzata che consente di avviare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione usando lo script attivo, è probabile che l'applicazione non verrà avviate in alcuni computer. Internet Explorer contiene un'impostazione denominata **richiesta di conferma automatica per il download di file**, che influisce su questo comportamento. Questa impostazione è disponibile nel **sicurezza** scheda relativo **opzioni** menu che influisce su questo comportamento. Viene chiamato **richiesta di conferma automatica per il file di download**, e viene elencato sotto il **Scarica** categoria. La proprietà è impostata su **abilitare** per impostazione predefinita per le pagine Web intranet e al **disabilitare** per impostazione predefinita per le pagine Web di Internet. Quando questa impostazione è impostata su **disabilitare**, qualsiasi tentativo di attivare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione a livello di codice (ad esempio, assegnando il relativo URL per il `document.location` proprietà) verranno bloccati. In questa circostanza, gli utenti possono avviare applicazioni cloud solo tramite un download avviato dall'utente, ad esempio, facendo clic su un collegamento ipertestuale impostato per l'URL dell'applicazione.  
  
## <a name="additional-server-configuration-issues"></a>Problemi di configurazione del Server aggiuntivi  
  
##### <a name="administrator-permissions-required"></a>Autorizzazioni di amministratore necessarie  
 Se esegue la pubblicazione tramite HTTP, è necessario disporre delle autorizzazioni di amministratore nel server di destinazione. IIS richiede questo livello di autorizzazioni. Se non si esegue la pubblicazione tramite HTTP, è necessario scrivere solo delle autorizzazioni nel percorso di destinazione.  
  
##### <a name="server-authentication-issues"></a>Problemi di autenticazione server  
 Durante la pubblicazione in un server remoto con "L'accesso anonimo" disattivata, si riceverà l'avviso seguente:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> È possibile configurare l'autenticazione NTLM (NT challenge-response) modo se il sito richiede le credenziali diverse dalle credenziali predefinite e, nella finestra di dialogo di sicurezza, si fa clic su **OK** quando viene chiesto se si desidera salvare l'oggetto fornito credenziali per le sessioni future. Tuttavia, questa soluzione alternativa non funzioneranno per l'autenticazione di base.  
  
## <a name="using-third-party-web-servers"></a>Utilizzo di server Web di terze parti  
 Se si distribuisce un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione da un server Web diversi da IIS, si verifichi un problema se il server restituisce il tipo di contenuto non corretto per la chiave [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] file, ad esempio il manifesto di distribuzione e il manifesto dell'applicazione. Per risolvere questo problema, vedere la Guida del server Web documentazione su come aggiungere nuovi tipi di contenuto al server e assicurarsi che tutti i mapping dei estensione del nome di file elencati nella tabella seguente sono presenti.  
  
|Estensione del file|Tipo di contenuto|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>Le unità mappate e ClickOnce  
 Se si usa Visual Studio per pubblicare un'applicazione ClickOnce, è possibile specificare un'unità mappata come il percorso di installazione. Tuttavia, è possibile modificare l'applicazione ClickOnce per l'installazione da un'unità mappata utilizzando il generatore di manifesti ed Editor (Mage.exe e MageUI.exe). Per altre informazioni, vedere [Mage.exe (Manifest Generation and Editing Tool)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) e [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Il protocollo FTP non è supportata per l'installazione di applicazioni  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] supporta l'installazione di applicazioni da qualsiasi server Web HTTP 1.1 o un file server. FTP, il File Transfer Protocol, non è supportato per l'installazione di applicazioni. È possibile utilizzare FTP per la pubblicazione solo le applicazioni. Queste differenze sono riepilogate nella tabella seguente:  
  
|Tipo di URL|Descrizione|  
|--------------|-----------------|  
|ftp://|È possibile pubblicare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione utilizzando questo protocollo.|  
|http://|È possibile installare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione utilizzando questo protocollo.|  
|https://|È possibile installare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione utilizzando questo protocollo.|  
|file://|È possibile installare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione utilizzando questo protocollo.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Firewall  
 Per impostazione predefinita, Windows XP SP2 Abilita il Firewall di Windows. Se si sviluppa l'applicazione in un computer in cui è installato Windows XP, si è ancora in grado di pubblicare ed eseguire [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni dal server locale che esegue IIS. Tuttavia, è possibile accedere il server che esegue IIS da un altro computer, a meno che si apre il Firewall di Windows. Per istruzioni su come la gestione di Windows Firewall, vedere la Guida di Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Abilitare le estensioni del server di FrontPage  
 Estensioni del Server di FrontPage di Microsoft è necessaria per la pubblicazione di applicazioni in un server Web di Windows che usa il protocollo HTTP.  
  
 Per impostazione predefinita, Windows Server non dispone di estensioni del Server di FrontPage installate. Se si desidera utilizzare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per pubblicare in un server Web di Windows Server che utilizza il protocollo HTTP con le estensioni del Server di FrontPage, è necessario installare prima le estensioni del Server di FrontPage. È possibile eseguire l'installazione usando lo strumento di amministrazione di gestione Server in Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: Tipi di contenuto bloccato  
 IIS in [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] Blocca tutti i tipi di file, ad eccezione di determinati tipi di contenuto noti (ad esempio,. htm, HTML, file con estensione txt e così via). Per abilitare la distribuzione di [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni che utilizzano questo server, è necessario modificare le impostazioni di IIS per consentire il download dei file di estensione Application. manifest e altri tipi di file personalizzati usati dall'applicazione.  
  
 Se si distribuisce tramite un server IIS, eseguire inetmgr.exe e aggiungere nuovi tipi di File per la pagina Web predefinita:  
  
- Per le estensioni Application e manifest, il tipo MIME deve essere "application/x-ms-application". Per altri tipi di file, il tipo MIME deve essere "application/octet-stream".  
  
- Se si crea un tipo MIME con l'estensione "*" e "application/octet-stream" il tipo MIME, consentirà di sbloccare i file di tipo da scaricare. (Bloccata, tuttavia, tipi, ad esempio. aspx e. asmx non è possibile scaricare file).  
  
  Per istruzioni specifiche sulla configurazione dei tipi MIME in Windows Server, fare riferimento all'articolo della Microsoft Knowledge Base KB326965, "IIS 6.0 non non servire MIME tipi sconosciuti" nella [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Mapping dei tipi di contenuto  
 Quando si pubblica su HTTP, il tipo di contenuto (detto anche tipo MIME) per il file con estensione Application deve essere "application/x-ms-application". Se hai [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] installato nel server, questo verrà impostato automaticamente automaticamente. Se questo non è installato, quindi è necessario creare un'associazione ai tipi MIME per il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vroot applicazione (o l'intero server).  
  
 Se si distribuisce tramite un server IIS, eseguire inetmgr.exe e aggiungere un nuovo tipo di contenuto di "application/x-ms-application" per l'estensione Application.  
  
## <a name="http-compression-issues"></a>Problemi relativi alla compressione HTTP  
 Con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], è possibile eseguire il download Usa la compressione HTTP, una tecnologia di server Web che usa l'algoritmo GZIP per comprimere un flusso di dati prima dell'invio nel flusso al client. Il client, in questo caso, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]: decomprime il flusso prima di leggere i file.  
  
 Se si utilizza IIS, è possibile abilitare facilmente la compressione HTTP. Tuttavia, quando si abilita la compressione HTTP, è abilitata solo per determinati tipi di file, vale a dire, file HTML e testo. Per abilitare la compressione per un assembly (DLL), XML (con estensione XML), i manifesti della distribuzione (Application) e i manifesti dell'applicazione (con estensione manifest), è necessario aggiungere questi tipi di file all'elenco di tipi per IIS da comprimere. Fino a quando non si aggiungono i tipi di file per la distribuzione, verranno compressi solo file di testo e HTML.  
  
 Per istruzioni dettagliate per IIS, vedere [come specificare i tipi di documenti aggiuntive per la compressione HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi di distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)
