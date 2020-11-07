---
title: Problemi di configurazione del server/client (ClickOnce)
description: Informazioni sui problemi di configurazione di server e client che possono influire sulla distribuzione dell'applicazione ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e5cebadb35ae5d4cddcd0d4bfb4763979937318
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350551"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce
Se si usa Internet Information Services (IIS) in Windows Server e la distribuzione contiene un tipo di file non riconosciuto da Windows, ad esempio un file di Microsoft Word, IIS rifiuterà di trasmettere tale file e la distribuzione avrà esito negativo.

 Inoltre, alcuni server Web e il software dell'applicazione Web, ad esempio [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , contengono un elenco di file e tipi di file che non è possibile scaricare. Ad esempio, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] impedisce il download di tutti i file di *Web.config* . Questi file possono contenere informazioni riservate, ad esempio nomi utente e password.

 Sebbene questa restrizione non causi problemi per il download di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file principali, ad esempio manifesti e assembly, questa restrizione potrebbe impedire il download dei file di dati inclusi nell' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. In [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è possibile risolvere questo errore rimuovendo il gestore che impedisce il download di tali file da Gestione configurazione IIS. Per ulteriori informazioni, vedere la documentazione del server IIS.

 Alcuni server Web potrebbero bloccare i file con estensioni, ad esempio *dll* , *config* e *MDF*. Le applicazioni basate su Windows in genere includono file con alcune di queste estensioni. Se un utente tenta di eseguire un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che accede a un file bloccato in un server Web, viene generato un errore. Anziché sbloccare tutte le estensioni di file, pubblica tutti i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file dell'applicazione con un'estensione di file *. deploy* per impostazione predefinita. Pertanto, l'amministratore deve solo configurare il server Web per sbloccare le tre estensioni di file seguenti:

- *. applicazione*

- *. manifest*

- *. Distribuisci*

  Tuttavia, è possibile disabilitare questa opzione deselezionando l'opzione **"Distribuisci" estensione di file** nella finestra di [dialogo Opzioni di pubblicazione](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)). in questo caso, è necessario configurare il server Web per sbloccare tutte le estensioni di file utilizzate nell'applicazione.

  È necessario configurare *. manifest* , *. Application* e *. deploy* , ad esempio se si usa IIS in cui non è stato installato il .NET Framework o se si usa un altro server Web (ad esempio, Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce e Secure Sockets Layer (SSL)
 Un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione funzionerà correttamente rispetto a SSL, tranne quando Internet Explorer genera una richiesta sul certificato SSL. La richiesta può essere generata quando si verifica un problema con il certificato, ad esempio quando i nomi di sito non corrispondono o il certificato è scaduto. Per eseguire il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lavoro su una connessione SSL, verificare che il certificato sia aggiornato e che i dati del certificato corrispondano ai dati del sito.

## <a name="clickonce-and-proxy-authentication"></a>Autenticazione ClickOnce e proxy
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornisce supporto per l'autenticazione proxy integrata di Windows a partire da .NET Framework 3,5. Non sono necessarie direttive machine.config specifiche. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non fornisce il supporto per altri protocolli di autenticazione, ad esempio di base o digest.

 Per abilitare questa funzionalità, è anche possibile applicare un hotfix a .NET Framework 2,0. Per ulteriori informazioni, vedere [correzione: messaggio di errore quando si tenta di installare un'applicazione ClickOnce creata nel .NET Framework 2,0 in un computer client configurato per l'utilizzo di un server proxy: "autenticazione proxy obbligatoria"](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that).

 Per ulteriori informazioni, vedere [ \<defaultProxy> elemento (impostazioni di rete)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>Compatibilità tra ClickOnce e Web browser
 Attualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le installazioni vengono avviate solo se l'URL del manifesto di distribuzione viene aperto utilizzando Internet Explorer. Una distribuzione il cui URL viene avviato da un'altra applicazione, ad esempio Microsoft Office Outlook, verrà avviata correttamente solo se Internet Explorer è impostato come Web browser predefinito.

> [!NOTE]
> Mozilla Firefox è supportato se il provider di distribuzione non è vuoto o se è installata l'estensione Microsoft .NET Framework Assistant. Questa estensione è assemblata con .NET Framework 3,5 SP1. Per il supporto di XBAP, il plug-in NPWPF viene attivato quando necessario.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Attivazione di applicazioni ClickOnce tramite scripting del browser
 Se è stata sviluppata una pagina Web personalizzata che avvia un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando lo scripting attivo, è possibile che l'applicazione non venga avviata in alcuni computer. Internet Explorer contiene un'impostazione denominata **richiesta automatica di download di file** , che influiscono su questo comportamento. Questa impostazione è disponibile nella scheda **sicurezza** del menu **Opzioni** che influiscono su questo comportamento. Viene chiamato **prompt automatico per i download di file** ed è elencato sotto la categoria **Downloads** . Per impostazione predefinita, la proprietà è impostata su **Abilita** per le pagine Web Intranet e per la **disabilitazione** per le pagine Web Internet. Quando questa impostazione è impostata su **Disabilita** , qualsiasi tentativo di attivare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione a livello di codice (ad esempio, assegnando il relativo URL alla `document.location` proprietà) verrà bloccato. In questa circostanza, gli utenti possono avviare le applicazioni solo tramite un download avviato dall'utente, ad esempio facendo clic su un collegamento ipertestuale impostato sull'URL dell'applicazione.

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

## <a name="use-third-party-web-servers"></a>Usare server Web di terze parti
 Se si distribuisce un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione da un server Web diverso da IIS, è possibile che si verifichi un problema se il server restituisce il tipo di contenuto non corretto per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i file di chiave, ad esempio il manifesto di distribuzione e il manifesto dell'applicazione. Per risolvere questo problema, vedere la documentazione della guida del server Web per informazioni su come aggiungere nuovi tipi di contenuto al server e assicurarsi che tutti i mapping dell'estensione di file elencati nella tabella seguente siano disponibili.

|Estensione del file|Tipo di contenuto|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce e unità mappate
 Se si usa Visual Studio per pubblicare un'applicazione ClickOnce, non è possibile specificare un'unità mappata come percorso di installazione. Tuttavia, è possibile modificare l'applicazione ClickOnce per l'installazione da un'unità mappata usando il generatore di manifesti e l'editor (Mage.exe e MageUI.exe). Per ulteriori informazioni, vedere [Mage.exe (strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) e [MageUI.exe (strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocollo FTP non supportato per l'installazione di applicazioni
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] supporta l'installazione di applicazioni da qualsiasi server Web HTTP 1,1 o file server. FTP, il File Transfer Protocol, non è supportato per l'installazione di applicazioni. È possibile utilizzare FTP solo per pubblicare le applicazioni. Nella tabella seguente sono riepilogate queste differenze:

| Tipo di URL | Descrizione |
|----------| - |
| ftp:// | È possibile pubblicare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo. |
| http:// | È possibile installare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo. |
| https:// | È possibile installare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo. |
| file:// | È possibile installare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione utilizzando questo protocollo. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Firewall
 Per impostazione predefinita, Windows XP SP2 Abilita il Windows Firewall. Se si sviluppa l'applicazione in un computer in cui è installato Windows XP, è ancora possibile pubblicare ed eseguire [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni dal server locale che esegue IIS. Tuttavia, non è possibile accedere a tale server che esegue IIS da un altro computer, a meno che non si apra il Windows Firewall. Per istruzioni sulla gestione del Windows Firewall, vedere la Guida di Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: abilitare le estensioni del server di FrontPage
 Estensioni del server di FrontPage di Microsoft è necessario per la pubblicazione di applicazioni in un server Web Windows che usa HTTP.

 Per impostazione predefinita, in Windows Server non è installato Estensioni del server di FrontPage. Se si desidera utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per pubblicare in un server Web Windows Server che utilizza http con estensioni del server di FrontPage, è necessario installare prima estensioni del server di FrontPage. È possibile eseguire l'installazione utilizzando lo strumento di amministrazione del server in Windows Server.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: tipi di contenuto bloccati
 IIS su [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] blocca tutti i tipi di file, ad eccezione di determinati tipi di contenuto noti, ad esempio *htm* , *HTML* , *txt* e così via. Per abilitare la distribuzione delle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni tramite questo server, è necessario modificare le impostazioni di IIS per consentire il download di file di tipo *. Application* , *. manifest* e di qualsiasi altro tipo di file personalizzato usato dall'applicazione.

 Se si esegue la distribuzione utilizzando un server IIS, eseguire *inetmgr.exe* e aggiungere nuovi tipi di file per la pagina Web predefinita:

- Per le estensioni *. Application* e *. manifest* , il tipo MIME deve essere "Application/x-ms-application". Per gli altri tipi di file, il tipo MIME deve essere "Application/ottetto-Stream".

- Se si crea un tipo MIME con estensione " \<em> " e il tipo MIME "Application/ottetto-Stream", sarà possibile scaricare i file del tipo di file non bloccato. Tuttavia, non è possibile scaricare i tipi di file bloccati, ad esempio *\* . aspx* e *\* . asmx* .

  Per istruzioni specifiche sulla configurazione dei tipi MIME in Windows Server, vedere [come aggiungere un tipo MIME a un sito Web o a un'applicazione](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).

## <a name="content-type-mappings"></a>Mapping dei tipi di contenuto
 Quando si pubblica su HTTP, il tipo di contenuto (noto anche come tipo MIME) per il file *. Application* deve essere "Application/x-ms-application". Se nel server è installato .NET Framework 2,0, questo verrà impostato automaticamente. Se non è installato, è necessario creare un'associazione di tipo MIME per l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione vroot (o intero server).

 Se si esegue la distribuzione tramite un server IIS, eseguire <em>inetmgr.</em> exe e aggiungere un nuovo tipo di contenuto "Application/x-ms-application" per l'estensione *. Application* .

## <a name="http-compression-issues"></a>Problemi di compressione HTTP
 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è possibile eseguire download che usano la compressione HTTP, una tecnologia server Web che usa l'algoritmo gzip per comprimere un flusso di dati prima di inviare il flusso al client. Il client, in questo caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] decomprime il flusso prima di leggere i file.

 Se si utilizza IIS, è possibile abilitare facilmente la compressione HTTP. Tuttavia, quando si Abilita la compressione HTTP, questa viene abilitata solo per determinati tipi di file, ovvero file HTML e di testo. Per abilitare la compressione per gli assembly (con *estensione dll* ), i *file XML (XML),* i manifesti della distribuzione ( *. Application* ) e i manifesti dell'applicazione ( *. manifest* ), è necessario aggiungere questi tipi di file all'elenco dei tipi per comprimere IIS. Fino a quando non si aggiungono i tipi di file alla distribuzione, verranno compressi solo i file di testo e HTML.

 Per istruzioni dettagliate su IIS, vedere [come specificare tipi di documenti aggiuntivi per la compressione HTTP](https://support.microsoft.com/help/234497).

## <a name="see-also"></a>Vedere anche
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)
