---
title: Novità di Visual Studio 2022 (anteprima)
titleSuffix: ''
description: Informazioni sulle nuove funzionalità della versione di anteprima di Visual Studio 2022.
ms.date: 09/17/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: ''
ms.prod: visual-studio-dev17
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 54e2c1984257b30587d4a9fc14deb75b4f07b916
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128432609"
---
# <a name="whats-new-in-visual-studio-2022-preview"></a>Novità di Visual Studio 2022 (anteprima)

**Aggiornamento per la versione 17.0 Preview 4.** Vedere [le note sulla versione |](/visualstudio/releases/2022/release-notes-preview/) Visualizzare la [roadmap del prodotto](/visualstudio/productinfo/vs-roadmap/)

>[!div class="button"]
>[Download Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022/)

Con Visual Studio, si ottengono sempre gli strumenti e i servizi migliori disponibili per qualsiasi sviluppatore, app e piattaforma. Se si usa Visual Studio per la prima volta o lo si usa da anni, la versione più recente, attualmente in anteprima, è molto simile.

## <a name="performance-improvements"></a>Miglioramenti delle prestazioni

Visual Studio 2022 è più veloce, più raggiungibile, più leggero ed è progettato sia per gli studenti che per quelli che compilano soluzioni su scala industriale.

### <a name="visual-studio-2022-is-64-bit"></a>Visual Studio 2022 è a 64 bit

Visual Studio 2022 in Windows è ora un'applicazione a 64 bit. Ciò significa che è possibile aprire, modificare, eseguire ed eseguire il debug anche delle soluzioni più grandi e complesse senza memoria insufficiente. Per altre informazioni, vedere i post di blog Visual Studio 2022 vision (Visione di Visual Studio [2022)](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/) [e Visual Studio 2022 Preview 1 (Anteprima 1).](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/)

### <a name="find-in-files-is-faster"></a>La ricerca nei file è più veloce

E, in [Visual Studio 2022 Preview 4,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)ci si è concentrati sul miglioramento delle prestazioni di diverse funzionalità chiave. Ad esempio, [la funzionalità Cerca nei file](find-in-files.md) è ora 3 volte più veloce durante la ricerca di soluzioni di grandi dimensioni, ad esempio [Orchard Core.](https://github.com/OrchardCMS/OrchardCore)

:::image type="content" source="media/vs-2022/find-files-faster.gif" alt-text="Animazione della funzionalità Cerca nei file durante la ricerca in una soluzione C# di grandi dimensioni tre volte più veloce rispetto alla versione precedente di Visual Studio.":::

## <a name="build-modern-apps"></a>Creare app moderne

Visual Studio 2022 semplifica e veloci la creazione di applicazioni moderne basate sul cloud con Azure. La nuova versione offre anche il supporto completo per .NET 6 e il relativo framework unificato per app Web, client e per dispositivi mobili per sviluppatori Windows e Mac. Inoltre, Visual Studio 2022 include un solido supporto per il carico di lavoro C++ con nuove funzionalità di produttività, strumenti C++20 e IntelliSense.

### <a name="better-dev-tools-for-c-and-net-and-hot-reload"></a>Strumenti di sviluppo migliori per C++, .NET e Ricaricamento rapido

[Visual Studio 2022 Preview 2](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-2-is-out/) include strumenti di sviluppo di app multipiattaforma migliori e la versione più recente degli strumenti di compilazione C++. È in corso anche l'aggiornamento **Ricaricamento rapido** in modo che sia possibile modificare i progetti C++ o .NET mentre l'applicazione è in esecuzione. Per altre informazioni, vedere il post di blog [**Speed up your .NET and C++ development with Ricaricamento rapido in Visual Studio 2022**](https://devblogs.microsoft.com/visualstudio/speed-up-your-dotnet-and-cplusplus-development-with-hot-reload-in-visual-studio-2022/) (Velocizzare lo sviluppo di .NET e C++ con Ricaricamento rapido in Visual Studio 2022).

### <a name="updates-for-blazor--razor-editors--hot-reload-for-aspnet"></a>Aggiornamenti per Blazor & editor Razor e Ricaricamento rapido per ASP.NET

E, una novità di [Visual Studio 2022 Preview 4,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)è disponibile un grande aggiornamento per gli editor Blazor e Razor e nuove funzionalità per **Ricaricamento rapido** in ASP.NET Core incluso Ricaricamento rapido quando si salva un file o quando si applicano modifiche ai file CSS in &mdash; tempo reale. 

:::image type="content" source="media/vs-2022/hot-reload-blazor-css-live.gif" alt-text="Animazione Ricaricamento rapido nelle app Razor e Blazor e nei file CSS in tempo reale.":::

## <a name="innovation-at-your-fingertips"></a>Innovazione a portata di mano

Da strumenti di collaborazione & in tempo reale a strumenti di produttività e informazioni dettagliate migliorati che si integrano facilmente con il flusso di lavoro giornaliero, Visual Studio 2022 include questo e altro ancora.

### <a name="multi-repo-support-with-git-in-the-ide"></a>Supporto di più repository con Git nell'IDE

Se si sono usati progetti ospitati in repository Git diversi, è possibile che si sia usato strumenti esterni o più istanze di Visual Studio per connettersi a essi. A partire da [Visual Studio 2022 Preview 3,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/)è possibile usare una singola soluzione con progetti in più repository e contribuire a tutti da una singola istanza di Visual Studio. Per altre informazioni, vedere il post di blog [**Multi-repo support in Visual Studio**](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) blog (Supporto di più Visual Studio repo).

### <a name="intellicode-improvements"></a>Miglioramenti di IntelliCode

* **Completamento riga intera:** in Visual Studio 2022, la funzionalità [IntelliCode](/visualstudio/intellicode/) può ora completare automaticamente il codice fino a un'intera riga alla volta. Per informazioni dettagliate, vedere il post di blog [**Type less, code more with IntelliCode completions**](https://devblogs.microsoft.com/visualstudio/type-less-code-more-with-intellicode-completions/) (Digitare meno codice con completamento IntelliCode).

* **Raccomandazioni** per azioni rapide: novità [di Visual Studio 2022 Preview 4,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)IntelliCode è ora in grado di individuare quando si sta eseguendo un'attività comune e consigliare l'azione rapida [appropriata,](quick-actions.md)completandolo proprio durante la digitazione. Per altre informazioni, vedere il post di blog Discover quick actions for common tasks as you type (Individuare azioni rapide per le attività comuni durante la [**digitazione) con IntelliCode.**](https://devblogs.microsoft.com/visualstudio/discover-quick-action-intellicode/)

## <a name="designing-for-everyone"></a>Progettazione per tutti

L'interfaccia utente verrà aggiornata per mantenere il flusso più aggiornato. Alcune delle modifiche sono tocchi sofisticati che modernizzano l'interfaccia utente o riducono il numero di persone.

### <a name="personalization-improvements"></a>Miglioramenti della personalizzazione

Una delle principali aree di interesse è rendere i Visual Studio più personalizzati e flessibili in modo da poter rendere l'IDE personalizzato. Ad esempio, [Visual Studio 2022 Preview 3](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/) offre la possibilità di eseguire la sincronizzazione con il tema Windows personalizzato. Pertanto, se è stata abilitata la funzionalità "luce notturna", Visual Studio anche questa funzionalità. Per altre informazioni, vedere il post di blog [**Personalizza Visual Studio 2022.**](https://devblogs.microsoft.com/visualstudio/personalize-your-visual-studio-2022/)

## <a name="whats-next"></a>Passaggi successivi

Per altre informazioni su ciò che si prevede di Visual Studio 2022? Per informazioni [**dettagliate,**](/visualstudio/productinfo/vs-roadmap/) vedere la pagina Roadmap Visual Studio post di blog sulla visione del [**2022.**](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)

## <a name="give-us-feedback"></a>Commenti e suggerimenti

È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.

* Se si vuole inviare un suggerimento per migliorare Visual Studio, è possibile usare lo strumento [Suggerisci una funzionalità](suggest-a-feature.md).

* Se si verifica un problema a causa del quale Visual Studio smette di rispondere, si arresta in modo anomalo o altri problemi di prestazioni, è possibile condividere facilmente i passaggi di riproduzione e i file di supporto con Microsoft usando lo strumento Segnala un [problema.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Vedi anche

* [Visual Studio 2022 Preview 4](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)
* [Visual Studio 2022 Preview 3](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/)
* [Visual Studio 2022 Preview 2](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-2-is-out/)
* [Visual Studio 2022 Preview 1](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/)
* [Visual Studio visione del 2022](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)
