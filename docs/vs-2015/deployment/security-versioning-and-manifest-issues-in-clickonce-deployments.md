---
title: Sicurezza, controllo delle versioni e i problemi di manifesto nelle distribuzioni ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 1274a636dd49a2ade1f21941d24817a0d54d49c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529122"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemi relativi alla sicurezza, al controllo delle versioni e ai manifesti nelle distribuzioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [sicurezza, controllo delle versioni e i problemi di manifesto nelle distribuzioni ClickOnce](https://docs.microsoft.com/visualstudio/deployment/security-versioning-and-manifest-issues-in-clickonce-deployments).  
  
Sono disponibili un'ampia gamma di problemi relativi alla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sicurezza, controllo delle versioni dell'applicazione e manifesto sintassi e semantica che può causare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione non corretta.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>Controllo Account utente di Windows Vista e ClickOnce  
 In [!INCLUDE[windowsver](../includes/windowsver-md.md)], applicazioni per impostazione predefinita vengono eseguite come utente standard, anche se l'utente corrente è connesso con un account che disponga delle autorizzazioni di amministratore. Se un'applicazione deve eseguire un'azione che richiede le autorizzazioni di amministratore, indica al sistema operativo, che quindi chiede all'utente di immettere le credenziali di amministratore. Questa funzionalità, denominata controllo Account utente (UAC), impedisce alle applicazioni di apportare modifiche che possono interessare l'intero sistema operativo senza l'approvazione esplicita dell'utente. Le applicazioni di Windows dichiarano che richiedono l'elevazione delle autorizzazioni, specificando il `requestedExecutionLevel` attributo la `trustInfo` sezione del manifesto dell'applicazione.  
  
 A causa del rischio di esposizione delle applicazioni ad attacchi di elevazione dei privilegi di sicurezza, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni non possono richiedere l'elevazione delle autorizzazioni se questa opzione è abilitata per il client. Eventuali [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione che tenta di impostare relativi `requestedExecutionLevel` dell'attributo `requireAdministrator` oppure `highestAvailable` non verranno installati nei [!INCLUDE[windowsver](../includes/windowsver-md.md)].  
  
 In alcuni casi, il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione potrebbe tentare l'esecuzione con autorizzazioni di amministratore a causa di logica di rilevamento del programma di installazione su [!INCLUDE[windowsver](../includes/windowsver-md.md)]. In questo caso, è possibile impostare il `requestedExecutionLevel` attributo nel manifesto dell'applicazione per `asInvoker`. Ciò causerà l'applicazione per l'esecuzione senza l'elevazione dei privilegi. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] Questo attributo viene aggiunto automaticamente a tutti i manifesti dell'applicazione.  
  
 Se si sta sviluppando un'applicazione che richiede le autorizzazioni di amministratore per l'intera durata dell'applicazione, è consigliabile distribuire l'applicazione usando la tecnologia Windows Installer (MSI) alternativa. Per altre informazioni, vedere [nozioni di base di Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Applicazioni con attendibilità parziale e le quote online delle applicazioni  
 Se il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione è in esecuzione in modalità online anziché un'installazione, è necessario che la quota di riservare per le applicazioni online. Inoltre, un'applicazione di rete che viene eseguito in attendibilità parziale, ad esempio con un set limitato di autorizzazioni di sicurezza, non può essere maggiore della metà delle dimensioni della quota.  
  
 Per altre informazioni e istruzioni su come modificare la quota di applicazione online, vedere [Cenni preliminari sulla Cache di ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Problemi di controllo delle versioni  
 Potrebbero verificarsi problemi se si assegna i nomi sicuri per l'assembly e incrementare il numero di versione di assembly in modo da riflettere l'aggiornamento di un'applicazione. Tutti gli assembly compilati con un riferimento a un assembly con nome sicuro deve essere ricompilato o l'assembly verrà effettuato un tentativo di fare riferimento alla versione precedente. L'assembly cercherà questo perché l'assembly tramite il valore della versione precedente di richiesta di associazione.  
  
 Ad esempio si dispone di un assembly con nome sicuro in un progetto specifico con la versione 1.0.0.0. Dopo aver compilato l'assembly, aggiungerlo come riferimento al progetto che contiene l'applicazione principale. Se si aggiorna l'assembly, incrementa la versione 1.0.0.1 e provare a eseguire la distribuzione senza ricompilare l'applicazione, l'applicazione non sarà in grado di caricare l'assembly in fase di esecuzione.  
  
 Questo errore può verificarsi solo se si sta modificando la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesti manualmente oppure non si dovrebbe riscontrare questo errore se si genera la distribuzione tramite [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Specificare i singoli assembly .NET Framework nel manifesto  
 L'applicazione non riuscirà a caricare se è stata modificata manualmente una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione a cui fare riferimento a una versione precedente di un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] assembly. Ad esempio, se è stato aggiunto un riferimento all'assembly di System.Net per una versione del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] prima la versione specificata nel manifesto, quindi potrebbe verificarsi un errore. In generale, è consigliabile non tenta di specificare riferimenti ai singoli [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] gli assembly, come la versione del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] in cui viene eseguita l'applicazione viene specificato come una dipendenza nel manifesto dell'applicazione.  
  
## <a name="manifest-parsing-issues"></a>Analisi dei problemi di manifesti  
 I file manifesto in cui vengono utilizzati da [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sono file XML e deve essere sia ben formato e valido: devono rispettare le regole di sintassi XML e usare solo gli elementi e attributi definiti nello schema XML pertinente.  
  
 Qualcosa che può causare problemi in un file manifesto consiste nel selezionare un nome per l'applicazione che contiene un carattere speciale, ad esempio un segno di virgolette singolo o doppio. Nome dell'applicazione fa parte del relativo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] identità. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] attualmente non analizza le identità che può contenere caratteri speciali. Se l'applicazione non riesce per l'attivazione, assicurarsi che si usano caratteri solo in ordine alfabetico e numerici per il nome e provare a distribuirlo nuovamente.  
  
 Se è stata modificata manualmente i manifesti di distribuzione o dell'applicazione, si potrebbe avere involontariamente danneggiato li. Impedendo così una corretta [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installazione. È possibile eseguire il debug di tali errori in fase di esecuzione facendo clic **dettagli** nel **ClickOnce errore** nella finestra di dialogo e la lettura del messaggio di errore nel log. Il log verrà visualizzato uno dei seguenti messaggi:  
  
-   Una descrizione dell'errore di sintassi e il numero di riga e carattere posizione in cui si è verificato l'errore.  
  
-   Il nome di un elemento o attributo utilizzato in violazione dello schema del manifesto. Se è stato aggiunto manualmente XML per i manifesti, è necessario confrontare le aggiunte agli schemi del manifesto. Per altre informazioni, vedere [del manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) e [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
-   Un conflitto tra ID. Riferimenti delle dipendenze nei manifesti di distribuzione e dell'applicazione devono essere univoci in entrambi i `name` e `publicKeyToken` attributi. Se entrambi gli attributi corrispondono tra qualsiasi due elementi all'interno di un manifesto, l'analisi del manifesto non riuscirà.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauzioni relative alla modifica manuale dei manifesti o applicazioni  
 Quando si aggiorna un manifesto dell'applicazione, è necessario firmare nuovamente il manifesto dell'applicazione sia il manifesto di distribuzione. Il manifesto di distribuzione contiene un riferimento al manifesto dell'applicazione che include l'hash del file e la relativa firma digitale.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Precauzioni relative all'utilizzo di utilizzo del Provider di distribuzione  
 Il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto di distribuzione ha un `deploymentProvider` proprietà che punta al percorso completo della posizione da in cui l'applicazione deve essere installata e servito:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Questo percorso viene impostato quando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crea l'applicazione ed è obbligatorio per le applicazioni installate. Il percorso punta alla posizione standard in cui il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] programma di installazione installerà l'applicazione da e cercare gli aggiornamenti. Se si usa il **xcopy** comando per copiare una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione in un percorso diverso, ma non modificare il `deploymentProvider` proprietà [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] faranno ancora riferimento nuovamente nel percorso originale quando prova a scaricare il applicazione.  
  
 Se si desidera spostare o copiare un'applicazione, è necessario aggiornare anche il `deploymentProvider` percorso, in modo che il client esegua effettivamente l'installazione dalla nuova posizione. L'aggiornamento di questo percorso è principalmente un problema se si sono installate le applicazioni. Per le applicazioni online che vengono sempre avviate tramite l'URL originale, impostare il `deploymentProvider` è facoltativo. Se `deploymentProvider` è impostato, verrà rispettata; in caso contrario, l'URL usato per avviare l'applicazione verrà utilizzato come URL di base per scaricare i file dell'applicazione.  
  
> [!NOTE]
>  Ogni volta che si aggiorna il manifesto è necessario inoltre firmarlo nuovamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi di distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



