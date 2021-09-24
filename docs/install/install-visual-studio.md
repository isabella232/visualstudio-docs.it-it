---
title: Installare Visual Studio
titleSuffix: ''
description: Informazioni dettagliate sull'installazione di Visual Studio.
ms.date: 09/14/2021
ms.custom: vs-acquisition
ms.topic: conceptual
helpviewer_keywords:
- install Visual Studio
- dev15
- dev16
- dev17
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e9672bf47f72aed58ec46edddab83fde594a4494
ms.sourcegitcommit: da5efd7698e357c59ba9b7dbbcaaceb5d1cfade2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2021
ms.locfileid: "128329508"
---
# <a name="install-visual-studio"></a>Installare Visual Studio

::: moniker range="vs-2017"

In questo articolo viene presentato un nuovo modo per installare Visual Studio! In questa versione è stata semplificata la procedura che consente di scegliere e installare solo le funzionalità necessarie. È anche stato ridotto il footprint minimo di Visual Studio in modo che possa essere installato più rapidamente, limitando l'impatto sul sistema.

::: moniker-end

::: moniker range="vs-2019"

Benvenuti in Visual Studio 2019. In questa versione è molto semplice scegliere e installare solo le funzionalità necessarie. Inoltre, grazie alla riduzione del footprint minimo, l'installazione viene eseguita velocemente e con un minore impatto sul sistema.

::: moniker-end

::: moniker range=">=vs-2022"

Benvenuti in Visual Studio 2022 Preview! In questa versione è molto semplice scegliere e installare solo le funzionalità necessarie.

::: moniker-end

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Installare Visual Studio per Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2017"

Per altre informazioni sulle novità in questa versione, vedere le [note sulla versione](/visualstudio/releasenotes/vs2017-relnotes) Microsoft.

::: moniker-end

::: moniker range="vs-2019"

Per altre informazioni sulle novità in questa versione, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes/) Microsoft.

::: moniker-end

::: moniker range=">=vs-2022"

Per altre informazioni sulle altre novità di questa versione di anteprima, vedere le [note sulla versione](/visualstudio/releases/2022/release-notes-preview/) Microsoft.

::: moniker-end

Tutto pronto? Sarà illustrata una procedura dettagliata.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Passaggio 1: Verificare che il computer sia pronto per Visual Studio

Prima di iniziare l'installazione di Visual Studio:

::: moniker range="vs-2017"

1. Controllare i [requisiti di sistema](/visualstudio/productinfo/vs2017-system-requirements-vs) I requisiti consentono di verificare se il computer supporta Visual Studio 2017.

1. Applicare gli aggiornamenti più recenti di Windows. Tali aggiornamenti consentono di avere la certezza che nel computer siano presenti sia gli aggiornamenti di sicurezza più recenti sia i componenti di sistema necessari per Visual Studio.

1. Riavviare il computer. Il riavvio garantisce che eventuali installazioni o aggiornamenti in sospeso non ostacolino l'Visual Studio installazione.

1. Liberare spazio. Rimuovere i file e le applicazioni non necessari dall'unità di sistema eseguendo, ad esempio, l'app Pulizia disco.

::: moniker-end

::: moniker range="vs-2019"

1. Controllare i [requisiti di sistema](/visualstudio/releases/2019/system-requirements) I requisiti consentono di verificare se il computer supporta Visual Studio 2019.

1. Applicare gli aggiornamenti più recenti di Windows. Tali aggiornamenti consentono di avere la certezza che nel computer siano presenti sia gli aggiornamenti di sicurezza più recenti sia i componenti di sistema necessari per Visual Studio.

1. Riavviare il computer. Il riavvio garantisce che eventuali installazioni o aggiornamenti in sospeso non ostacolino l'Visual Studio installazione.

1. Liberare spazio. Rimuovere i file e le applicazioni non necessari dall'unità di sistema eseguendo, ad esempio, l'app Pulizia disco.

::: moniker-end

::: moniker range=">=vs-2022"

1. Controllare i [requisiti di sistema](/visualstudio/releases/2022/system-requirements) Questi requisiti consentono di sapere se il computer supporta Visual Studio 2022.

1. Applicare gli aggiornamenti più recenti di Windows. Tali aggiornamenti consentono di avere la certezza che nel computer siano presenti sia gli aggiornamenti di sicurezza più recenti sia i componenti di sistema necessari per Visual Studio.

1. Riavviare il computer. Il riavvio garantisce che eventuali installazioni o aggiornamenti in sospeso non ostacolino l'Visual Studio installazione.

1. Liberare spazio. Rimuovere i file e le applicazioni non necessari dall'unità di sistema eseguendo, ad esempio, l'app Pulizia disco.

::: moniker-end

::: moniker range="vs-2017"

Per domande sull'esecuzione di Visual Studio 2017 side by side con versioni precedenti di Visual Studio, vedere [Compatibilità con le versioni precedenti](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Per domande sull'esecuzione di versioni precedenti di Visual Studio side-by-side con Visual Studio 2019, vedere Visual Studio [2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility/).

::: moniker-end

::: moniker range=">=vs-2022"

È possibile installare Visual Studio 2022 side-by-side con le versioni precedenti. Per altre informazioni, vedere Visual Studio [2022 platform targeting and compatibility](/visualstudio/releases/2022/compatibility) (Distribuzione e compatibilità della piattaforma 2022) e Installare Visual Studio [versioni side-by-side.](install-visual-studio-versions-side-by-side.md?view=vs-2022&preserve-view=true)

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Passaggio 2: Scaricare Visual Studio

Scaricare quindi il file del programma di avvio automatico di Visual Studio.

::: moniker range="vs-2017"

Per ottenere un programma di avvio automatico Visual Studio 2017, vedere la Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/) delle versioni precedenti per informazioni dettagliate su come eseguire questa operazione.

::: moniker-end

::: moniker range="vs-2019"

A tale scopo, fare clic sul pulsante seguente, scegliere l'edizione di Visual Studio da scaricare, scegliere **Salva** e quindi scegliere **Apri cartella**.

 > [!div class="button"]
 > [Download di Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

::: moniker range=">=vs-2022"

A tale scopo, selezionare il pulsante seguente, scegliere l'edizione Visual Studio desiderata e quindi salvare nella **cartella Download.**

 > [!div class="button"]
 > [Download di Visual Studio](https://visualstudio.microsoft.com/vs/preview/#download-preview)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Passaggio 3: Installare il Programma di installazione di Visual Studio

Eseguire il file del programma di avvio automatico per installare il programma di installazione di Visual Studio. Questo nuovo programma di installazione semplificato include tutto ciò che occorre per installare e personalizzare Visual Studio.

1. Dalla cartella **Download** fare doppio clic sul file del programma di avvio automatico corrispondente o simile a uno dei file seguenti:

   * **vs_community.exe** per Visual Studio Community
   * **vs_professional.exe** per Visual Studio Professional
   * **vs_enterprise.exe** per Visual Studio Enterprise

   Se viene visualizzata una notifica di Controllo dell'account utente, scegliere **Sì**.

1. Verrà richiesto di confermare le [Condizioni di licenza](https://visualstudio.microsoft.com/license-terms/) e l'[Informativa sulla privacy](https://privacy.microsoft.com/privacystatement) di Microsoft. Scegliere **Continua**.

::: moniker range="<=vs-2019"

   ![Screenshot che mostra le condizioni di licenza e l'informativa sulla privacy Microsoft.](media/privacy-and-license-terms.png "Condizioni di licenza Microsoft e informativa sulla privacy")

::: moniker-end

::: moniker range=">=vs-2022"

   ![Screenshot che mostra le condizioni di licenza e l'informativa sulla privacy Microsoft.](../install/media/vs-2022/privacy-and-license-terms.png "Condizioni di licenza Microsoft e informativa sulla privacy")

::: moniker-end

## <a name="step-4---choose-workloads"></a>Passaggio 4: Scegliere i carichi di lavoro

Dopo aver installato il programma di installazione, è possibile usarlo per personalizzare l'installazione selezionando i set di funzionalità o carichi di lavoro desiderati. Ecco come.

::: moniker range="vs-2017"

1. Trovare il carico di lavoro desiderato nella **Programma di installazione di Visual Studio**.

   ![Screenshot che mostra la scheda Carichi di lavoro del Programma di installazione di Visual Studio.](../install/media/vs-installer-installing-workloads.png)

     Scegliere ad esempio il carico di lavoro "Sviluppo per desktop .NET". Include l'editor principale predefinito che offre supporto di base per la modifica del codice per oltre 20 linguaggi, la possibilità di aprire e modificare il codice da qualsiasi cartella senza che sia necessario un progetto e il controllo del codice sorgente integrato.

1. Dopo aver selezionato il carico di lavoro, scegliere **Installa**.

    A questo punto si apriranno diverse schermate di stato in cui sarà visualizzato l'avanzamento dell'installazione di Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Trovare il carico di lavoro desiderato nella **Programma di installazione di Visual Studio**.

   ![Screenshot che mostra la scheda Carichi di lavoro del Programma di installazione di Visual Studio.](../install/media/vs-2019/vs-installer-workloads.png)

     Scegliere ad esempio il carico di lavoro "Sviluppo ASP.NET e Web&quot;. Include l'editor principale predefinito che offre supporto di base per la modifica del codice per oltre 20 linguaggi, la possibilità di aprire e modificare il codice da qualsiasi cartella senza che sia necessario un progetto e il controllo del codice sorgente integrato.

1. Dopo aver selezionato il carico di lavoro, scegliere **Installa**.

    A questo punto si apriranno diverse schermate di stato in cui sarà visualizzato l'avanzamento dell'installazione di Visual Studio.

::: moniker-end

::: moniker range=&quot;>=vs-2022&quot;

1. Selezionare il carico di lavoro desiderato nel **Programma di installazione di Visual Studio**.

   ![Screenshot che mostra la scheda Carichi di lavoro del Programma di installazione di Visual Studio.](../install/media/vs-2022/vs-installer-workloads.png &quot;Installare i Visual Studio di lavoro")

     Esaminare i riepiloghi del carico di lavoro per decidere quale carico di lavoro supporta le funzionalità necessarie. Ad esempio, scegliere il carico di lavoro sviluppo **ASP.NET** e Web per modificare pagine Web ASP.NET con Web Live Preview o creare app Web reattive con Blazor oppure scegliere tra carichi di lavoro **Desktop & Mobile** per sviluppare app multipiattaforma con progetti C#o C++ che hanno come destinazione C++20.

1. Dopo aver scelto i carichi di lavoro desiderati, selezionare **Installa**.

    A questo punto si apriranno diverse schermate di stato in cui sarà visualizzato l'avanzamento dell'installazione di Visual Studio.

::: moniker-end

> [!TIP]
> In qualsiasi momento dopo l'installazione, è possibile installare i carichi di lavoro o i componenti che non sono stati installati inizialmente. Se è stato aperto Visual Studio, passare **a** Strumenti Ottieni strumenti e  >  **funzionalità,** che apre il Programma di installazione di Visual Studio. In caso contrario, **aprire Programma di installazione di Visual Studio** dal menu Start. Da qui, è possibile scegliere i carichi di lavoro o i componenti che si vogliono installare. Scegliere quindi **Modifica**.

## <a name="step-5---choose-individual-components-optional"></a>Passaggio 5: Scegliere i singoli componenti (facoltativo)

Se non si vuole usare la funzionalità Carichi di lavoro per personalizzare l'installazione di Visual Studio o aggiungere più componenti rispetto alle installazioni di un carico di lavoro, è possibile installare o aggiungere singoli componenti dalla scheda **Singoli** componenti. Scegliere quello che si vuole e quindi seguire le istruzioni.

::: moniker range="vs-2017"

  ![Screenshot che mostra la scheda Singoli componenti del Programma di installazione di Visual Studio.](media/vs-installer-installing-components.png "Installare Visual Studio singoli componenti")

::: moniker-end

::: moniker range="vs-2019"

  ![Screenshot che mostra la scheda Singoli componenti del Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-individual-components.png "Installare Visual Studio singoli componenti")

::: moniker-end

::: moniker range=">=vs-2022"

  ![Screenshot che mostra la scheda Singoli componenti del Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-individual-components.png "Installare Visual Studio singoli componenti")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Passaggio 6: Installare i Language Pack (facoltativo)

Per impostazione predefinita, alla prima esecuzione il programma di installazione tenta di trovare una corrispondenza con la lingua del sistema operativo. Per installare Visual Studio in un linguaggio specifico, scegliere la scheda **Language Pack** nel programma di installazione di Visual Studio e quindi seguire le istruzioni visualizzate.

::: moniker range="vs-2017"

  ![Screenshot che mostra la scheda Language Pack del Programma di installazione di Visual Studio.](media/vs-installer-installing-language-packs.png "Installare Visual Studio Language Pack")

::: moniker-end

::: moniker range="vs-2019"

  ![Screenshot che mostra la scheda Language Pack del Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-language-packs.png "Installare Visual Studio Language Pack")

::: moniker-end

::: moniker range=">=vs-2022"

  ![Screenshot che mostra la scheda Language Pack del Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-language-packs.png "Installare Visual Studio Language Pack")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Modificare la lingua del programma di installazione dalla riga di comando

::: moniker range="<=vs-2019"

Un altro modo per poter modificare la lingua predefinita consiste nell'eseguire il programma di installazione dalla riga di comando. Ad esempio, usare il comando seguente per forzare l'esecuzione in inglese del programma di installazione: `vs_installer.exe --locale en-US`. Il programma di installazione memorizza questa impostazione per l'esecuzione successiva. Il programma di installazione supporta i token delle lingue seguenti: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru e tr-tr.

::: moniker-end

::: moniker range=">=vs-2022"

Un altro modo per poter modificare la lingua predefinita consiste nell'eseguire il programma di installazione dalla riga di comando. Ad esempio, usare il comando seguente per forzare l'esecuzione in inglese del programma di installazione: `vs_installer.exe --locale en-US`. Il programma di installazione memorizza questa impostazione alla successiva esecuzione. Il programma di installazione supporta queste impostazioni locali della [lingua:](/visualstudio/install/use-command-line-parameters-to-install-visual-studio?view=vs-2022&preserve-view=true#list-of-language-locales)zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru e tr-tr.

::: moniker-end

## <a name="step-7---select-the-installation-location-optional"></a>Passaggio 7 - Selezionare il percorso di installazione (facoltativo)

::: moniker range="vs-2017"

**Novità della versione 15.7**: è ora possibile ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema. È possibile scegliere di spostare la Download Cache, i componenti condivisi, gli SDK e gli strumenti in unità diverse e mantenere Visual Studio nell'unità che lo esegue più rapidamente.

  ![Screenshot che mostra la scheda Percorsi di installazione del Programma di installazione di Visual Studio.](media/installation-options-by-location.png "Modificare il percorso di installazione")

::: moniker-end

::: moniker range="vs-2019"

È possibile ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema. È possibile scegliere di spostare la Download Cache, i componenti condivisi, gli SDK e gli strumenti in unità diverse e mantenere Visual Studio nell'unità che lo esegue più rapidamente.

  ![Screenshot che mostra la scheda Percorsi di installazione del Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-installation-locations.png "Selezionare il percorso di installazione")

::: moniker-end

::: moniker range=">=vs-2022"

È possibile ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema. Per altre informazioni, vedere Selezionare [i percorsi di installazione.](change-installation-locations.md)

  ![Screenshot che mostra la scheda Percorsi di installazione del Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-installation-locations.png "Selezionare il percorso di installazione")

::: moniker-end

> [!IMPORTANT]
> È possibile selezionare un'unità diversa per **l Visual Studio IDE** o **la download cache** solo quando si installa per la prima volta Visual Studio. Se Visual Studio è già stato installato e si vuole modificare l'unità, è necessario disinstallarlo e quindi reinstallarlo.
>
> Se è stato installato Visual Studio nel computer in precedenza, non sarà possibile modificare il percorso componenti **condivisi,** strumenti e SDK e verrà visualizzato in grigio. Questo percorso è condiviso da tutte le installazioni di Visual Studio.

## <a name="step-8---start-developing"></a>Passaggio 8: Avviare lo sviluppo

::: moniker range="vs-2017"

1. Al termine dell'installazione di Visual Studio, fare clic sul pulsante **Avvia** per iniziare a sviluppare con Visual Studio.

1. Scegliere **File** e quindi scegliere **Nuovo progetto**.

1. Selezionare un tipo di progetto.

   Ad esempio, per [compilare un'app C++](/cpp/get-started/tutorial-console-cpp), scegliere **Installati**, espandere **Visual C++** e scegliere il tipo di progetto C++ che si vuole compilare.

   Per [compilare un'app C#](../get-started/csharp/tutorial-console.md), scegliere **Installati**, espandere **Visual C#** e scegliere il tipo di progetto C# che si vuole compilare.

::: moniker-end

::: moniker range="vs-2019"

1. Dopo Visual Studio'installazione, selezionare il **pulsante Avvia** per iniziare a sviluppare con Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

1. Nella casella di ricerca immettere il tipo di app da creare per visualizzare un elenco dei modelli disponibili. L'elenco dei modelli dipende dai carichi di lavoro scelti durante l'installazione. Per visualizzare modelli diversi, è possibile scegliere carichi di lavoro differenti.

   È anche possibile filtrare la ricerca in base a un linguaggio di programmazione specifico usando l'elenco a discesa **Linguaggio** e applicare filtri usando gli elenchi **Piattaforma** e **Tipo di progetto**.

1. Il nuovo progetto verrà aperto in Visual Studio e sarà possibile iniziare a scrivere codice.

::: moniker-end

::: moniker range=">=vs-2022"

1. Al termine dell Visual Studio installazione, selezionare il **pulsante Avvia** per iniziare a sviluppare con Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

1. Nella casella di ricerca dei modelli immettere il tipo di app che si vuole creare per visualizzare un elenco dei modelli disponibili. L'elenco dei modelli dipende dai carichi di lavoro scelti durante l'installazione. Per visualizzare modelli diversi, è possibile scegliere carichi di lavoro differenti.

   È anche possibile filtrare la ricerca in base a un linguaggio di programmazione specifico usando l'elenco a discesa **Linguaggio** e applicare filtri usando gli elenchi **Piattaforma** e **Tipo di progetto**.

1. Il nuovo progetto verrà aperto in Visual Studio e sarà possibile iniziare a scrivere codice.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Aggiornare Visual Studio](update-visual-studio.md)
* [Modificare Visual Studio](modify-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Installare Visual Studio per Mac](/visualstudio/mac/installation)
