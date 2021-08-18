---
title: Problemi di sicurezza/controllo delle versioni/manifesto (ClickOnce)
description: Informazioni sui problemi relativi alla ClickOnce, al controllo delle versioni delle applicazioni, alla sintassi e alla semantica dei manifesti che possono causare ClickOnce una distribuzione non riuscita.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b6048aeb6972b2f60c8ba421e9a1593ba2cf42a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035625"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemi relativi alla sicurezza, al controllo delle versioni e ai manifesti nelle distribuzioni ClickOnce

Esistono diversi problemi relativi alla sicurezza, al controllo delle versioni delle applicazioni, alla sintassi e alla semantica dei manifesti che possono causare la non riuscita [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di una distribuzione.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce e Windows controllo dell'account utente di Vista

In le applicazioni vengono eseguite per impostazione predefinita come utente standard, anche se l'utente corrente è connesso con un [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] account con autorizzazioni di amministratore. Se un'applicazione deve eseguire un'azione che richiede autorizzazioni di amministratore, indica al sistema operativo, che quindi richiede all'utente di immettere le credenziali di amministratore. Questa funzionalità, denominata Controllo dell'account utente, impedisce alle applicazioni di apportare modifiche che potrebbero influire sull'intero sistema operativo senza l'approvazione esplicita di un utente. Windows dichiarano di richiedere questa elevazione delle autorizzazioni specificando l'attributo `requestedExecutionLevel` nella sezione del manifesto `trustInfo` dell'applicazione.

A causa del rischio di esporre le applicazioni ad attacchi di elevazione dei privilegi di sicurezza, le applicazioni non possono richiedere l'elevazione delle autorizzazioni se controllo dell'account utente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è abilitato per il client. Qualsiasi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione che tenta di impostare il relativo attributo su o non verrà installata in `requestedExecutionLevel` `requireAdministrator` `highestAvailable` [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] .

In alcuni casi, è possibile che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione tenti di essere eseguita con autorizzazioni di amministratore a causa della logica di rilevamento del programma di installazione in [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] . In questo caso, è possibile impostare `requestedExecutionLevel` l'attributo nel manifesto dell'applicazione su `asInvoker` . In questo modo l'applicazione stessa verrà eseguita senza elevazione dei privilegi. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] aggiunge automaticamente questo attributo a tutti i manifesti dell'applicazione.

Se si sviluppa un'applicazione che richiede autorizzazioni di amministratore per l'intera durata dell'applicazione, è consigliabile distribuire l'applicazione usando invece la tecnologia Windows Installer (MSI). Per altre informazioni, vedere [nozioni Windows installer.](../extensibility/internals/windows-installer-basics.md)

## <a name="online-application-quotas-and-partial-trust-applications"></a>Quote di applicazioni online e applicazioni parzialmente attendibili

Se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione viene eseguita online anziché tramite un'installazione, deve rientrare nella quota impostata per le applicazioni online. Inoltre, un'applicazione di rete eseguita in attendibilità parziale, ad esempio con un set limitato di autorizzazioni di sicurezza, non può essere superiore alla metà delle dimensioni della quota.

Per altre informazioni e istruzioni su come modificare la quota di applicazioni online, vedere panoramica ClickOnce [cache.](../deployment/clickonce-cache-overview.md)

## <a name="versioning-issues"></a>Problemi relativi al controllo delle versioni

È possibile che si verifichino problemi se si assegnano nomi sicuri all'assembly e si incrementa il numero di versione dell'assembly per riflettere un aggiornamento dell'applicazione. Qualsiasi assembly compilato con un riferimento a un assembly con nome sicuro deve essere ricompilato oppure l'assembly tenterà di fare riferimento alla versione precedente. L'assembly proverà a eseguire questa operazione perché l'assembly usa il valore della versione precedente nella richiesta di associazione.

Si supponga, ad esempio, di avere un assembly con nome sicuro nel proprio progetto con la versione 1.0.0.0. Dopo aver compilato l'assembly, aggiungerlo come riferimento al progetto che contiene l'applicazione principale. Se si aggiorna l'assembly, si incrementa la versione a 1.0.0.1 e si tenta di distribuirlo senza ricompilare anche l'applicazione, l'applicazione non sarà in grado di caricare l'assembly in fase di esecuzione.

Questo errore può verificarsi solo se si modificano i manifesti manualmente. Questo errore non dovrebbe verificarsi se si genera la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione usando Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Specificare singoli .NET Framework assembly nel manifesto

L'applicazione non verrà caricata se è stata modificata manualmente una distribuzione per fare riferimento a una versione precedente di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un assembly .NET Framework. Ad esempio, se è stato aggiunto un riferimento all'assembly System.Net per una versione del .NET Framework precedente alla versione specificata nel manifesto, si verificherà un errore. In generale, non è consigliabile tentare di specificare riferimenti a singoli assembly .NET Framework, perché la versione del .NET Framework in cui viene eseguita l'applicazione viene specificata come dipendenza nel manifesto dell'applicazione.

## <a name="manifest-parsing-issues"></a>Problemi di analisi del manifesto

I file manifesto utilizzati da sono file XML e devono essere sia in formato corretto che validi: devono rispettare le regole della sintassi XML e utilizzare solo gli elementi e gli attributi definiti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nell'XML Schema pertinente.

Un elemento che può causare problemi in un file manifesto è la selezione di un nome per l'applicazione che contiene un carattere speciale, ad esempio una virgoletta singola o doppia. Il nome dell'applicazione fa parte della relativa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identità. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] attualmente non analizza le identità che contengono caratteri speciali. Se l'applicazione non viene attivata, assicurarsi di usare solo caratteri alfabetici e numerici per il nome e provare a distribuirla nuovamente.

Se i manifesti dell'applicazione o della distribuzione sono stati modificati manualmente, potrebbero essere stati involontariamente danneggiati. Il manifesto danneggiato impedirà un'installazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] corretta. È possibile eseguire il debug  di tali errori in fase di esecuzione facendo clic su Dettagli nella finestra di dialogo ClickOnce **errore** e leggendo il messaggio di errore nel log. Nel log verrà elencato uno dei messaggi seguenti:

- Descrizione dell'errore di sintassi e numero di riga e posizione del carattere in cui si è verificato l'errore.

- Nome di un elemento o di un attributo usato in violazione dello schema del manifesto. Se il codice XML è stato aggiunto manualmente ai manifesti, sarà necessario confrontare le aggiunte agli schemi del manifesto. Per altre informazioni, vedere [l'ClickOnce di distribuzione](../deployment/clickonce-deployment-manifest.md) e ClickOnce [dell'applicazione.](../deployment/clickonce-application-manifest.md)

- Conflitto di ID. I riferimenti alle dipendenze nei manifesti di distribuzione e dell'applicazione devono essere univoci nei relativi `name` `publicKeyToken` attributi e . Se entrambi gli attributi corrispondono tra due elementi qualsiasi all'interno di un manifesto, l'analisi del manifesto non riuscirà.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauzioni quando si modificano manualmente manifesti o applicazioni

Quando si aggiorna un manifesto dell'applicazione, è necessario firmare nuovamente sia il manifesto dell'applicazione che il manifesto della distribuzione. Il manifesto della distribuzione contiene un riferimento al manifesto dell'applicazione che include l'hash del file e la relativa firma digitale.

### <a name="precautions-with-deployment-provider-usage"></a>Precauzioni per l'utilizzo del provider di distribuzione

Il manifesto della distribuzione ha una proprietà che punta al percorso completo del percorso da cui l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] deve essere installata e `deploymentProvider` utilizzata:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Questo percorso viene impostato quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea l'applicazione ed è disponibile per le applicazioni installate. Il percorso punta al percorso standard da cui il programma di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installazione installerà l'applicazione e cerca gli aggiornamenti. Se si usa il **comando xcopy** per copiare un'applicazione in un percorso diverso, ma non si modifica la proprietà , farà comunque riferimento al percorso originale quando tenta di scaricare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `deploymentProvider` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione.

Se si vuole spostare o copiare un'applicazione, è necessario aggiornare anche il percorso, in modo che il client si `deploymentProvider` installi effettivamente dal nuovo percorso. L'aggiornamento di questo percorso rappresenta principalmente un problema se sono state installate applicazioni. Per le applicazioni online che vengono sempre avviate tramite l'URL originale, l'impostazione `deploymentProvider` di è facoltativa. Se è impostato, verrà rispettato. In caso contrario, l'URL usato per avviare l'applicazione verrà usato come URL di base per scaricare i `deploymentProvider` file dell'applicazione.

> [!NOTE]
> Ogni volta che si aggiorna il manifesto, è necessario firmarlo di nuovo.

## <a name="see-also"></a>Vedi anche

[Risolvere i ClickOnce distribuzioni](../deployment/troubleshooting-clickonce-deployments.md) 
 [Proteggere ClickOnce applicazioni](../deployment/securing-clickonce-applications.md) 
 [Scegliere una strategia ClickOnce distribuzione locale](../deployment/choosing-a-clickonce-deployment-strategy.md)
