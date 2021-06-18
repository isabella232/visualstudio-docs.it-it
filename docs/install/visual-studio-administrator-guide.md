---
title: Guida di Visual Studio Administrator
titleSuffix: ''
description: Altre informazioni su come distribuire Visual Studio in un ambiente aziendale.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ba41c545c2af2e0490ef0410fde7849706123940
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306709"
---
# <a name="visual-studio-administrator-guide"></a>Guida di Visual Studio Administrator

Negli ambienti aziendali, gli amministratori di sistema distribuiscono in genere le installazioni agli utenti finali da una condivisione di rete o tramite software di gestione dei sistemi. Il motore di installazione di Visual Studio è stato progettato per supportare la distribuzione aziendale e consente agli amministratori di sistema di creare un percorso di installazione di rete, preconfigurare valori di installazione predefiniti, distribuire codici Product Key durante il processo di installazione e gestire aggiornamenti di prodotto in seguito a una distribuzione eseguita correttamente.

Questa guida dell'amministratore offre indicazioni basate sullo scenario per la distribuzione aziendale in ambienti di rete.

## <a name="before-you-begin"></a>Prima di iniziare

Prima di distribuire Visual Studio all'interno dell'organizzazione, è necessario prendere alcune decisioni e svolgere alcune attività:

::: moniker range=">=vs-2019"

* Assicurarsi che ogni computer di destinazione soddisfi i [requisiti minimi di installazione](/visualstudio/releases/2019/system-requirements/).

::: moniker-end

::: moniker range="vs-2017"

* Assicurarsi che ogni computer di destinazione soddisfi i [requisiti minimi di installazione](/visualstudio/productinfo/vs2017-system-requirements-vs/).

::: moniker-end

* Definire le esigenze di manutenzione.

  Se l'azienda ha l'esigenza di mantenere un set di funzionalità più a lungo ma desidera comunque ottenere aggiornamenti di manutenzione regolari, prevedere di usare una baseline di manutenzione. Per altre informazioni, vedere la sezione Opzioni di supporto per i clienti Enterprise e ***Professional*** della pagina ciclo di vita e manutenzione del prodotto [Visual Studio,](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) nonché la pagina Aggiorna [Visual Studio](update-servicing-baseline.md) in una baseline di manutenzione.

* Scegliere il modello di aggiornamento.

  Da dove si desidera che i singoli computer client otterrà gli aggiornamenti del prodotto? In particolare, decidere se il client deve ottenere gli aggiornamenti da Internet o da una condivisione locale a livello aziendale. Se si sceglie di usare una condivisione locale, decidere se i singoli utenti possono aggiornare i propri client o se un amministratore si farà carico di aggiornare i client a livello di codice. È meglio prendere queste decisioni prima che l'installazione originale avvenga nel computer client. Per altre informazioni, vedere [Creare un'installazione di rete di Visual Studio](../install/create-a-network-installation-of-visual-studio.md).

  È possibile aggiornare un layout di installazione di rete di Visual Studio con gli aggiornamenti più recenti del prodotto in modo che possa essere usato sia come punto di installazione per l'aggiornamento più recente di Visual Studio, sia per mantenere le installazioni già distribuite nelle workstation client. Per altre informazioni, vedere [Aggiornare un'installazione basata sulla rete di Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Le organizzazioni che utilizzano gli strumenti di distribuzione aziendali possono sfruttare il fatto che gli aggiornamenti Visual Studio sono disponibili nel catalogo Microsoft Update e Windows Server Update Services. Per altre informazioni, vedere [Abilitazione degli aggiornamenti dell'amministratore](../install/enabling-administrator-updates.md) [e Applicazione degli aggiornamenti dell'amministratore](../install/applying-administrator-updates.md).

  Per i computer che non sono connessi a Internet, la creazione di un layout minimo è il modo più semplice e rapido per aggiornare le istanze Visual Studio offline. Per altre informazioni, vedere [Aggiornare Visual Studio usando un layout offline minimo.](update-minimal-layout.md)

::: moniker range=">=vs-2019"

* Decidere di quali [carichi di lavoro e componenti](workload-and-component-ids.md?view=vs-2019&preserve-view=true) ha bisogno l'azienda.

* Decidere se usare un [file di risposta](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true), scelta che semplifica la gestione delle informazioni dettagliate nel file di script.

::: moniker-end

::: moniker range="vs-2017"

* Decidere di quali [carichi di lavoro e componenti](workload-and-component-ids.md?view=vs-2017&preserve-view=true) ha bisogno l'azienda.

* Decidere se usare un [file di risposta](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true), scelta che semplifica la gestione delle informazioni dettagliate nel file di script.

::: moniker-end

* Decidere se abilitare Criteri di gruppo e se configurare la disabilitazione dei suggerimenti dei clienti nei singoli computer in Visual Studio.

::: moniker range=">=vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Passaggio 1: Scaricare i file di prodotto Visual Studio

* [Selezionare i carichi di lavoro e i componenti](workload-and-component-ids.md?view=vs-2019&preserve-view=true) da installare.

* [Creare una condivisione di rete per i file di prodotto di Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Passaggio 2: Creare uno script di installazione

* Creare uno script di installazione che usi [parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) per controllare l'installazione.

  >[!NOTE]
  > È possibile semplificare gli script utilizzando un [file di risposta](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true). Assicurarsi di creare un file di risposta che contenga l'opzione di installazione predefinita.

* (Facoltativo) Includere nello script di installazione le istruzioni per [applicare un codice Product Key per contratti multilicenza](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true), in modo che gli utenti non debbano attivare il software separatamente.

* (Facoltativo) Aggiornare il layout di rete per [controllare quando gli aggiornamenti del prodotto vengono messi a disposizione degli utenti finali e la loro provenienza](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true).

* (Facoltativo) Impostare i criteri del registro di sistema che influiscono sulla distribuzione di Visual Studio, ad esempio dove sono installati alcuni pacchetti condivisi con altre versioni o istanze, [dove vengono memorizzati i pacchetti nella cache](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) o [se i pacchetti vengono memorizzati nella cache](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true).

* (Facoltativo) Impostare Criteri di gruppo. È anche possibile [configurare Visual Studio per disabilitare i suggerimenti dei clienti](../ide/visual-studio-experience-improvement-program.md) nei singoli computer.

## <a name="step-3---deploy-updates"></a>Passaggio 3- Distribuire gli aggiornamenti

Usare la tecnologia di distribuzione desiderata per eseguire lo script nelle workstation di sviluppo di destinazione.

* [Aggiornare il percorso di rete con gli aggiornamenti più recenti](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) di Visual Studio eseguendo regolarmente il comando usato nel passaggio 1 in modo da aggiungere i componenti aggiornati.

  È possibile aggiornare Visual Studio usando uno script di aggiornamento. A tale scopo, usare il parametro [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) della riga di comando.

  È possibile distribuire Visual Studio aggiornamenti dal Windows Server Update Services o dal catalogo Microsoft Update con strumenti come System Center Gestione configurazione.  Per altre [informazioni, vedere Applicazione degli aggiornamenti](applying-administrator-updates.md) dell'amministratore. 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Passaggio 4 - (facoltativo) Usare Visual Studio per verificare l'installazione

Sono stati resi disponibili diversi strumenti che consentono di [rilevare e gestire le istanze installate di Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) nei computer client.

## <a name="advanced-configuration"></a>Configurazione avanzata

Per impostazione predefinita, l Visual Studio installazione consente l'inclusione di tipi personalizzati nelle ricerche Bing dall'elenco errori F1 e dai collegamenti di codice. È possibile configurare Visual Studio per disabilitare il meccanismo di ricerca dall'inclusione di qualsiasi tipo di utente personalizzato modificando il valore della chiave del Registro di sistema seguente in base ai criteri:

**DWORD "PutCustomTypeInBingSearch" 0**

Il Registro di sistema si trova nella directory *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics dell'hive del Registro \* di sistema privato. Per istruzioni su come aprire l'hive del Registro di sistema, vedere modifica del Registro di sistema [per un'Visual Studio istanza di](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Passaggio 1: Scaricare i file di prodotto Visual Studio

* [Selezionare i carichi di lavoro e i componenti](workload-and-component-ids.md?view=vs-2017&preserve-view=true) da installare.

* [Creare una condivisione di rete per i file di prodotto di Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Passaggio 2: Creare uno script di installazione

* Creare uno script di installazione che usi [parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) per controllare l'installazione.

  >[!NOTE]
  > È possibile semplificare gli script utilizzando un [file di risposta](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true). Assicurarsi di creare un file di risposta che contenga l'opzione di installazione predefinita.

* (Facoltativo) Includere nello script di installazione le istruzioni per [applicare un codice Product Key per contratti multilicenza](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true), in modo che gli utenti non debbano attivare il software separatamente.

* (Facoltativo) Aggiornare il layout di rete per [controllare quando gli aggiornamenti del prodotto vengono messi a disposizione degli utenti finali e la loro provenienza](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true).

* (Facoltativo) Impostare i criteri del registro di sistema che influiscono sulla distribuzione di Visual Studio, ad esempio dove sono installati alcuni pacchetti condivisi con altre versioni o istanze, [dove vengono memorizzati i pacchetti nella cache](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) o [se i pacchetti vengono memorizzati nella cache](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true).

* (Facoltativo) Impostare Criteri di gruppo. È anche possibile [configurare Visual Studio per disabilitare i suggerimenti dei clienti](../ide/visual-studio-experience-improvement-program.md) nei singoli computer.

## <a name="step-3---deploy-updates"></a>Passaggio 3- Distribuire gli aggiornamenti

Usare la tecnologia di distribuzione desiderata per eseguire lo script nelle workstation di sviluppo di destinazione.

* [Aggiornare il percorso di rete con gli aggiornamenti più recenti](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) di Visual Studio eseguendo regolarmente il comando usato nel passaggio 1 in modo da aggiungere i componenti aggiornati.

  È possibile aggiornare Visual Studio usando uno script di aggiornamento. A tale scopo, usare il parametro [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) della riga di comando.

  È possibile distribuire Visual Studio aggiornamenti dal Windows Server Update Services o dal catalogo Microsoft Update con strumenti come System Center Gestione configurazione. Per altre informazioni, vedere [Applicazione degli aggiornamenti dell'amministratore.](applying-administrator-updates.md)

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Passaggio 4 - (facoltativo) Usare Visual Studio per verificare l'installazione

Sono stati resi disponibili diversi strumenti che consentono di [rilevare e gestire le istanze installate di Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) nei computer client.

## <a name="advanced-configuration"></a>Configurazione avanzata

Per impostazione predefinita, l Visual Studio installazione consente l'inclusione di tipi personalizzati nelle ricerche Bing dall'elenco errori F1 e dai collegamenti di codice. È possibile configurare Visual Studio per disabilitare il meccanismo di ricerca dall'inclusione di qualsiasi tipo di utente personalizzato modificando il valore della chiave del Registro di sistema seguente in base ai criteri:

**DWORD "PutCustomTypeInBingSearch" 0**

Il Registro di sistema si trova nella `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` directory dell'hive del Registro di sistema privato. Per istruzioni su come aprire l'hive del Registro di sistema, vedere modifica del Registro di sistema [per un'Visual Studio istanza di](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Abilitazione degli aggiornamenti dell'amministratore](enabling-administrator-updates.md)
* [Applicazione degli aggiornamenti dell'amministratore](applying-administrator-updates.md)
* [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Installare i certificati necessari per l'installazione offline di Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Importare o esportare configurazioni di installazione](import-export-installation-configurations.md)
* [Visual Studio Setup Archives](https://devblogs.microsoft.com/setup/tag/vs2017/) (Archivi di installazione di Visual Studio)
* [Visual Studio ciclo di vita e manutenzione del prodotto](/visualstudio/releases/2019/servicing/)
* [Impostazioni di caricamento automatico sincrono](../extensibility/synchronously-autoloaded-extensions.md)
