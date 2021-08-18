---
title: Problemi di configurazione server/client (ClickOnce)
description: Informazioni sui problemi di configurazione del server e del client che possono influire sulla distribuzione dell ClickOnce app ClickOnce client.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 3ae02ecb906c14992672c822a7bda1c579d91d43
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120738"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemi relativi alla configurazione del server e del client nelle distribuzioni ClickOnce
Se si usa Internet Information Services (IIS) in Windows Server e la distribuzione contiene un tipo di file che Windows non riconosce, ad esempio un file Microsoft Word, IIS rifiuterà di trasmettere il file e la distribuzione non riuscirà.

 Inoltre, alcuni server Web e software applicativo Web, ad esempio , contengono un elenco di file e tipi di file che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è possibile scaricare. Ad esempio, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] impedisce il download di tutti i *Web.config* file. Questi file possono contenere informazioni riservate, ad esempio nomi utente e password.

 Anche se questa restrizione non deve causare problemi per il download di file di base, ad esempio manifesti e assembly, questa restrizione potrebbe impedire il download dei file di dati inclusi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nell'applicazione. In è possibile risolvere questo errore rimuovendo il gestore che impedisce il download di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tali file da Gestione configurazione IIS. Per altri dettagli, vedere la documentazione del server IIS.

 Alcuni server Web potrebbero bloccare i file con estensioni *come.dll*, *.config* e *mdf*. Windows applicazioni basate su applicazioni in genere includono file con alcune di queste estensioni. Se un utente tenta di eseguire [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione che accede a un file bloccato in un server Web, verrà generato un errore. Invece di sbloccare tutte le estensioni di file, pubblica ogni file dell'applicazione con estensione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *deploy* per impostazione predefinita. Pertanto, l'amministratore deve solo configurare il server Web per sbloccare le tre estensioni di file seguenti:

- *Application*

- *Manifest*

- *.deploy*

  È tuttavia possibile disabilitare questa opzione deselezionando l'opzione Usa **estensione di file ".deploy"** nella finestra di dialogo [Opzioni](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100))di pubblicazione , nel qual caso è necessario configurare il server Web per sbloccare tutte le estensioni di file usate nell'applicazione.

  Sarà necessario configurare *.manifest,* *.application* e *.deploy,* ad esempio se si usa IIS in cui non è stato installato il .NET Framework o se si usa un altro server Web , ad esempio Apache.

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce e Secure Sockets Layer (SSL)
 Un'applicazione funziona correttamente su SSL, tranne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] quando Internet Explorer genera una richiesta sul certificato SSL. La richiesta può essere generata quando si verificano problemi con il certificato, ad esempio quando i nomi dei siti non corrispondono o il certificato è scaduto. Per usare una connessione SSL, assicurarsi che il certificato sia aggiornato e che i dati del certificato corrispondano ai [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dati del sito.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce e proxy
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]offre il supporto per Windows'autenticazione proxy integrata a partire da .NET Framework 3.5. Non sono machine.config direttive specifiche. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non fornisce il supporto per altri protocolli di autenticazione, ad esempio Basic o Digest.

 È anche possibile applicare un hotfix a .NET Framework 2.0 per abilitare questa funzionalità. Per altre informazioni, vedere FIX: Error message when you [try to install a ClickOnce application that you created in the .NET Framework 2.0 onto a client computer that is configured to use a proxy server: "Proxy authentication required".](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that)

 Per altre informazioni, vedere [ \<defaultProxy> elemento (impostazioni di rete).](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce e Web browser compatibilità
 Attualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le installazioni verranno avviate solo se l'URL del manifesto della distribuzione viene aperto usando Internet Explorer. Una distribuzione il cui URL viene avviato da un'altra applicazione, ad esempio Microsoft Office Outlook, verrà avviata correttamente solo se Internet Explorer è impostato come predefinito Web browser.

> [!NOTE]
> Mozilla Firefox è supportato se il provider di distribuzione non è vuoto o se è installata l'estensione Microsoft .NET Framework Assistant. Questa estensione è in pacchetto con .NET Framework 3.5 SP1. Per il supporto XBAP, il plug-in NPWPF viene attivato quando necessario.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Attivare ClickOnce applicazioni tramite script del browser
 Se è stata sviluppata una pagina Web personalizzata che avvia un'applicazione tramite script attivo, è possibile che l'applicazione non venga avviata [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in alcuni computer. Internet Explorer contiene un'impostazione denominata **Richiesta automatica per i download di file**, che influisce su questo comportamento. Questa impostazione è disponibile **nella** scheda Sicurezza del menu **Opzioni** che influisce su questo comportamento. Si chiama **Richiesta automatica per i download di file** ed è elencata sotto la categoria **Download.** La proprietà è impostata su **Abilita per** impostazione predefinita per le pagine Web Intranet e su **Disabilita** per impostazione predefinita per le pagine Web Internet. Quando questa impostazione è impostata su **Disabilita**, qualsiasi tentativo di attivare un'applicazione a livello di codice ,ad esempio assegnando il relativo URL alla proprietà , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà `document.location` bloccato. In questa circostanza, gli utenti possono avviare le applicazioni solo tramite un download avviato dall'utente, ad esempio facendo clic su un collegamento ipertestuale impostato sull'URL dell'applicazione.

## <a name="additional-server-configuration-issues"></a>Altri problemi di configurazione del server

##### <a name="administrator-permissions-required"></a>Autorizzazioni di amministratore necessarie
 Se si pubblica con HTTP, è necessario disporre delle autorizzazioni di amministratore nel server di destinazione. IIS richiede questo livello di autorizzazioni. Se non si pubblica tramite HTTP, è necessaria solo l'autorizzazione di scrittura per il percorso di destinazione.

##### <a name="server-authentication-issues"></a>Problemi di autenticazione del server
 Quando si pubblica in un server remoto con l'opzione "Accesso anonimo" disattivata, verrà visualizzato l'avviso seguente:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> È possibile fare in modo che l'autenticazione NTLM (NT challenge-response) funzioni se il sito richiede credenziali diverse da quelle predefinite e, nella finestra di dialogo di sicurezza, fare clic su **OK** quando viene richiesto se si desidera salvare le credenziali fornite per le sessioni future. Tuttavia, questa soluzione alternativa non funzionerà per l'autenticazione di base.

## <a name="use-third-party-web-servers"></a>Usare server Web di terze parti
 Se si distribuisce un'applicazione da un server Web diverso da IIS, è possibile che si verifichi un problema se il server restituisce il tipo di contenuto non corretto per i file di chiave, ad esempio il manifesto della distribuzione e il manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Per risolvere questo problema, vedere la documentazione della Guida del server Web su come aggiungere nuovi tipi di contenuto al server e verificare che siano presenti tutti i mapping delle estensioni di file elencati nella tabella seguente.

|Estensione del file|Tipo di contenuto|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce e unità mappate
 Se si usa Visual Studio per pubblicare un'ClickOnce, non è possibile specificare un'unità mappata come percorso di installazione. È tuttavia possibile modificare l'applicazione ClickOnce per l'installazione da un'unità mappata usando il generatore e l'editor di manifesti (Mage.exe e MageUI.exe). Per altre informazioni, [vedereMage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) e [MageUI.exe (Strumento per la generazione e la modifica di manifesti, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocollo FTP non supportato per l'installazione di applicazioni
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] supporta l'installazione di applicazioni da qualsiasi server Web HTTP 1.1 o file server. FTP, il File Transfer Protocol, non è supportato per l'installazione di applicazioni. È possibile usare FTP solo per pubblicare applicazioni. La tabella seguente riepiloga queste differenze:

| Tipo di URL | Descrizione |
|----------| - |
| ftp:// | È possibile pubblicare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione usando questo protocollo. |
| http:// | È possibile installare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione usando questo protocollo. |
| https:// | È possibile installare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione usando questo protocollo. |
| file:// | È possibile installare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione usando questo protocollo. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows firewall
 Per impostazione predefinita, Windows XP SP2 abilita Windows firewall. Se si sviluppa l'applicazione in un computer in cui è installato Windows XP, è comunque possibile pubblicare ed eseguire applicazioni dal server locale che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esegue IIS. Tuttavia, non è possibile accedere al server che esegue IIS da un altro computer, a meno che non si accedono Windows Firewall. Vedere Windows guida per istruzioni sulla gestione del firewall Windows rete.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: abilitare le estensioni del server di FrontPage
 Estensioni del server di FrontPage da Microsoft è necessario per la pubblicazione di applicazioni in Windows server Web che usa HTTP.

 Per impostazione predefinita, Windows Server non Estensioni del server di FrontPage installato. Se si desidera utilizzare per pubblicare in un server Web Windows Server che utilizza HTTP con Estensioni del server di FrontPage, è necessario installare prima Estensioni del server di FrontPage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] server. È possibile eseguire l'installazione usando lo strumento di amministrazione Manage Your Server in Windows Server.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: tipi di contenuto bloccati
 IIS in blocca tutti i tipi di file ad eccezione di determinati tipi di contenuto [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] noti(ad esempio, *.htm*, *.html*, *.txt* e così via). Per abilitare la distribuzione di applicazioni tramite questo server, è necessario modificare le impostazioni di IIS per consentire il download di file di tipo .application , .manifest e qualsiasi altro tipo di file personalizzato usato [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dall'applicazione.  

 Se si esegue la distribuzione usando un server IIS, *eseguireinetmgr.exe* e aggiungere nuovi tipi di file per la pagina Web predefinita:

- Per le *estensioni .application* e *.manifest,* il tipo MIME deve essere "application/x-ms-application". Per altri tipi di file, il tipo MIME deve essere "application/octet-stream".

- Se si crea un tipo MIME con estensione " " e il tipo MIME "application/octet-stream", sarà possibile scaricare i file con tipo \<em> di file non bloccato. Non è tuttavia possibile scaricare tipi di file bloccati, ad esempio *\* aspx* *\* e asmx.*

  Per istruzioni specifiche sulla configurazione dei tipi MIME in Windows Server, vedere Come aggiungere un tipo MIME a un [sito Web o a un'applicazione.](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application)

## <a name="content-type-mappings"></a>Mapping dei tipi di contenuto
 Quando si esegue la pubblicazione su HTTP, il tipo di contenuto (noto anche come tipo MIME) per il file con estensione *application* deve essere "application/x-ms-application". Se la versione .NET Framework 2.0 è installata nel server, questa opzione verrà impostata automaticamente. Se non è installato, è necessario creare un'associazione di tipo MIME per la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vroot dell'applicazione (o l'intero server).

 Se si esegue la distribuzione con un server IIS, eseguire <em>inetmgr.</em> exe e aggiungere un nuovo tipo di contenuto "application/x-ms-application" per *l'estensione .application.*

## <a name="http-compression-issues"></a>Problemi di compressione HTTP
 Con , è possibile eseguire download che usano la compressione HTTP, una tecnologia server Web che usa l'algoritmo GZIP per comprimere un flusso di dati prima di inviare il flusso [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] al client. Il client, in questo caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] decomprime il flusso prima di leggere i file.

 Se si usa IIS, è possibile abilitare facilmente la compressione HTTP. Tuttavia, quando si abilita la compressione HTTP, questa è abilitata solo per determinati tipi di file, ovvero file HTML e di testo. Per abilitare la compressione per gli assembly (*.dll*), XML (*.xml*), manifesti di distribuzione (*.application*) e manifesti dell'applicazione (*manifest*), è necessario aggiungere questi tipi di file all'elenco di tipi per la compressione da parte di IIS. Finché non si aggiungono i tipi di file alla distribuzione, verranno compressi solo i file di testo e HTML.

 Per istruzioni dettagliate su IIS, vedere [Come specificare tipi di documento aggiuntivi per la compressione HTTP.](/troubleshoot/iis/content-types-http-compression)

## <a name="see-also"></a>Vedi anche
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)
