---
title: "Procedura: diagnosticare le prestazioni dell'estensione | Microsoft Docs"
description: Visual Studio notifica agli utenti le estensioni lente. Informazioni sul modo in cui viene calcolato l'effetto sulle estensioni e sul modo in cui è possibile analizzare l'effetto dell'estensione localmente
ms.custom: SEO-VS-2020
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 03721f2aedd231dd9d4c4edaadf5eeb3a89389c2
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994199"
---
# <a name="measuring-extension-impact-in-startup"></a>Misurazione dell'effetto dell'estensione all'avvio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Concentrarsi sulle prestazioni dell'estensione in Visual Studio 2017

In base ai suggerimenti dei clienti, una delle aree di interesse per la versione di Visual Studio 2017 è stata l'avvio e le prestazioni di caricamento della soluzione. Il team di Visual Studio Platform si è impegnato a migliorare le prestazioni di avvio e di caricamento delle soluzioni. In generale, le misure suggeriscono che le estensioni installate possono anche avere un impatto significativo su tali scenari.

Per consentire agli utenti di comprendere questo impatto, è stata aggiunta una nuova funzionalità di Visual Studio per notificare agli utenti le estensioni lente. In alcuni casi, Visual Studio rileva una nuova estensione che rallenta il caricamento o l'avvio della soluzione. Quando viene rilevato un rallentamento, gli utenti visualizzeranno una notifica nell'IDE che punta alla nuova finestra di dialogo "Gestisci prestazioni di Visual Studio". È anche possibile accedere a questa finestra di dialogo dal menu? per sfogliare le estensioni rilevate in precedenza.

![Gestisci prestazioni di Visual Studio](media/manage-performance.png)

Questo documento mira a aiutare gli sviluppatori di estensioni, descrivendo il modo in cui viene calcolato l'effetto sulle estensioni. Questo documento descrive anche il modo in cui l'effetto sull'estensione può essere analizzato localmente. L'analisi locale degli effetti dell'estensione determinerà se un'estensione può essere visualizzata come un'estensione con conseguenze sulle prestazioni.

> [!NOTE]
> Questo documento è incentrato sull'effetto delle estensioni all'avvio e al caricamento della soluzione. Le estensioni influire inoltre sulle prestazioni di Visual Studio quando provocano la mancata risposta dell'interfaccia utente. Per altre informazioni su questo argomento, vedere [procedura: diagnosticare i ritardi dell'interfaccia utente causati da estensioni](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Come le estensioni possono avere un effetto sull'avvio

Uno dei modi più comuni per le estensioni per influisca sulle prestazioni di avvio è la scelta di caricare automaticamente in uno dei contesti dell'interfaccia utente di avvio noti, ad esempio NoSolutionExists o ShellInitialized. Questi contesti dell'interfaccia utente vengono attivati durante l'avvio. Tutti i pacchetti che includono l' `ProvideAutoLoad` attributo nella definizione con tali contesti verranno caricati e inizializzati in quel momento.

Quando si misura l'effetto di un'estensione, si concentra principalmente sul tempo impiegato dalle estensioni che scelgono di caricarsi automaticamente nei contesti descritti in precedenza. I tempi misurati includono ma non sono limitati a:

* Caricamento degli assembly di estensione per i pacchetti sincroni
* Tempo impiegato nel costruttore della classe del pacchetto per i pacchetti sincroni
* Tempo impiegato per il metodo di inizializzazione (o di sito) del pacchetto per i pacchetti sincroni
* Per i pacchetti asincroni, le operazioni precedenti vengono eseguite sul thread in background.  Di conseguenza, le operazioni vengono escluse dal monitoraggio.
* Tempo impiegato in tutte le operazioni asincrone pianificate durante l'inizializzazione del pacchetto per l'esecuzione sul thread principale
* Tempo impiegato nei gestori eventi, in particolare l'attivazione del contesto inizializzata della shell o la modifica dello stato di zombie Shell
* A partire da Visual Studio 2017 Update 3, viene avviato anche il monitoraggio del tempo dedicato alle chiamate inattive prima dell'inizializzazione della shell. Anche le operazioni lunghe nei gestori inattivi generano IDE che non rispondono e contribuiscono al tempo di avvio percepito dall'utente.

Sono state aggiunte molte funzionalità a partire da Visual Studio 2015. Queste funzionalità consentono di rimuovere la necessità di caricare automaticamente i pacchetti. Le funzionalità rimandano inoltre la necessità di caricare i pacchetti in casi più specifici. In questi casi sono inclusi esempi in cui gli utenti sono più sicuri di utilizzare l'estensione o di ridurre l'effetto di un'estensione quando vengono caricati automaticamente.

Per ulteriori informazioni su queste funzionalità, vedere i documenti seguenti:

[Contesti dell'interfaccia utente basati su regole](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un motore basato su regole più completo basato sui contesti dell'interfaccia utente consente di creare contesti personalizzati in base ai tipi di progetto, alle versioni e agli attributi. I contesti personalizzati possono essere utilizzati per caricare un pacchetto in scenari più specifici. Questi scenari specifici includono la presenza di un progetto con una funzionalità specifica anziché l'avvio. I contesti personalizzati consentono inoltre [di associare la visibilità del comando a un contesto personalizzato](visibilityconstraints-element.md) basato sui componenti del progetto o su altri termini disponibili. Questa funzionalità Elimina la necessità di caricare un pacchetto per registrare un gestore di query sullo stato del comando.

[Supporto](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)dei pacchetti asincroni: la nuova classe base AsyncPackage in Visual Studio 2015 consente il caricamento in background dei pacchetti di Visual Studio in modo asincrono se il caricamento del pacchetto è stato richiesto da un attributo di caricamento automatico o da una query del servizio asincrona. Questo caricamento in background consente all'IDE di rimanere reattivo. L'IDE risponde anche quando l'estensione viene inizializzata in background e gli scenari critici come l'avvio e il caricamento della soluzione non saranno interessati.

[Servizi asincroni](how-to-provide-an-asynchronous-visual-studio-service.md): grazie al supporto asincrono dei pacchetti, è stato aggiunto anche il supporto per l'esecuzione di query dei servizi in modo asincrono e la possibilità di registrare servizi asincroni. In particolare, stiamo lavorando alla conversione dei servizi di base di Visual Studio per supportare la query asincrona in modo che la maggior parte del lavoro in una query asincrona avvenga nei thread in background. SComponentModel (host MEF di Visual Studio) è uno dei principali servizi che ora supporta la query asincrona per consentire alle estensioni di supportare completamente il caricamento asincrono.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Riduzione dell'effetto delle estensioni caricate automaticamente

Se è ancora necessario caricare automaticamente un pacchetto all'avvio, è importante ridurre al minimo le operazioni eseguite durante l'inizializzazione del pacchetto. Riducendo al minimo il lavoro di inizializzazione dei pacchetti si riducono le probabilità che l'estensione abbia effetto sull'avvio.

Di seguito sono riportati alcuni esempi che potrebbero compromettere l'inizializzazione dei pacchetti:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Utilizzo del caricamento sincrono dei pacchetti anziché del caricamento asincrono del pacchetto

Poiché per impostazione predefinita i pacchetti sincroni vengono caricati nel thread principale, si consiglia ai proprietari di estensioni con pacchetti caricati automaticamente di usare la classe di base del pacchetto asincrona come indicato in precedenza. La modifica di un pacchetto caricato automaticamente per supportare il caricamento asincrono renderà più semplice la risoluzione degli altri problemi riportati di seguito.

### <a name="synchronous-filenetwork-io-requests"></a>Richieste di i/o file/rete sincrona

Idealmente, qualsiasi richiesta di i/o di file sincrono o di rete deve essere evitata nel thread principale. Il loro effetto dipenderà dallo stato del computer e in alcuni casi può bloccarsi per lunghi periodi di tempo.

L'uso del caricamento asincrono del pacchetto e delle API di i/o asincrone deve assicurarsi che l'inizializzazione dei pacchetti non blocchi il thread principale in tali casi. Gli utenti possono anche continuare a interagire con Visual Studio mentre le richieste di I/O vengono effettuate in background.

### <a name="early-initialization-of-services-components"></a>Inizializzazione iniziale dei servizi, componenti

Uno dei modelli comuni nell'inizializzazione del pacchetto consiste nell'inizializzare i servizi usati da o forniti da tale pacchetto nel pacchetto `constructor` o nel `initialize` metodo. Sebbene ciò assicuri che i servizi siano pronti per l'uso, può anche aggiungere costi superflui al caricamento del pacchetto se tali servizi non vengono usati immediatamente. È invece consigliabile inizializzare tali servizi su richiesta per ridurre al minimo il lavoro svolto nell'inizializzazione del pacchetto.

Per i servizi globali forniti da un pacchetto, è possibile utilizzare `AddService` metodi che accettano una funzione per inizializzare in modo differito il servizio solo quando viene richiesto da un componente. Per i servizi utilizzati all'interno del pacchetto, è possibile utilizzare Lazy \<T> o AsyncLazy \<T> per assicurarsi che i servizi vengano inizializzati/sottoposti a query al primo utilizzo.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Misurazione dell'effetto delle estensioni caricate automaticamente tramite il log attività

A partire da Visual Studio 2017 Update 3, il log attività di Visual Studio conterrà le voci per l'impatto sulle prestazioni dei pacchetti durante l'avvio e il caricamento della soluzione. Per visualizzare queste misurazioni, è necessario aprire Visual Studio con l'opzione/log e aprire *ActivityLog.xml* file.

Nel log attività, le voci saranno incluse nell'origine "Gestisci prestazioni di Visual Studio" e sarà simile all'esempio seguente:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Questo esempio mostra che un pacchetto con GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" ha dedicato 2008 MS all'avvio di Visual Studio. Si noti che Visual Studio considera il costo di primo livello come il numero principale durante il calcolo dell'impatto di un pacchetto, poiché si tratta del risparmio visualizzato dagli utenti quando disabilitano l'estensione per il pacchetto.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Misurazione dell'effetto delle estensioni caricate automaticamente con PerfView

Mentre l'analisi del codice consente di identificare i percorsi di codice che possono rallentare l'inizializzazione del pacchetto, è anche possibile usare la traccia usando applicazioni come PerfView per comprendere l'impatto del carico di un pacchetto nell'avvio di Visual Studio.

PerfView è uno strumento di traccia a livello di sistema. Questo strumento consente di comprendere i percorsi sensibili in un'applicazione a causa dell'utilizzo della CPU o delle chiamate di sistema bloccanti. Di seguito è riportato un esempio rapido di analisi di un'estensione di esempio tramite PerfView disponibile nell' [area download Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Codice di esempio:**

Questo esempio è basato sul codice di esempio riportato di seguito, progettato per mostrare casi di ritardo comuni:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Registrazione di una traccia con PerfView:**

Dopo aver configurato l'ambiente di Visual Studio con l'estensione installata, è possibile registrare una traccia dell'avvio aprendo PerfView e aprendo la finestra di dialogo **Collect** dal menu **Collect** .

![menu raccolta PerfView](media/perfview-collect-menu.png)

Le opzioni predefinite forniranno stack di chiamate per l'utilizzo della CPU, ma poiché si è interessati a bloccare il tempo, è necessario abilitare anche gli stack **temporali dei thread** . Quando le impostazioni sono pronte, è possibile fare clic su **Avvia raccolta** e quindi aprire Visual Studio dopo l'avvio della registrazione.

Prima di arrestare la raccolta, è necessario assicurarsi che Visual Studio sia completamente inizializzato, che la finestra principale sia completamente visibile e che l'estensione includa le parti dell'interfaccia utente visualizzate automaticamente, anch ' esse visibili. Quando Visual Studio viene caricato completamente e viene inizializzata l'estensione, è possibile arrestare la registrazione per analizzare la traccia.

**Analisi di una traccia con PerfView:**

Al termine della registrazione, PerfView apre automaticamente la traccia ed espande le opzioni.

Ai fini di questo esempio, si è interessati principalmente alla visualizzazione degli **stack temporali del thread** che è possibile trovare sotto il **gruppo Advanced**. Questa vista Mostra il tempo totale impiegato in un thread da un metodo che include sia il tempo della CPU che il tempo di blocco, ad esempio l'i/o del disco o l'attesa di handle.

 ![stack temporali thread](media/perfview-thread-time-stacks.png)

 Durante l'apertura della visualizzazione **stack tempo thread** , è necessario scegliere il processo **devenv** per avviare l'analisi.

In PerfView sono disponibili istruzioni dettagliate su come leggere gli stack temporali del thread nel proprio menu della Guida per un'analisi più dettagliata. Ai fini di questo esempio, si vuole filtrare ulteriormente questa visualizzazione includendo solo gli stack con il nome del modulo dei pacchetti e il thread di avvio.

1. Impostare **GroupPats** su testo vuoto per rimuovere tutti i raggruppamenti aggiunti per impostazione predefinita.
2. Impostare **IncPats** in modo da includere parte del nome dell'assembly e del thread di avvio oltre al filtro di processo esistente. In questo caso, deve essere **devenv; Thread di avvio; MakeVsSlowExtension**.

A questo punto, la vista mostrerà solo i costi associati agli assembly correlati all'estensione. In questa visualizzazione, qualsiasi ora elencata sotto la colonna **Inc (costo inclusivo)** del thread di avvio è correlata all'estensione filtrata e avrà un impatto sull'avvio.

Per l'esempio precedente, alcuni stack di chiamate interessanti sono:

1. IO usando `System.IO` la classe: Sebbene il costo inclusivo di questi frame potrebbe non essere troppo costoso nella traccia, è possibile che si verifichi un problema perché la velocità di i/o dei file varia da computer a computer.

   ![frame io di sistema](media/perfview-system-io-frames.png)

2. Chiamate di blocco in attesa di altre operazioni asincrone: in questo caso, il tempo inclusivo rappresenterà il tempo in cui il thread principale è bloccato al completamento del lavoro asincrono.

   ![blocco di frame di chiamata](media/perfview-blocking-call-frames.png)

Una delle altre viste della traccia che saranno utili per determinare l'effetto saranno gli **stack di caricamento dell'immagine**. È possibile applicare gli stessi filtri applicati alla visualizzazione **stack tempo thread** e individuare tutti gli assembly caricati a causa del codice eseguito dal pacchetto caricato automaticamente.

È importante ridurre al minimo il numero di assembly caricati all'interno di una routine di inizializzazione del pacchetto, in quanto ogni assembly aggiuntivo implica operazioni di I/O su disco aggiuntive che possono rallentare notevolmente l'avvio in computer più lenti.

## <a name="summary"></a>Riepilogo

L'avvio di Visual Studio è una delle aree in cui si ricevono continuamente commenti. L'obiettivo indicato in precedenza è che tutti gli utenti hanno un'esperienza di avvio coerente indipendentemente dai componenti e dalle estensioni installate. Microsoft vuole collaborare con i proprietari delle estensioni per aiutarli a raggiungere questo obiettivo. Le linee guida riportate sopra dovrebbero essere utili per comprendere l'effetto di un'estensione all'avvio ed evitare la necessità di caricarli automaticamente o di caricarli in modo asincrono per ridurre al minimo l'effetto sulla produttività degli utenti.
