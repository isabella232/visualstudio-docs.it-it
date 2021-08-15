---
title: Progettare XAML in Visual Studio e in Blend per Visual Studio
titleSuffix: ''
description: Informazioni sulle funzionalità degli strumenti di progettazione visiva in Visual Studio e Blend per Visual Studio per la creazione di interfaccia utente ed esperienze in XAML.
ms.custom: SEO-VS-2020
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 3367574ab52f02d3c6d4c8316eb6f616e5ca80540e5ed8874b8aad60280cd7a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351608"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Progettare XAML in Visual Studio e Blend per Visual Studio

Visual Studio e Blend per Visual Studio offrono entrambi strumenti visivi per la creazione con XAML di interfacce utente accattivanti e funzionalità multimediali avanzate per un'ampia varietà di tipi di app. I due ambienti di sviluppo integrato (IDE) condividono un set comune di funzionalità, tra cui un editor XAML (finestra di progettazione). Blend per Visual Studio, che supporta le piattaforme WPF e UWP, fornisce strumenti aggiuntivi per la progettazione degli stati di visualizzazione e la creazione di animazioni.

È possibile spostarsi tra Visual Studio e Blend per Visual Studio e persino aprire lo stesso progetto in entrambi gli IDE contemporaneamente. Le modifiche salvate in file XAML in un IDE possono essere applicate tramite ricaricamento automatico quando si passa all'altro IDE. È possibile controllare il comportamento di ricaricamento passando **a** Strumenti Opzioni Documenti di ambiente  >    >    >   in entrambi gli IDE.

## <a name="installation"></a>Installazione

- Per creare app WPF, installare il carico di lavoro **Sviluppo per desktop .NET** in Visual Studio. Verrà installato anche Blend per Visual Studio.

     ![Screenshot del carico di lavoro Sviluppo per desktop .NET dal Programma di installazione di Visual Studio](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Per creare app UWP, installare il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** in Visual Studio. Verrà installato anche Blend per Visual Studio.

     ![Screenshot del carico di lavoro Sviluppo della piattaforma Windows universali dal Programma di installazione di Visual Studio](../xaml-tools/media/uwp-workload.png)

- Per creare app Xamarin.Forms, installare il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con .NET** in Visual Studio. Blend per Visual Studio *non* viene installato, in quanto non supporta le app Xamarin.Forms.

     ![Screenshot del carico di lavoro Sviluppo di applicazioni per dispositivi mobili con .NET dal Programma di installazione di Visual Studio](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Funzionalità condivise

Per le attività di sviluppo più fondamentali, Visual Studio e Blend per Visual Studio condividono lo stesso set di finestre e funzionalità, con alcune piccole differenze. Ecco alcune delle caratteristiche principali:

- **IntelliSense:** Entrambi gli IDE supportano le funzionalità IntelliSense, ad esempio il completamento delle istruzioni.

- **Debug:** È possibile eseguire il debug [in](inspect-xaml-properties-while-debugging.md) Visual Studio [e Blend per Visual Studio](../xaml-tools/debug-xaml-in-blend.md), inclusa l'impostazione di punti di interruzione nel codice per eseguire il debug di un'app in esecuzione e l'uso di [Ricaricamento rapido per](../xaml-tools/xaml-hot-reload.md) modificare il codice XAML mentre l'app è in esecuzione. Per garantire un'esperienza di debug coerente con Visual Studio, Blend per Visual Studio include la maggior parte delle finestre di debug e le barre degli strumenti di Visual Studio.

- **Ricaricamento file:** È possibile modificare i file XAML in Visual Studio o Blend per Visual Studio. I file modificati che sono stati salvati vengono ricaricati automaticamente quando si passa da un IDE all'altro. È possibile controllare il comportamento di ricaricamento passando **a** Strumenti Opzioni Documenti di ambiente  >    >    >   in entrambi gli IDE.

- **Layout e impostazioni sincronizzati:** I layout della finestra dello strumento di personalizzazione della progettazione e le preferenze delle impostazioni per Visual Studio o Blend per Visual Studio vengono sincronizzati tra i dispositivi e le versioni quando si accede con lo stesso account di personalizzazione. Vedere [Sincronizzare le impostazioni tra più computer](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Funzionalità avanzate di Blend per Visual Studio

Per aumentare la produttività, è consigliabile usare Blend per Visual Studio per le attività seguenti. Queste sono le aree in cui Blend per Visual Studio offre più funzionalità rispetto alla finestra di progettazione di Visual Studio o al solo codice.

| Attività | Visual Studio | Blend per Visual Studio | Altre informazioni |
| - | - | - | - |
| **Progettare stati di visualizzazione** | Non esiste uno strumento che consenta di progettare stati di visualizzazione, è necessario crearli a livello di codice. | Usare gli strumenti di progettazione per modificare l'aspetto di un controllo in base al suo stato. | [Stati di visualizzazione](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Creare animazioni** |Non esiste alcuno strumento di progettazione per animazioni. È necessario crearle a livello di codice. Ciò richiede la comprensione del sistema di animazione e temporizzazione in WPF e ampia esperienza di codifica.|È possibile creare le animazioni visivamente e verificarne l'anteprima in Blend per Visual Studio. Questa procedura è più veloce e precisa della creazione delle animazioni nel codice. È possibile aggiungere trigger per gestire l'interazione con l'utente e passare al codice per aggiungere gestori eventi e altre funzionalità.|[Animare oggetti](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Trasformare le forme e il testo in tracciati per semplificarne la manipolazione**|Non supportata.|È possibile apportare modifiche o di maggiore impatto alle forme, quali rettangoli ed ellissi, convertendole in tracciati, che offrono un migliore controllo della modifica. È possibile modificare la forma dei tracciati o combinarli e q creare tracciati composti da più forme.<br /><br />È anche possibile convertire blocchi di testo in tracciati, in modo da modificarli come immagini vettoriali.|[Disegnare forme e tracciati](../xaml-tools/draw-shapes-and-paths.md)|
|**Modificare i controlli, i modelli e gli stili**|Richiede l'uso di codifica e conoscenza degli stili e dei modelli WPF.|Convertire un'immagine in un controllo.<br /><br />Usare gli strumenti di modifica dei modelli per modificare i controlli, gli stili e i modelli con pochi clic del mouse.<br /><br />È ad esempio possibile usare risorse di stile di Blend per Visual Studio per implementare controlli WPF comuni, quali pulsanti, caselle di riepilogo, barre di scorrimento, menu e così via, e modificarne il colore, lo stile o il modello sottostante direttamente in Blend per Visual Studio. È quindi possibile passare al codice per apportare eventuali ultimi ritocchi.|[Modificare lo stile degli oggetti](modify-the-style-of-objects-in-blend.md)|
|**Connettere l'interfaccia utente ai dati**|È possibile creare un'origine dati da risorse come database SQL Server, servizi WCF o servizi Web, oggetti oppure elenchi di SharePoint e quindi associare l'origine dati ai controlli dell'interfaccia utente.<br /><br />I dati della fase di progettazione devono essere creati manualmente per un'esperienza di progettazione interattiva.|Per le app .NET Framework, è possibile creare con facilità dati di esempio per la creazione di prototipi e il test. Passare ai dati dinamici quando si è pronti.<br /><br />Le funzionalità di generazione di dati di Blend per Visual Studio sono straordinarie. È possibile aggiungere nomi, numeri, URL e foto con facilità in pochi istanti e risparmiare molto tempo.<br /><br />Per i dati dinamici è possibile associare i controlli dell'interfaccia utente a un file XML o a qualsiasi origine dati CLR.|[Visualizzare dati](display-data-in-blend.md)|

Per altre informazioni sulla progettazione XAML avanzata, vedere [Creare un'interfaccia utente usando Blend per Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Panoramica di XAML](xaml-overview.md)
- [Panoramica di Blend per Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
