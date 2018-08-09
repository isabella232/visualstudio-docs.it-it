---
title: 'Procedura: diagnosticare le prestazioni delle estensioni | Microsoft Docs'
ms.custom: ''
ms.date: 11/08/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: douge
ms.workload:
- bertaygu
ms.openlocfilehash: 8ef7b61eca40c1a5c74deeb0b3e61de0df8a6be1
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637575"
---
# <a name="measuring-extension-impact-in-startup"></a>Misurare l'impatto di estensione in avvio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Concentrarsi sulle prestazioni delle estensioni in Visual Studio 2017

In base ai suggerimenti dei clienti, una delle aree di interesse per il rilascio di Visual Studio 2017 è stata le prestazioni di caricamento di avvio e di soluzione. Come il team della piattaforma Visual Studio, abbiamo lavorato su come migliorare le prestazioni di caricamento di avvio e di soluzione. In generale, le nostre misurazioni suggeriscono le estensioni installate possono anche avere un impatto notevole su tali scenari.

Per consentire agli utenti comprendere tale impatto, abbiamo aggiunto una nuova funzionalità in Visual Studio per inviare notifiche agli utenti di estensioni lente. In alcuni casi, Visual Studio rileva una nuova estensione che rallenta il caricamento della soluzione o l'avvio. Quando viene rilevato un rallentamento, gli utenti visualizzeranno una notifica nell'IDE di puntarli a una nuova finestra di dialogo "Gestisci le prestazioni di Visual Studio". Questa finestra di dialogo è inoltre sempre accessibile dal menu per Sfoglia le estensioni rilevate in precedenza.

![Gestisci prestazioni di Visual Studio](media/manage-performance.png)

Questo documento è destinato agli sviluppatori di estensioni descrivendo la modalità di calcolo impatto di estensione. Questo documento descrive anche come impatto di estensione può essere analizzato in locale. In locale l'analisi impatto estensione determina se un'estensione può essere visualizzata come alcun impatto sull'estensione delle prestazioni.

> [!NOTE]
> Questo documento è incentrato sull'impatto delle estensioni nel carico di avvio e di soluzione. Estensioni di incidere sulle prestazioni di Visual Studio quando e far sì che l'interfaccia utente smette di rispondere. Per altre informazioni su questo argomento, vedere [procedura: ritardi di diagnosi dell'interfaccia utente causati dalle estensioni](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Estensioni del possibile impatto avvio

Uno dei modi più comuni per le estensioni influire sulle prestazioni di avvio viene eseguita optando per caricamento automatico in uno dei contesti dell'interfaccia utente noti di avvio, ad esempio NoSolutionExists o ShellInitialized. Questi contesti dell'interfaccia utente è essere attivati durante l'avvio. Tutti i pacchetti che includono il `ProvideAutoLoad` attributo nella relativa definizione con tali contesti verrà caricato e inizializzato in quel momento.

Quando è misurare l'impatto di un'estensione, focalizzata principalmente sul tempo impiegato da tali estensioni che sceglie di caricamento automatico nei contesti precedenti. Misurato volte sarebbero includono ma non essere limitati a:

* Il caricamento degli assembly di estensioni per i pacchetti sincroni
* Tempo trascorso nel costruttore della classe del pacchetto per i pacchetti sincroni
* Tempo impiegato nel metodo Initialize (o SetSite) del pacchetto per i pacchetti sincroni
* Per i pacchetti asincroni, le operazioni precedenti eseguite sul thread in background.  Di conseguenza, le operazioni vengono esclusi dal monitoraggio.
* Tempo impiegato nelle operazioni asincrone pianificati durante l'inizializzazione del pacchetto per l'esecuzione sul thread principale
* Tempo impiegato nei gestori eventi, in particolare l'attivazione rapida shell inizializzata o la modifica dello stato di zombie shell
* A partire da Visual Studio 2017 Update 3, verrà inoltre avviato monitoraggio tempo impiegato nelle chiamate inattivo prima che venga inizializzata shell. Esecuzione di operazioni lunghe nei gestori di inattività anche causare IDE che non risponde e contribuire al tempo di avvio percepito dall'utente.

Sono state aggiunte molte funzionalità a partire da Visual Studio 2015. Queste funzionalità consentono con eliminando la necessità di pacchetti di caricamento automatico. Le funzionalità di posticipare anche la necessità di pacchetti da caricare in casi più specifici. Alcuni esempi sono esempi in cui gli utenti sarebbero in grado di usare l'estensione o ridurre l'impatto un'estensione quando si carica automaticamente.

È possibile trovare altre informazioni su queste funzionalità nei documenti seguenti:

[Contesti dell'interfaccia utente basata su regole](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un motore basato su regole più avanzato basato su contesti dell'interfaccia utente consente di creare contesti personalizzati basati sui tipi di progetto, versioni e gli attributi. Contesti personalizzati utilizzabile per caricare un pacchetto durante gli scenari più specifici. Questi scenari specifici includono la presenza di un progetto con una funzionalità specifica invece di avvio. Contesti personalizzati consentono inoltre [visibilità essere associato a un contesto personalizzato di comando](visibilityconstraints-element.md) basato su componenti del progetto o altre condizioni disponibili. Questa funzionalità Elimina la necessità di caricare un pacchetto per registrare un gestore di query dello stato comando.

[Supporto per il pacchetto asincrona](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): la nuova classe di base AsyncPackage in Visual Studio 2015 consente pacchetti di Visual Studio da caricare in background in modo asincrono se il caricamento del pacchetto è stato richiesto da un attributo di caricamento automatico o una query del servizio asincrona . Il caricamento in background consente all'IDE di prestare attenzione. L'IDE è reattiva anche quando l'estensione viene inizializzato in background e gli scenari critici, ad esempio avvio e soluzione di carico non risultare peggiorati.

[Servizi asincroni](how-to-provide-an-asynchronous-visual-studio-service.md): con il supporto asincrono del pacchetto, è inoltre aggiunto il supporto per l'esecuzione di query i servizi in modo asincrono e la possibilità di registrare i servizi asincroni. Aspetto ancora più importante stiamo lavorando sulla conversione di servizi di Visual Studio di base per supportare query asincrona in modo che la maggior parte del lavoro in una query asincrona si verifica nel thread in background. SComponentModel (host MEF di Visual Studio) è uno dei servizi principali che supporta ora la query asincrona per consentire le estensioni per supportare completamente il caricamento asincrono.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Ridurre l'impatto di auto caricare le estensioni

Se un pacchetto deve ancora essere caricato all'avvio automatico, è importante per ridurre al minimo le operazioni eseguite durante l'inizializzazione del pacchetto. Riducendo al minimo le operazioni di inizializzazione del pacchetto, si riduce le probabilità dell'estensione alcun impatto sull'avvio.

Alcuni esempi che poteva causare l'inizializzazione del pacchetto sia costosa sono:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Utilizzo del caricamento del pacchetto sincrona anziché caricamento asincrono del pacchetto

Perché sono stati caricati pacchetti sincroni sul thread principale per impostazione predefinita, ti consigliamo di proprietari di estensione che hanno caricato automaticamente i pacchetti per usare la classe di base pacchetto asincrona invece come indicato in precedenza. La modifica di un pacchetto di caricamento automatico per supportare il caricamento asincrono anche renderà più facile risolvere i problemi seguenti.

### <a name="synchronous-filenetwork-io-requests"></a>Richieste dei / o sincrono file/rete

In teoria è consigliabile evitare qualsiasi richiesta dei / o file o rete sincrona nel thread principale. L'impatto dipenderà lo stato della macchina e può essere bloccato per lunghi periodi di tempo, in alcuni casi.

Usando le API dei / o asincrone e il caricamento del pacchetto asincrona deve assicurarsi che l'inizializzazione del pacchetto non blocca il thread principale in tali casi. Inoltre, gli utenti possono continuare a interagire con Visual Studio mentre si verificano le richieste dei / o in background.

### <a name="early-initialization-of-services-components"></a>Inizializzazione anticipata dei servizi, componenti

Uno dei modelli comuni nell'inizializzazione del pacchetto consiste nell'inizializzare servizi usato da o fornite da tale pacchetto nel pacchetto `constructor` o `initialize` (metodo). Mentre in questo modo i servizi sono pronti per essere usato, è anche possibile aggiungere costi non necessari per creare un pacchetto di caricamento se tali servizi non vengono usati immediatamente. Invece, tali servizi devono essere inizializzati su richiesta per ridurre al minimo le operazioni eseguite nell'inizializzazione del pacchetto.

Per i servizi globali forniti da un pacchetto, è possibile usare `AddService` metodi che accettano una funzione in modo differito inizializzare il servizio solo quando richiesto da un componente. Per i servizi usati all'interno del pacchetto, è possibile usare Lazy<T> AsyncLazy o<T> per assicurarsi che i servizi siano inizializzati o eseguire una query al primo utilizzo.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Misurare l'impatto di auto caricare le estensioni usando i log attività

A partire da Visual Studio 2017 Update 3, log attività di Visual Studio ora contiene voci per impatto sulle prestazioni dei pacchetti durante il caricamento di avvio e di soluzione. Per visualizzare queste misure, è necessario avviare Visual Studio con l'opzione /log. e aprire *Activitylog* file.

Nel log attività, le voci si trovano in origine "Gestire le prestazioni di Visual Studio" e avrà un aspetto simile al seguente:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

In questo esempio mostra che un pacchetto con GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" impiegato di Visual Studio 2008 ms in avvio. Si noti che Visual Studio considera costo di livello superiore come il numero principale durante il calcolo impatto di un pacchetto che sarebbe che visibile agli utenti un risparmio quando si disabilita l'estensione per tale pacchetto.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Misurare l'impatto di auto caricare le estensioni con PerfView

Durante l'analisi del codice consentono di identificare i percorsi del codice che possono rallentare l'inizializzazione del pacchetto, possono usare anche la tracciatura usando applicazioni come PerfView per comprendere l'impatto di un caricamento del pacchetto di avvio di Visual Studio.

PerfView è uno strumento di traccia a livello di sistema. Questo strumento consente di comprendere i percorsi critici in un'applicazione a causa dell'utilizzo della CPU o bloccare le chiamate di sistema. Di seguito è riportato un esempio sull'analisi di un'estensione di esempio con PerfView disponibile all'indirizzo il [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Esempio di codice:**

Questo esempio è basato sull'esempio di codice riportato di seguito, che è progettato per mostrare caso alcune cause comuni di ritardo:

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

**La registrazione di un oggetto trace con PerfView:**

Dopo aver impostato l'ambiente di Visual Studio con l'estensione installata, è possibile registrare una traccia di avvio aprendo PerfView e la **raccogliere** della finestra di dialogo il **raccogliere** menu.

![menu collect perfview](media/perfview-collect-menu.png)

Le opzioni predefinite fornirà gli stack di chiamate per l'utilizzo della CPU, ma poiché si è interessati anche della durata di blocco, è anche necessario abilitare **Thread ora** stack. Dopo aver completato le impostazioni è possibile fare clic su **Avvia raccolta** e avviare Visual Studio dopo aver avviata la registrazione.

Prima di interrompere la raccolta, si desidera assicurarsi che Visual Studio è completamente inizializzato, la finestra principale è completamente visibile e se l'estensione dispone degli elementi dell'interfaccia utente che mostrano automaticamente, sono inoltre visibili. Dopo che Visual Studio è stata caricata completamente e viene inizializzata l'estensione, è possibile arrestare la registrazione per analizzare la traccia.

**Analisi di un oggetto trace con PerfView:**

Dopo aver completata la registrazione PerfView verrà automaticamente aprire la traccia ed espandere le opzioni.

Ai fini di questo esempio, si è interessati principalmente il **stack in fase di Thread** visualizzazione che è possibile trovare **gruppo avanzate**. Questa visualizzazione saranno inclusi tempo totale impiegato in un thread da un metodo inclusi tempo CPU e il tempo di blocco, ad esempio/o del disco o in attesa di handle.

 ![tempo stack di thread](media/perfview-thread-time-stacks.png)

 Durante l'apertura **stack in fase di Thread** visualizzazione, è consigliabile scegliere le **devenv** processo per avviare l'analisi.

PerfView è Guida dettagliata su come leggere gli stack di tempo in un proprio menu Guida per un'analisi più dettagliata di thread. Ai fini di questo esempio, si vuole filtrare ulteriormente questa visualizzazione includendo solo gli stack di thread di avvio e nome del modulo di pacchetti.

1. Impostare **GroupPats** al testo vuoto per rimuovere qualsiasi forma di raggruppamento aggiunta per impostazione predefinita.
2. Impostare **IncPats** per includere una parte del nome dell'assembly e avvio Thread oltre a filtro processo esistente. In questo caso, deve essere **devenv; Thread di avvio. MakeVsSlowExtension**.

A questo punto la vista mostrerà solo i costi associati con gli assembly correlati all'estensione. In questa visualizzazione, elencato in qualsiasi momento il **Inc (costo inclusivo)** colonna del thread di avvio è correlata alla nostra estensione filtrati e sarà alcun impatto sull'avvio.

Per l'esempio precedente alcuni interessano chiamata stack sarà:

1. IO utilizzo `System.IO` classe: inclusivo costo di tali frame potrebbe non essere troppo costoso nella traccia, ma sono una potenziale causa di un problema poiché file velocità dei / o possono variare da computer a computer.

  ![fotogrammi i/o di sistema](media/perfview-system-io-frames.png)

2. Bloccare le chiamate in attesa di altre operazioni asincrone: In questo caso, al tempo inclusivo rappresenta l'ora in cui il thread principale è bloccato al completamento del lavoro asincrono.

  ![frame di chiamata di blocco](media/perfview-blocking-call-frames.png)

Una delle altre visualizzazioni nella traccia che si riveleranno utili per determinare l'impatto sarà il **serie di caricamento immagini**. È possibile applicare i medesimi filtri applicati agli **stack in fase di Thread** consente di visualizzare e individuare tutti gli assembly caricati a causa il codice eseguito dal pacchetto caricato automaticamente.

È importante minimizzare il numero di assembly caricati all'interno di una routine di inizializzazione del pacchetto come ogni assembly aggiuntivo comporterà i/o disco aggiuntivo che può rallentare l'avvio notevolmente nei computer più lenti.

## <a name="summary"></a>Riepilogo

Avvio di Visual Studio è stata una delle aree su che è continuamente ottenere commenti e suggerimenti. Il nostro obiettivo, come indicato in precedenza è per tutti gli utenti abbiano un avvio coerenti con l'esperienza indipendentemente dal fatto di componenti e le estensioni installate. Vorremmo lavorare con i proprietari di estensione per aiutarli a contribuire a raggiungere tale obiettivo. Le linee guida precedenti devono essere utili per comprendere l'impatto estensioni all'avvio e sia evitando la necessità di auto carico o per caricare in modo asincrono per ridurre al minimo l'impatto sulla produttività degli utenti.
