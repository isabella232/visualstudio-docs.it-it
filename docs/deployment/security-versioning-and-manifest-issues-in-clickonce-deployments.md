---
title: Problemi di sicurezza/controllo delle versioni/manifesti nella distribuzione ClickOnce
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
ms.openlocfilehash: bb2ec5229132265feb1095c9ee921d73a1568dd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "66745602"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemi relativi alla sicurezza, al controllo delle versioni e ai manifesti nelle distribuzioni ClickOnce

Esistono diversi problemi relativi alla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sicurezza, al controllo delle versioni delle applicazioni e alla sintassi del manifesto e alla semantica che possono causare la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mancata riuscita della distribuzione.

## <a name="clickonce-and-windows-vista-user-account-control"></a>Controllo dell'account utente di ClickOnce e Windows Vista

In [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] , per impostazione predefinita, le applicazioni vengono eseguite come utente standard, anche se l'utente corrente è connesso con un account che dispone di autorizzazioni di amministratore. Se un'applicazione deve eseguire un'azione che richiede autorizzazioni di amministratore, indica al sistema operativo che quindi chiede all'utente di immettere le credenziali di amministratore. Questa funzionalità, denominata controllo dell'account utente, impedisce alle applicazioni di apportare modifiche che potrebbero influire sull'intero sistema operativo senza l'approvazione esplicita dell'utente. Le applicazioni Windows dichiarano che richiedono questa elevazione delle autorizzazioni specificando l' `requestedExecutionLevel` attributo nella `trustInfo` sezione del manifesto dell'applicazione.

A causa del rischio di esporre le applicazioni agli attacchi con elevazione di sicurezza, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni non possono richiedere l'elevazione delle autorizzazioni se UAC è abilitato per il client. Qualsiasi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che tenti di impostare il relativo `requestedExecutionLevel` attributo `requireAdministrator` `highestAvailable` su o non verrà installata in [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] .

In alcuni casi, l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione potrebbe tentare di eseguire con autorizzazioni di amministratore a causa della logica di rilevamento del programma di installazione in [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] . In questo caso, è possibile impostare l' `requestedExecutionLevel` attributo nel manifesto dell'applicazione su `asInvoker` . Questa operazione causerà l'esecuzione dell'applicazione senza elevazione dei privilegi. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] aggiunge automaticamente questo attributo a tutti i manifesti dell'applicazione.

Se si sta sviluppando un'applicazione che richiede autorizzazioni di amministratore per l'intera durata dell'applicazione, è consigliabile distribuire l'applicazione usando la tecnologia Windows Installer (MSI). Per ulteriori informazioni, vedere [nozioni di base su Windows Installer](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Quote di applicazioni online e applicazioni con attendibilità parziale

Se l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione viene eseguita online anziché tramite un'installazione, deve rientrare nella quota accantonata per le applicazioni online. Inoltre, un'applicazione di rete eseguita in attendibilità parziale, ad esempio con un set limitato di autorizzazioni di sicurezza, non può essere maggiore della metà della dimensione della quota.

Per ulteriori informazioni e istruzioni su come modificare la quota dell'applicazione online, vedere [Cenni preliminari sulla cache ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Problemi relativi al controllo delle versioni

È possibile che si verifichino problemi se si assegnano nomi sicuri all'assembly e si incrementa il numero di versione dell'assembly per riflettere l'aggiornamento di un'applicazione. Tutti gli assembly compilati con un riferimento a un assembly con nome sicuro devono essere ricompilati o l'assembly tenterà di fare riferimento alla versione precedente. L'assembly proverà a eseguire questa operazione perché l'assembly usa il valore della versione precedente nella relativa richiesta di binding.

Si immagini, ad esempio, di avere un assembly con nome sicuro nel proprio progetto con la versione 1.0.0.0. Dopo aver compilato l'assembly, aggiungerlo come riferimento al progetto che contiene l'applicazione principale. Se si aggiorna l'assembly, si incrementa la versione in 1.0.0.1 e si prova a distribuirla senza ricompilare anche l'applicazione, l'applicazione non sarà in grado di caricare l'assembly in fase di esecuzione.

Questo errore può verificarsi solo se si modificano i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti manualmente. questo errore non dovrebbe verificarsi se si genera la distribuzione usando Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Specificare singoli assembly di .NET Framework nel manifesto

Se una distribuzione è stata modificata manualmente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per fare riferimento a una versione precedente di un assembly .NET Framework, l'applicazione non verrà caricata. Se, ad esempio, è stato aggiunto un riferimento all'assembly System.Net per una versione della .NET Framework prima della versione specificata nel manifesto, si verificherà un errore. In generale, non si deve tentare di specificare riferimenti a singoli assembly di .NET Framework, perché la versione di .NET Framework in cui viene eseguita l'applicazione viene specificata come dipendenza nel manifesto dell'applicazione.

## <a name="manifest-parsing-issues"></a>Problemi di analisi dei manifesti

I file manifesto utilizzati da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono file XML ed è necessario che siano entrambi ben formati e validi: devono rispettare le regole di sintassi XML e utilizzare solo elementi e attributi definiti nel XML schema pertinente.

Un elemento che può causare problemi in un file manifesto è la selezione di un nome per l'applicazione che contiene un carattere speciale, ad esempio virgolette singole o doppie. Il nome dell'applicazione fa parte della propria [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identità. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Attualmente non analizza le identità che contengono caratteri speciali. Se l'applicazione non viene attivata, assicurarsi di usare solo caratteri alfabetici e numerici per il nome e provare a distribuirla nuovamente.

Se i manifesti della distribuzione o dell'applicazione sono stati modificati manualmente, è possibile che siano stati danneggiati in modo involontario. Il manifesto danneggiato impedisce un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installazione corretta. È possibile eseguire il debug di tali errori in fase di esecuzione facendo clic su **Dettagli** nella finestra di dialogo **errore ClickOnce** e leggendo il messaggio di errore nel log. Il log elenca uno dei messaggi seguenti:

- Una descrizione dell'errore di sintassi, il numero di riga e la posizione del carattere in cui si è verificato l'errore.

- Nome di un elemento o di un attributo utilizzato per la violazione dello schema del manifesto. Se il codice XML è stato aggiunto manualmente ai manifesti, sarà necessario confrontare le aggiunte agli schemi del manifesto. Per ulteriori informazioni, vedere [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) e [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).

- Conflitto ID. I riferimenti alle dipendenze nei manifesti di distribuzione e dell'applicazione devono essere univoci in entrambi `name` `publicKeyToken` gli attributi e. Se entrambi gli attributi corrispondono tra due elementi qualsiasi all'interno di un manifesto, l'analisi del manifesto avrà esito negativo.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauzioni per la modifica manuale di manifesti o applicazioni

Quando si aggiorna un manifesto dell'applicazione, è necessario firmare di nuovo sia il manifesto dell'applicazione che il manifesto della distribuzione. Il manifesto di distribuzione contiene un riferimento al manifesto dell'applicazione che include l'hash del file e la relativa firma digitale.

### <a name="precautions-with-deployment-provider-usage"></a>Precauzioni con l'utilizzo del provider di distribuzione

Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione ha una `deploymentProvider` proprietà che punta al percorso completo della posizione da cui l'applicazione deve essere installata e gestita:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Questo percorso viene impostato quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea l'applicazione ed è obbligatorio per le applicazioni installate. Il percorso punta alla posizione standard in cui il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] programma di installazione installerà l'applicazione e cerca gli aggiornamenti. Se si utilizza il comando **xcopy** per copiare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in un percorso diverso, ma non si modifica la `deploymentProvider` proprietà, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] si riferisce ancora al percorso originale quando tenta di scaricare l'applicazione.

Se si desidera spostare o copiare un'applicazione, è necessario aggiornare anche il `deploymentProvider` percorso, in modo che il client venga effettivamente installato dal nuovo percorso. L'aggiornamento di questo percorso rappresenta principalmente un problema se sono state installate applicazioni. Per le applicazioni online che vengono sempre avviate tramite l'URL originale, l'impostazione di `deploymentProvider` è facoltativa. Se `deploymentProvider` è impostato, verrà rispettato; in caso contrario, l'URL utilizzato per avviare l'applicazione verrà utilizzato come URL di base per scaricare i file dell'applicazione.

> [!NOTE]
> Ogni volta che si aggiorna il manifesto, è necessario firmarlo di nuovo.

## <a name="see-also"></a>Vedere anche

[Risolvere i problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md) 
 [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md) 
 [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
