---
title: "Procedura: Diagnosticare le prestazioni dell'estensione| Microsoft Docs"
description: Visual Studio notifica agli utenti la lentezza delle estensioni. Informazioni su come viene calcolato l'impatto dell'estensione e su come è possibile analizzare l'impatto dell'estensione in locale.
ms.custom: SEO-VS-2020
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- bertaygu
ms.openlocfilehash: a71f0c9b22c8af137ec59e6b53e3bf5aca56442cbb0e2df6b7c546b9b4fb8b87
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376581"
---
# <a name="measuring-extension-impact-in-startup"></a>Misurazione dell'impatto dell'estensione all'avvio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Concentrarsi sulle prestazioni dell'estensione Visual Studio 2017

In base ai commenti e suggerimenti dei clienti, una delle aree di interesse per Visual Studio versione 2017 è stata l'avvio e le prestazioni di caricamento delle soluzioni. In qualità di team Visual Studio piattaforma, microsoft ha lavorato per migliorare le prestazioni di avvio e caricamento delle soluzioni. In generale, le misurazioni suggeriscono che anche le estensioni installate possono avere un notevole impatto su tali scenari.

Per aiutare gli utenti a comprendere questo impatto, è stata aggiunta una nuova funzionalità in Visual Studio per informare gli utenti di estensioni lente. In alcuni Visual Studio rileva una nuova estensione che rallenta il caricamento o l'avvio della soluzione. Quando viene rilevato un rallentamento, gli utenti visualizzano una notifica nell'IDE che punta alla nuova finestra di dialogo "Gestisci prestazioni Visual Studio prestazioni". È sempre possibile accedere a questa finestra di dialogo dal menu ? per esplorare le estensioni rilevate in precedenza.

![gestire le Visual Studio prestazioni](media/manage-performance.png)

Questo documento ha lo scopo di aiutare gli sviluppatori di estensioni descrivendo come viene calcolato l'impatto dell'estensione. Questo documento descrive anche come l'impatto sulle estensioni può essere analizzato in locale. L'analisi locale dell'impatto dell'estensione determinerà se un'estensione può essere visualizzata come un'estensione che influisce sulle prestazioni.

> [!NOTE]
> Questo documento è in particolare sull'impatto delle estensioni sull'avvio e sul caricamento della soluzione. Le estensioni influiscono Visual Studio prestazioni quando causano il fatto che l'interfaccia utente non risponde. Per altre informazioni su questo argomento, vedere [Procedura: Diagnosticare i ritardi dell'interfaccia utente causati dalle estensioni.](how-to-diagnose-ui-delays-caused-by-extensions.md)

## <a name="how-extensions-can-impact-startup"></a>Come le estensioni possono influire sull'avvio

Uno dei modi più comuni per le estensioni per influire sulle prestazioni di avvio è scegliere di caricare automaticamente in uno dei contesti noti dell'interfaccia utente di avvio, ad esempio NoSolutionExists o ShellInitialized. Questi contesti dell'interfaccia utente vengono attivati durante l'avvio. Tutti i pacchetti che includono l'attributo nella relativa definizione con tali contesti verranno `ProvideAutoLoad` caricati e inizializzati in quel momento.

Quando si misura l'impatto di un'estensione, ci si concentra principalmente sul tempo dedicato alle estensioni che scelgono di caricare automaticamente nei contesti precedenti. I tempi misurati includono, ma non sono limitati a:

* Caricamento di assembly di estensione per pacchetti sincroni
* Tempo impiegato nel costruttore della classe del pacchetto per i pacchetti sincroni
* Tempo impiegato nel metodo Initialize (o SetSite) del pacchetto per i pacchetti sincroni
* Per i pacchetti asincroni, le operazioni precedenti vengono eseguite sul thread in background.  Di conseguenza, le operazioni vengono escluse dal monitoraggio.
* Tempo impiegato in qualsiasi attività asincrona pianificata durante l'inizializzazione del pacchetto per l'esecuzione nel thread principale
* Tempo impiegato nei gestori eventi, in particolare l'attivazione del contesto inizializzato dalla shell o la modifica dello stato non valido della shell
* A partire Visual Studio 2017 Update 3, si inizierà anche a monitorare il tempo impiegato nelle chiamate inattive prima dell'inizializzazione della shell. Le operazioni lunghe nei gestori inattivi causano anche la non risposta dell'IDE e contribuiscono al tempo di avvio percepito dall'utente.

A partire da Visual Studio 2015 sono state aggiunte molte funzionalità. Queste funzionalità consentono di eliminare la necessità di caricare automaticamente i pacchetti. Le funzionalità posticipano anche la necessità di caricare i pacchetti in casi più specifici. Questi casi includono esempi in cui gli utenti sono più certi di usare l'estensione o ridurre l'impatto dell'estensione durante il caricamento automatico.

Altri dettagli su queste funzionalità sono disponibili nei documenti seguenti:

[Contesti dell'interfaccia](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)utente basati su regole: un motore più avanzato basato su regole basato su contesti dell'interfaccia utente consente di creare contesti personalizzati in base a tipi di progetto, tipi e attributi. I contesti personalizzati possono essere usati per caricare un pacchetto in scenari più specifici. Questi scenari specifici includono la presenza di un progetto con una funzionalità specifica anziché l'avvio. I contesti personalizzati consentono anche di creare un'associazione della [visibilità](visibilityconstraints-element.md) dei comandi a un contesto personalizzato in base ai componenti del progetto o ad altri termini disponibili. Questa funzionalità elimina la necessità di caricare un pacchetto per registrare un gestore di query sullo stato del comando.

[](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)Supporto dei pacchetti asincroni: la nuova classe di base AsyncPackage in Visual Studio 2015 consente il caricamento in background dei pacchetti Visual Studio in modo asincrono se il caricamento del pacchetto è stato richiesto da un attributo di caricamento automatico o da una query asincrona del servizio. Questo caricamento in background consente all'IDE di rimanere reattivo. L'IDE è reattivo anche quando l'estensione viene inizializzata in background e gli scenari critici come l'avvio e il caricamento della soluzione non saranno influenzati.

[Servizi asincroni:](how-to-provide-an-asynchronous-visual-studio-service.md)con il supporto dei pacchetti asincroni, è stato aggiunto anche il supporto per l'esecuzione di query su servizi in modo asincrono e la possibilità di registrare servizi asincroni. Ancora più importante, si sta lavorando alla conversione dei servizi di Visual Studio core per supportare le query asincrone, in modo che la maggior parte del lavoro in una query asincrona si verifichi nei thread in background. SComponentModel (Visual Studio host MEF) è uno dei servizi principali che ora supporta la query asincrona per consentire alle estensioni di supportare completamente il caricamento asincrono.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Riduzione dell'impatto delle estensioni caricate automaticamente

Se un pacchetto deve ancora essere caricato automaticamente all'avvio, è importante ridurre al minimo le operazioni eseguite durante l'inizializzazione del pacchetto. Riducendo al minimo il lavoro di inizializzazione del pacchetto, si riducono le probabilità che l'estensione influisca sull'avvio.

Di seguito sono riportati alcuni esempi che potrebbero causare costi elevati per l'inizializzazione dei pacchetti:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Uso del caricamento sincrono dei pacchetti anziché del caricamento asincrono dei pacchetti

Poiché i pacchetti sincroni vengono caricati nel thread principale per impostazione predefinita, si consiglia ai proprietari di estensioni che hanno pacchetti caricati automaticamente di usare la classe di base del pacchetto asincrono, come indicato in precedenza. La modifica di un pacchetto caricato automaticamente per supportare il caricamento asincrono semplifica anche la risoluzione degli altri problemi riportati di seguito.

### <a name="synchronous-filenetwork-io-requests"></a>Richieste di I/O di file/rete sincrone

Idealmente, qualsiasi richiesta di I/O di rete o file sincrona deve essere evitata nel thread principale. L'impatto dipende dallo stato del computer e in alcuni casi può bloccarsi per lunghi periodi di tempo.

L'uso del caricamento asincrono dei pacchetti e delle API I/O asincrone deve garantire che l'inizializzazione del pacchetto non blocchi il thread principale in questi casi. Gli utenti possono anche continuare a interagire con i Visual Studio le richieste di I/O avvengono in background.

### <a name="early-initialization-of-services-components"></a>Inizializzazione anticipata di servizi, componenti

Uno dei modelli comuni nell'inizializzazione del pacchetto è l'inizializzazione dei servizi usati da o forniti da tale pacchetto nel pacchetto `constructor` o nel `initialize` metodo . Anche se ciò garantisce che i servizi siano pronti per l'uso, può anche aggiungere costi non necessari per il caricamento dei pacchetti se tali servizi non vengono usati immediatamente. Tali servizi devono invece essere inizializzati su richiesta per ridurre al minimo le operazioni eseguite nell'inizializzazione del pacchetto.

Per i servizi globali forniti da un pacchetto, è possibile usare metodi che accettano una funzione per inizializzare il servizio in modo lazily solo quando viene richiesto `AddService` da un componente. Per i servizi usati all'interno del pacchetto, è possibile usare Lazy o AsyncLazy per assicurarsi che i servizi siano inizializzati/sottoposti a \<T> query al primo \<T> utilizzo.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Misurazione dell'impatto delle estensioni caricate automaticamente tramite il log attività

A partire da Visual Studio 2017 Update 3, Visual Studio log attività conterrà voci per l'impatto sulle prestazioni dei pacchetti durante l'avvio e il caricamento della soluzione. Per visualizzare queste misurazioni, è necessario aprire il Visual Studio con l'opzione /log e *aprire* ActivityLog.xmlfile.

Nel log attività le voci saranno nell'origine "Manage Visual Studio Performance" e saranno simili all'esempio seguente:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Questo esempio mostra che un pacchetto con GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" ha impiegato 2008 ms all'avvio di Visual Studio. Si noti Visual Studio considera il costo di primo livello come numero principale quando si calcola l'impatto di un pacchetto, come sarebbe il risparmio che gli utenti vedono quando disabilitano l'estensione per tale pacchetto.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Misurazione dell'impatto delle estensioni caricate automaticamente con PerfView

Anche se l'analisi del codice consente di identificare i percorsi di codice che possono rallentare l'inizializzazione dei pacchetti, è anche possibile usare la traccia usando applicazioni come PerfView per comprendere l'impatto del caricamento di un pacchetto Visual Studio avvio.

PerfView è uno strumento di traccia a livello di sistema. Questo strumento consente di comprendere i percorsi ad accesso più elevato in un'applicazione a causa dell'utilizzo della CPU o del blocco delle chiamate di sistema. Di seguito è riportato un rapido esempio di analisi di un'estensione di esempio con PerfView disponibile [nell'Area download Microsoft.](https://www.microsoft.com/en-us/download/details.aspx?id=28567)

**Codice di esempio:**

Questo esempio si basa sul codice di esempio seguente, progettato per mostrare alcune cause di ritardo comuni:

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

Dopo aver configurato l'ambiente Visual Studio con l'estensione installata, è possibile registrare una  traccia di avvio aprendo PerfView e aprendo la finestra di dialogo Raccogli dal menu **Raccogli.**

![Menu raccolta perfview](media/perfview-collect-menu.png)

Le opzioni predefinite forniranno stack di chiamate per l'utilizzo della CPU, ma poiché si è interessati anche al tempo di blocco, è consigliabile abilitare anche gli stack **di** tempo del thread. Quando le impostazioni sono pronte, è possibile fare clic su **Avvia** raccolta e quindi aprire Visual Studio dopo l'avvio della registrazione.

Prima di arrestare la raccolta, è necessario assicurarsi che Visual Studio sia completamente inizializzata, che la finestra principale sia completamente visibile e che, se l'estensione include parti dell'interfaccia utente che vengono automaticamente mostrate, anche queste sono visibili. Quando Visual Studio viene caricata completamente e l'estensione viene inizializzata, è possibile arrestare la registrazione per analizzare la traccia.

**Analisi di una traccia con PerfView:**

Al termine della registrazione, PerfView aprirà automaticamente le opzioni di traccia ed espansione.

Ai fini di questo esempio, si è interessati principalmente alla visualizzazione **Stack** tempo di thread, che è possibile trovare in **Gruppo avanzato**. Questa visualizzazione mostra il tempo totale impiegato in un thread da un metodo, inclusi il tempo CPU e il tempo di blocco, ad esempio l'I/O su disco o l'attesa sugli handle.

 ![stack di tempo dei thread](media/perfview-thread-time-stacks.png)

 Quando si apre **la visualizzazione Stack tempo di thread,** è necessario scegliere il processo **devenv** per avviare l'analisi.

PerfView include indicazioni dettagliate su come leggere gli stack di tempo dei thread nel relativo menu ? per un'analisi più dettagliata. Ai fini di questo esempio, si vuole filtrare ulteriormente questa visualizzazione includendo solo gli stack con il nome del modulo dei pacchetti e il thread di avvio.

1. Impostare **GroupPats su** testo vuoto per rimuovere qualsiasi raggruppamento aggiunto per impostazione predefinita.
2. Impostare **IncPats in** modo da includere parte del nome dell'assembly e del thread di avvio oltre al filtro del processo esistente. In questo caso, deve essere **devenv. Thread di avvio; MakeVsSlowExtension**.

Ora la visualizzazione mostrerà solo il costo associato agli assembly correlati all'estensione. In questa visualizzazione, qualsiasi momento elencato nella colonna **Inc (costo inclusivo)** del thread di avvio è correlato all'estensione filtrata e avrà un impatto sull'avvio.

Per l'esempio precedente, alcuni stack di chiamate interessanti sono:

1. I/O tramite la classe : anche se il costo inclusivo di questi frame potrebbe non essere troppo costoso nella traccia, sono una causa potenziale di un problema perché la velocità di I/O del file varia da computer `System.IO` a computer.

   ![frame di I/O di sistema](media/perfview-system-io-frames.png)

2. Blocco delle chiamate in attesa di altre operazioni asincrone: in questo caso, il tempo inclusivo rappresenta il tempo in cui il thread principale viene bloccato al completamento del lavoro asincrono.

   ![frame di chiamata di blocco](media/perfview-blocking-call-frames.png)

Una delle altre visualizzazioni nella traccia che sarà utile per determinare l'impatto sarà stack **di caricamento delle immagini.** È possibile applicare gli stessi filtri applicati alla visualizzazione **Stack** di tempo dei thread e individuare tutti gli assembly caricati a causa del codice eseguito dal pacchetto caricato automaticamente.

È importante ridurre al minimo il numero di assembly caricati all'interno di una routine di inizializzazione del pacchetto perché ogni assembly aggiuntivo comporterà operazioni di I/O su disco aggiuntive che possono rallentare notevolmente l'avvio nei computer più lenti.

## <a name="summary"></a>Riepilogo

L'Visual Studio è stata una delle aree in cui si continua a ricevere commenti e suggerimenti. Come indicato in precedenza, l'obiettivo è quello di consentire a tutti gli utenti di avere un'esperienza di avvio coerente indipendentemente dai componenti e dalle estensioni installati. Microsoft vuole collaborare con i proprietari delle estensioni per contribuire a raggiungere tale obiettivo. Le linee guida precedenti dovrebbero essere utili per comprendere un impatto sulle estensioni all'avvio ed evitare la necessità di caricarlo automaticamente o caricarlo in modo asincrono per ridurre al minimo l'impatto sulla produttività degli utenti.
