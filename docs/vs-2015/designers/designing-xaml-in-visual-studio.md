---
title: Progettazione di XAML
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a1c58ca9d567db88fb8267d56e071c11ba8aef27
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870229"
---
# <a name="designing-xaml-in-visual-studio"></a>Progettazione di XAML in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio e Blend per Visual Studio offrono strumenti visivi per la creazione di interfacce utente accattivanti e funzionalità multimediali avanzate per app per Windows desktop, Web, [Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx)e [Windows Store](http://msdn.microsoft.com/library/windows/apps/jj129478.aspx) basate su XAML. Entrambi condividono un set comune di finestre di progettazione e degli strumenti e un editor XAML, ma Blend per Visual Studio offre strumenti di progettazione aggiuntive per attività più avanzate quali animazioni e comportamenti.

## <a name="choosing-the-right-tool"></a>Scegliere lo strumento giusto
 La scelta degli strumenti di progettazione dipende in larga misura dal bagaglio di competenze. Se si è più orientati al codice, è possibile scrivere codice XAML in Visual Studio per eseguire attività di progettazione anche avanzata. Se si è più orientati alla progettazione, Blend per Visual Studio consente di eseguire attività avanzate senza scrivere codice.

 È possibile passare da Visual Studio e Blend per Visual Studio ed è possibile persino aprire lo stesso progetto contemporaneamente. Le modifiche apportate al file XAML in un IDE possono essere applicate tramite ricarica automatica quando si passa ad altri IDE. È possibile controllare il ricaricamento tramite le opzioni nella finestra di dialogo **Strumenti**, **Opzioni** nell'IDE.

### <a name="shared-capabilities"></a>Funzionalità condivise
 Per attività più semplici l'IDE per Visual Studio e Blend per Visual Studio condividono lo stesso set di finestre e funzionalità, con alcune piccole differenze. Alcune delle principali caratteristiche includono:

-   **Un'interfaccia utente coerente:** è possibile progettare le applicazioni all'interno del contesto familiare dell'interfaccia utente di Visual Studio. Ciò rende più produttivo e piacevole il passaggio da un IDE all'altro. Blend per Visual Studio usa il tema scuro di Visual Studio che consente di concentrarsi sul contenuto che si sta progettando migliorando il contrasto tra il contenuto e l'interfaccia utente. Vedere [Creating a UI by using XAML Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md) (Creazione di un'interfaccia utente tramite la finestra di progettazione XAML).

     ![IDE per Blend per Visual Studio ](../designers/media/blendide.png "BlendIDE")

-   **IntelliSense XAML:** entrambi gli IDE supportano tutte le funzionalità comuni che ci si aspettano da IntelliSense, tra cui completamento istruzioni, supporto di operazioni quali aggiunta di commenti e formattazione di codice e possibilità di spostarsi tra risorse, binding e codice.

-   **Funzionalità di debug di base:** è ora possibile eseguire il debug in Blend, con la possibilità di usare l'impostazione di punti di interruzione nel codice per il debug dell'app in esecuzione. Per garantire un'esperienza di debug coerente con Visual Studio, Blend per Visual Studio include la maggior parte delle finestre di debug e le barre degli strumenti di Visual Studio. Avanzate funzionalità di debug, ad esempio la diagnostica e l’analisi del codice sono disponibili solo in Visual Studio. Vedere [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md).

-   **Esperienza di ricaricamento file:** è possibile modificare i file XAML in Blend per Visual Studio o in Visual Studio e ricaricare automaticamente i file modificati quando si passa dall'uno all'altro. Per ridurre al minimo le interruzioni di flusso di lavoro, è ora possibile impostare le preferenze di ricaricamento file nella finestra Ricarica file.

     ![Esperienza di ricaricamento file](../designers/media/blendfilereload.png "BlendFileReload")

-   **Impostazioni e layout sincronizzati:** i layout personalizzati consentono di salvare e applicare personalizzazioni di layout delle finestre degli strumenti. Quando si effettua l’accesso con lo stesso account Microsoft, Visual Studio sincronizzerà queste personalizzazioni e le preferenze per Visual Studio e Blend per Visual Studio tra più computer. Vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

-   **Esplora soluzioni comune:** Esplora soluzioni offre una visualizzazione organizzata dei progetti e dei relativi file, nonché l'accesso immediato ai comandi associati. Con Esplora soluzioni è più facile lavorare con progetti di grandi imprese. Vedere [Solutions and Projects](../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)

-   **Team Explorer:** con Team Explorer è possibile gestire i progetti con repository GIT o TFS per agevolare la collaborazione tra team. Vedere [Lavorare in Team Explorer](http://msdn.microsoft.com/library/fd7a5cf7-7916-4fa0-b5e6-5a83cf377a02).

-   **NuGet:** è possibile gestire pacchetti NuGet in Visual Studio e in Blend per Visual Studio. NuGet è una gestione pacchetti per .NET Framework che semplifica l'installazione e la rimozione dei pacchetti da una soluzione.

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Funzionalità avanzate di Blend per Visual Studio
 Per aumentare la produttività, è consigliabile usare Blend per Visual Studio per le attività seguenti. Queste sono le aree in cui Blend per Visual Studio offre maggiore velocità e funzionalità rispetto alla finestra di progettazione di Visual Studio o al solo codice.

|A|Visual Studio|Blend per Visual Studio|Altre informazioni|
|--------|-------------------|-----------------------------|----------------------|
|**Creare animazioni**|Non esiste alcuno strumento di progettazione per animazioni. È necessario crearle a livello di codice. Ciò richiede la comprensione del sistema di animazione e temporizzazione in WPF e ampia esperienza di codifica.|È possibile creare le animazioni visivamente e verificarne l'anteprima in Blend per Visual Studio. Questa procedura è più veloce e precisa della creazione delle animazioni nel codice. È possibile aggiungere trigger per gestire l'interazione con l'utente e passare al codice per aggiungere gestori eventi e altre funzionalità.|[Animare oggetti](../designers/animate-objects-in-xaml-designer.md)|
|**Trasformare le forme e il testo in tracciati per semplificarne la manipolazione**|Non supportato.|È possibile apportare modifiche o di maggiore impatto alle forme, quali rettangoli ed ellissi, convertendole in tracciati, che offrono un migliore controllo della modifica.  È possibile modificare la forma dei tracciati o combinarli e q creare tracciati composti da più forme.<br /><br /> È anche possibile convertire blocchi di testo in tracciati, in modo da modificarli come immagini vettoriali.|[Disegnare forme e tracciati](../designers/draw-shapes-and-paths.md)|
|**Aggiungere interattività alle progettazioni dell'interfaccia utente**|Richiede il codice C#, Visual Basic o C++.|Trascinare e rilasciare i comportamenti sui controlli per aggiungere interattività alle progettazioni statiche. I comportamenti sono frammenti di codice pronti per l'uso che includono funzionalità quali il trascinamento, lo zoom e le modifiche dello stato visivo. È possibile scegliere i comportamenti da insieme in continua crescita oppure creare comportamenti personalizzati.<br /><br /> È quindi possibile personalizzare ogni comportamento modificandone le proprietà in Blend per Visual Studio oppure aggiungendo gestori eventi nel codice.|[Inserire i controlli e modificarne il comportamento](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|
|**Usare le immagini di Adobe**|Non supportato.|È possibile importare immagini di Adobe FXG, PhotoShop o Illustrator e implementare l'interfaccia utente in Blend per Visual Studio.|[Inserire immagini, video e clip audio](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|
|**Modificare controlli, modelli e stili**|Richiede l'uso di codifica e conoscenza degli stili e dei modelli WPF.|Convertire un'immagine in un controllo.<br /><br /> Usare gli strumenti di modifica dei modelli per modificare i controlli, gli stili e i modelli con pochi clic del mouse.<br /><br /> È ad esempio possibile usare risorse di stile di Blend per Visual Studio per implementare controlli WPF comuni, quali pulsanti, caselle di riepilogo, barre di scorrimento, menu e così via, e modificarne il colore, lo stile o il modello sottostante direttamente in Blend per Visual Studio. È quindi possibile passare al codice per apportare eventuali ultimi ritocchi.|[Modificare lo stile degli oggetti](../designers/modify-the-style-of-objects-in-blend.md)|
|**Connettere l'interfaccia utente ai dati**|È possibile creare un'origine dati da risorse quali database SQL Server, servizi WCF o servizi Web, oggetti oppure elenchi di SharePoint e associare l'origine dati ai controlli dell'interfaccia utente.<br /><br /> I dati della fase di progettazione devono essere creati manualmente per un'esperienza di progettazione interattiva.|Creare con facilità dati di esempio per la creazione di prototipi e il test. Passare ai dati dinamici quando si è pronti.<br /><br /> Le funzionalità di generazione di dati di Blend per Visual Studio sono straordinarie. È possibile aggiungere nomi, numeri, URL e foto con facilità in pochi istanti e risparmiare molto tempo.<br /><br /> Per i dati dinamici è possibile associare i controlli dell'interfaccia utente a un file XML o a qualsiasi origine dati CLR.|[Visualizzare i dati](../designers/display-data-in-blend.md)|

 Per altre informazioni sulla finestra di progettazione XAML, vedere . [Creazione di un'interfaccia utente usando Blend per Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
