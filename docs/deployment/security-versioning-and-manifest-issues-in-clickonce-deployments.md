---
title: Sicurezza, controllo delle versioni e i problemi di manifesto nelle distribuzioni ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e95c89633c047a0a56a1efed5aba46e6632da7cc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983431"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemi relativi alla sicurezza, al controllo delle versioni e ai manifesti nelle distribuzioni ClickOnce

Sono disponibili un'ampia gamma di problemi relativi alla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sicurezza, controllo delle versioni dell'applicazione e manifesto sintassi e semantica che può causare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione non corretta.

## <a name="clickonce-and-windows-vista-user-account-control"></a>Controllo Account utente di Windows Vista e ClickOnce

In [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], applicazioni per impostazione predefinita vengono eseguite come utente standard, anche se l'utente corrente è connesso con un account che disponga delle autorizzazioni di amministratore. Se un'applicazione deve eseguire un'azione che richiede le autorizzazioni di amministratore, indica al sistema operativo, che quindi chiede all'utente di immettere le credenziali di amministratore. Questa funzionalità, denominata controllo Account utente (UAC), impedisce alle applicazioni di apportare modifiche che possono interessare l'intero sistema operativo senza l'approvazione esplicita dell'utente. Le applicazioni di Windows dichiarano che richiedono l'elevazione delle autorizzazioni, specificando il `requestedExecutionLevel` attributo la `trustInfo` sezione del manifesto dell'applicazione.

A causa del rischio di esposizione delle applicazioni ad attacchi di elevazione dei privilegi di sicurezza, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni non possono richiedere l'elevazione delle autorizzazioni se questa opzione è abilitata per il client. Eventuali [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione che tenta di impostare relativi `requestedExecutionLevel` dell'attributo `requireAdministrator` oppure `highestAvailable` non verranno installati nei [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].

In alcuni casi, il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione potrebbe tentare l'esecuzione con autorizzazioni di amministratore a causa di logica di rilevamento del programma di installazione su [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. In questo caso, è possibile impostare il `requestedExecutionLevel` attributo nel manifesto dell'applicazione per `asInvoker`. Ciò causerà l'applicazione per l'esecuzione senza l'elevazione dei privilegi. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Questo attributo viene aggiunto automaticamente a tutti i manifesti dell'applicazione.

Se si sta sviluppando un'applicazione che richiede le autorizzazioni di amministratore per l'intera durata dell'applicazione, è consigliabile distribuire l'applicazione usando la tecnologia Windows Installer (MSI) alternativa. Per altre informazioni, vedere [nozioni di base di Windows Installer](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Le quote online delle applicazioni e le applicazioni con attendibilità parziale

Se il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è in esecuzione in modalità online anziché un'installazione, è necessario che la quota di riservare per le applicazioni online. Inoltre, un'applicazione di rete che viene eseguito in attendibilità parziale, ad esempio con un set limitato di autorizzazioni di sicurezza, non può essere maggiore della metà delle dimensioni della quota.

Per altre informazioni e istruzioni su come modificare la quota di applicazione online, vedere [Cenni preliminari sulla cache di ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Problemi relativi al controllo delle versioni

Potrebbero verificarsi problemi se si assegna i nomi sicuri per l'assembly e incrementare il numero di versione di assembly in modo da riflettere l'aggiornamento di un'applicazione. Tutti gli assembly compilati con un riferimento a un assembly con nome sicuro deve essere ricompilato o l'assembly verrà effettuato un tentativo di fare riferimento alla versione precedente. L'assembly cercherà questo perché l'assembly tramite il valore della versione precedente di richiesta di associazione.

Ad esempio si dispone di un assembly con nome sicuro in un progetto specifico con la versione 1.0.0.0. Dopo aver compilato l'assembly, aggiungerlo come riferimento al progetto che contiene l'applicazione principale. Se si aggiorna l'assembly, incrementa la versione 1.0.0.1 e provare a eseguire la distribuzione senza ricompilare l'applicazione, l'applicazione non sarà in grado di caricare l'assembly in fase di esecuzione.

Questo errore può verificarsi solo se si sta modificando il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti manualmente oppure non si dovrebbe riscontrare questo errore se si genera la distribuzione usando Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Specificare i singoli assembly di .NET Framework nel manifesto

L'applicazione non riuscirà a caricare se è stata modificata manualmente una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione a cui fare riferimento a una versione precedente di un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assembly. Ad esempio, se è stato aggiunto un riferimento all'assembly di System.Net per una versione del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] prima la versione specificata nel manifesto, quindi potrebbe verificarsi un errore. In generale, è consigliabile non tenta di specificare riferimenti ai singoli [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] gli assembly, come la versione del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in cui viene eseguita l'applicazione viene specificato come una dipendenza nel manifesto dell'applicazione.

## <a name="manifest-parsing-issues"></a>Manifesto i problemi di analisi

I file manifesto in cui vengono utilizzati da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono file XML e deve essere sia ben formato e valido: devono rispettare le regole di sintassi XML e usare solo gli elementi e attributi definiti nello schema XML pertinente.

Qualcosa che può causare problemi in un file manifesto consiste nel selezionare un nome per l'applicazione che contiene un carattere speciale, ad esempio un segno di virgolette singolo o doppio. Nome dell'applicazione fa parte del relativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identità. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] attualmente non analizza le identità che può contenere caratteri speciali. Se l'applicazione non riesce per l'attivazione, assicurarsi che si usano caratteri solo in ordine alfabetico e numerici per il nome e provare a distribuirlo nuovamente.

Se è stata modificata manualmente i manifesti di distribuzione o dell'applicazione, si potrebbe avere involontariamente danneggiato li. Impedendo così una corretta [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installazione. È possibile eseguire il debug di tali errori in fase di esecuzione facendo clic **dettagli** nel **ClickOnce errore** nella finestra di dialogo e la lettura del messaggio di errore nel log. Il log verrà visualizzato uno dei seguenti messaggi:

- Una descrizione dell'errore di sintassi e il numero di riga e carattere posizione in cui si è verificato l'errore.

- Il nome di un elemento o attributo utilizzato in violazione dello schema del manifesto. Se è stato aggiunto manualmente XML per i manifesti, è necessario confrontare le aggiunte agli schemi del manifesto. Per altre informazioni, vedere [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) e [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).

- Un conflitto tra ID. Riferimenti delle dipendenze nei manifesti di distribuzione e dell'applicazione devono essere univoci in entrambi i `name` e `publicKeyToken` attributi. Se entrambi gli attributi corrispondono tra qualsiasi due elementi all'interno di un manifesto, l'analisi del manifesto non riuscirà.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauzioni relative alla modifica manuale dei manifesti o applicazioni

Quando si aggiorna un manifesto dell'applicazione, è necessario firmare nuovamente il manifesto dell'applicazione sia il manifesto di distribuzione. Il manifesto di distribuzione contiene un riferimento al manifesto dell'applicazione che include l'hash del file e la relativa firma digitale.

### <a name="precautions-with-deployment-provider-usage"></a>Precauzioni relative all'utilizzo di utilizzo del provider di distribuzione

Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione ha un `deploymentProvider` proprietà che punta al percorso completo della posizione da in cui l'applicazione deve essere installata e servito:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Questo percorso viene impostato quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea l'applicazione ed è obbligatorio per le applicazioni installate. Il percorso punta alla posizione standard in cui il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] programma di installazione installerà l'applicazione da e cercare gli aggiornamenti. Se si usa il **xcopy** comando per copiare una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione in un percorso diverso, ma non modificare il `deploymentProvider` proprietà [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] faranno ancora riferimento nuovamente nel percorso originale quando prova a scaricare il applicazione.

Se si desidera spostare o copiare un'applicazione, è necessario aggiornare anche il `deploymentProvider` percorso, in modo che il client esegua effettivamente l'installazione dalla nuova posizione. L'aggiornamento di questo percorso è principalmente un problema se si sono installate le applicazioni. Per le applicazioni online che vengono sempre avviate tramite l'URL originale, impostare il `deploymentProvider` è facoltativo. Se `deploymentProvider` è impostato, verrà rispettata; in caso contrario, l'URL usato per avviare l'applicazione verrà utilizzato come URL di base per scaricare i file dell'applicazione.

> [!NOTE]
> Ogni volta che si aggiorna il manifesto è necessario inoltre firmarlo nuovamente.

## <a name="see-also"></a>Vedere anche

[Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)  
[Applicazioni Securw ClickOnce](../deployment/securing-clickonce-applications.md)  
[Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)