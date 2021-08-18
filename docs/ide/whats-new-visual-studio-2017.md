---
title: Novità di Visual Studio 2017
titleSuffix: ''
description: Informazioni sulle nuove funzionalità di Visual Studio 2017.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 65ee7d1a1252e4906f291ace121f7c92c889f616
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150924"
---
# <a name="whats-new-in-visual-studio-2017"></a>Novità di Visual Studio 2017

**Aggiornamento per la [versione 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Se si sta valutando l'opportunità di eseguire l'aggiornamento da una versione precedente di Visual Studio, ecco cosa può offrire Visual Studio 2017: produttività senza precedenti per qualsiasi sviluppatore, qualsiasi app e qualsiasi piattaforma. Visual Studio 2017 è perfetto per lo sviluppo di app per Android, iOS, Windows, Linux, Web e cloud. Consente la rapida scrittura del codice, assicura facilità di debug e diagnosi e permette l'esecuzione frequente di test per il rilascio di app affidabili. È inoltre possibile rendere Visual Studio un ambiente "su misura" grazie alla possibilità di creare estensioni personalizzate. Questa versione offre eccezionali vantaggi, inclusi controllo della versione, strumenti e processi Agile ed efficienti funzionalità di collaborazione!

>[!div class="button"]
>[Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Di seguito è riportato un riepilogo generale delle modifiche apportate dopo la versione precedente, ovvero Visual Studio 2015:

* **[Concetti fondamentali ridefiniti.](#redefined-fundamentals)** Una nuova esperienza di installazione offre la possibilità di completare l'installazione più rapidamente e di installare quello che serve all'occorrenza.
* **[Prestazioni e produttività](#performance-and-productivity)**. Microsoft si è concentrata sulle funzionalità nuove e moderne di sviluppo per dispositivi mobili, cloud e desktop. E Visual Studio si avvia più velocemente, offre tempi di risposta migliori e usa meno memoria rispetto a prima.
* **[Sviluppo di app cloud con Azure](#cloud-app-development-with-azure)**. Un gruppo di strumenti Azure incorporati consentono di creare facilmente app per cloud con tecnologia Microsoft Azure. Visual Studio facilita la configurazione, la compilazione, il debug, l'inserimento in pacchetti e la distribuzione di app e servizi in Azure.
* **[Windows sviluppo di app](#windows-app-development)**. Usare i modelli UWP in Visual Studio 2017 per creare un unico progetto per tutti i dispositivi Windows 10, ovvero PC, tablet, telefono, Xbox, HoloLens, Surface Hub e altro.
* **[Sviluppo di app per dispositivi mobili](#mobile-app-development)**. Xamarin consente di promuovere l'innovazione e di ottenere rapidamente risultati, inoltre unifica i requisiti per i dispositivi mobili multipiattaforma usando un'unica codebase principale e un singolo set di competenze.
* **[Sviluppo multipiattaforma](#cross-platform-development)**. Distribuire facilmente software a qualsiasi piattaforma di destinazione. Estendere i processi DevOps a SQL Server con Redgate Data Tools e automatizza in modo sicuro le distribuzioni dei database da Visual Studio. Oppure, utilizzare .NET Core per scrivere app e librerie in modo che vengano eseguite senza modifiche nei sistemi operativi Windows, Linux e macOS.
* **[Sviluppo di giochi](#games-development)**. Con Visual Studio Tools per Unity (VSTU) è possibile usare Visual Studio per scrivere script di giochi ed editor in C# e quindi usarne il potente debugger per individuare e correggere gli errori.
* **[Sviluppo di intelligenza artificiale](#ai-development)**. Con Visual Studio Tools for AI è possibile usare le funzionalità di produttività di Visual Studio per promuovere l'innovazione nel settore dell'intelligenza artificiale. Compilare, testare e distribuire soluzioni per l'apprendimento avanzato o l'intelligenza artificiale perfettamente integrate con Azure Machine Learning per offrire funzionalità di sperimentazione avanzate.

> [!NOTE]
> Per un elenco completo delle nuove funzionalità in Visual Studio 2017, vedere le [note sulla versione corrente](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Per un'anteprima delle offerte di funzionalità future, vedere le [note sulla versione di anteprima](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Ecco informazioni più dettagliate su alcuni dei più importanti miglioramenti e delle nuove funzionalità di Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Concetti fondamentali ridefiniti

### <a name="a-new-setup-experience"></a>Una nuova esperienza di installazione

Con Visual Studio è ancora più semplice e veloce installare solo le funzionalità necessarie, all'occorrenza. E in più la disinstallazione non presenta problemi.

La modifica più importante da notare quando si installa Visual Studio è la nuova esperienza di installazione. Nella scheda **Carichi di lavoro** sono visualizzate le opzioni di installazione raggruppate in modo da rappresentare i framework, i linguaggi e le piattaforme più comuni, in grado di supportare qualsiasi attività, dallo sviluppo desktop .NET allo sviluppo di applicazioni C++ in Windows, Linux e iOS.

Scegliere i carichi di lavoro necessari e modificarli all'occorrenza.

![Finestra di dialogo di installazione di Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

Sono disponibili anche opzioni per ottimizzare l'installazione:

* Si vuole scegliere i propri componenti anziché usare i carichi di lavoro? Selezionare la scheda **Singoli componenti** nel programma di installazione.
* Si vuole installare i Language Pack anche senza modificare l'opzione lingua di Windows? Scegliere la scheda **Language Pack** del programma di installazione.
* **Novità della versione 15.7**: si vuole cambiare il percorso d'installazione di Visual Studio? Scegliere la scheda **Opzioni di installazione** nel programma di installazione.

Per altre informazioni sulla nuova esperienza di installazione, incluse le istruzioni dettagliate per eseguirla, vedere la pagina [Installare Visual Studio](../install/install-visual-studio.md).

### <a name="a-focus-on-accessibility"></a>Informazioni sull'accessibilità

**Nella versione 15.3** sono state apportate oltre 1700 correzioni mirate a migliorare la compatibilità tra Visual Studio e i dispositivi di Assistive Technology usati da molti clienti. Molti scenari, inoltre, sono stati resi ancora più compatibili con utilità di lettura dello schermo, temi a contrasto elevato e altri dispositivi di Assistive Technology. Anche il debugger, l'editor e la shell hanno tutti subito considerevoli miglioramenti.

Per altre informazioni, visitare il post di blog sui [miglioramenti dell'accessibilità di Visual Studio 2017 (versione 15.3)](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/).

## <a name="performance-and-productivity"></a>Prestazioni e produttività

### <a name="sign-in-across-multiple-accounts"></a>Accedere a più account

È stato introdotto in Visual Studio un nuovo servizio di identità che consente di condividere gli account utente in Team Explorer, strumenti di Azure, pubblicazione in Microsoft Store e altri strumenti.

È anche possibile rimanere connessi più a lungo. Non verrà richiesto di accedere nuovamente ogni 12 ore. Per altre informazioni, vedere il post del blog [Fewer Visual Studio sign-in prompts](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) (Riduzione del numero di richieste di accesso a Visual Studio).

### <a name="start-visual-studio-faster"></a>Avviare Visual Studio più rapidamente

Il nuovo strumento Controllo prestazioni di Visual Studio può essere utile per ottimizzare i tempi di avvio dell'IDE. In Controllo prestazioni sono elencate tutte le estensioni e le finestre degli strumenti che potrebbero rallentare l'avvio dell'IDE. È possibile usare la funzionalità per migliorare le prestazioni di avvio, stabilendo quando avviare le estensioni o se le finestre degli strumenti vengono aperte all'avvio.

### <a name="faster-on-demand-loading-of-extensions"></a>Caricamento su richiesta delle estensioni più rapido

Le estensioni di Visual Studio (così come le estensioni di terze parti) sono state spostate in modo da poter essere caricate su richiesta, invece che all'avvio dell'IDE. Le informazioni sulle estensioni che hanno un impatto sulle prestazioni di avvio, caricamento delle soluzioni e digitazione, È possibile visualizzare queste informazioni in **Guida alla** gestione delle  >  **Visual Studio prestazioni**.

  ![Finestra di dialogo Opzioni in Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gestire le estensioni con Gestione roaming estensioni

È ancora più semplice configurare ogni ambiente di sviluppo usando le estensioni preferite quando si accede a Visual Studio. Il nuovo strumento Gestione roaming estensioni tiene traccia di tutte le estensioni preferite creando un elenco sincronizzato nel cloud.

Per visualizzare un elenco delle estensioni in Visual Studio, fare clic su Strumenti  >  **Estensioni & aggiornamenti** e quindi fare clic su Gestione estensioni **mobili**.

![Visual Studio 2017 - Finestra di dialogo Estensioni e aggiornamenti](media/vs2017ide-extensions-and-updates.png)

Gestione roaming estensioni tiene traccia di tutte le estensioni installate, ma è possibile scegliere quelle che si vuole aggiungere all'elenco di roaming.

![Visual Studio 2017 - Gestione estensioni mobili](media/vs2017ide-RoamingExtensionManager.png)

Quando si usa Gestione roaming estensioni sono disponibili tre tipi di icona nell'elenco:

* ![Icona di roaming con roaming: estensione che fa parte di questo elenco di ](media/vs2017ide-roamedicon.png) **** roaming, ma non installata nel computer.
  Per eseguire l'installazione usare il pulsante **Download**.
* ![Roaming dell'& installato con roaming & installato : tutte le estensioni che fanno parte di questo elenco di roaming e installate ](media/vs2017ide-roamedinstalledicon.png) **** nell'ambiente di sviluppo.
  Se si decide di evitare il roaming, è possibile rimuovere le estensioni usando il pulsante **Arresta roaming**.
* ![Icona installata ](media/vs2017ide-installedicon.png) **_Installato_**: tutte le estensioni installate in questo ambiente, ma che non fanno parte dell'elenco di roaming.
  Per aggiungere le estensioni all'elenco di roaming, usare il pulsante **Avvia roaming**.

Qualsiasi estensione scaricata quando si è connessi viene aggiunta all'elenco come **Roamed & Installed** (In roaming e installata). L'estensione diventa quindi parte dell'elenco di roaming, rendendola così accessibile da qualsiasi computer.

### <a name="experience-live-unit-testing"></a>Provare Live Unit Testing

In Visual Studio Enterprise 2017, questa funzionalità mostra i risultati dei live unit test e del code coverage direttamente nell'editor mentre si scrive il codice. Funziona con i progetti C# e Visual Basic per .NET Framework e .NET Core e supporta tre framework di test di MSTest, xUnit e NUnit.

![Live Unit Testing](media/lut-codewindow.png)

Per altre informazioni, vedere [Introduzione a Live Unit Testing](../test/live-unit-testing-intro.md). Per un elenco delle nuove funzionalità aggiunte in ogni versione di Visual Studio Enterprise 2017, vedere [Novità di Live Unit Testing](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Configurare una CI/CD

#### <a name="automated-testing"></a>Test automatizzati

I test automatizzati sono componenti fondamentali di qualsiasi pipeline DevOps. Consente di testare in modo coerente e attendibile e di rilasciare la soluzione in cicli più brevi. I flussi CI/CD (Integrazione continua e Recapito continuo) consentono di rendere più efficiente il processo.

Per altre informazioni sui test automatizzati, vedere il post di blog [CI/CD pipeline for automated tests in DevOps](/archive/blogs/visualstudioalmrangers/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently) (Pipeline CI/CD per test automatizzati in DevOps).

Per altre informazioni sulle novità dell'estensione DevLabs [Strumenti di recapito continuo per Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio), vedere il post del blog [Commit with confidence: Commit time code quality](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) (Eseguire il commit in sicurezza: qualità del codice in fase di commit).

### <a name="visual-studio-ide-enhancements"></a>Miglioramenti dell'IDE di Visual Studio

#### <a name="multi-caret-editing"></a>Modifica di più punti di inserimento

**Novità della versione 15.8**: la modifica in contemporanea di più posizioni in un file ora è facile. Iniziare a creare punti di inserimento e selezioni in più posizioni in un file. Usare quindi la funzionalità di modifica di più punti di inserimento per apportare la stessa modifica in due o più posizioni nello stesso momento.

Per altre informazioni, vedere la sezione [Multi-caret selection](finding-and-replacing-text.md#multi-caret-selection) (Selezione di più punti di inserimento) della pagina [Cercare e sostituire testo](finding-and-replacing-text.md).

#### <a name="keep-keybinding-profiles-consistent"></a>Mantenere la coerenza tra i profili dei tasti di scelta rapida

**Novità nella versione 15.8**: ora è possibile mantenere la coerenza dei tasti di scelta rapida tra gli strumenti con due nuovi profili di tastiera: Visual Studio Code e ReSharper (Visual Studio). Questi schemi sono disponibili in **Strumenti**  >  **Opzioni**  >  **Tastiera**  >  **generale e** nel menu a discesa superiore.

  ![Nuovi profili di tasti di scelta rapida per ReSharper e Visual Studio Code](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Utilizzare i nuovi refactoring

Il refactoring è il processo di miglioramento del codice dopo la scrittura. Il refactoring consente di modificare la struttura interna del codice senza modificarne il comportamento. Vengono spesso aggiunti nuovi processi di refactoring, come quelli elencati di seguito:

* Aggiungere un parametro (da CallSite)
* Generare sostituzioni
* Aggiungere un argomento denominato
* Aggiungere il controllo Null per i parametri
* Inserire separatori di cifre in valori letterali
* Modificare la base per i valori letterali numerici (ad esempio da esadecimale a binario)
* Convertire if-to-switch
* Rimuovere la variabile non usata

Per altre informazioni, vedere [Azioni rapide](common-quick-actions.md).

#### <a name="interact-with-git"></a>Interagire con Git

Quando si lavora con un progetto in Visual Studio, è possibile configurare il codice ed eseguirne rapidamente il commit e la pubblicazione in un servizio GIT. È anche possibile gestire i repository GIT tramite i menu visualizzati facendo clic sui pulsanti nell'angolo inferiore destro dell'IDE.

![Visual Studio 2017 interagisce con la finestra di dialogo di GIT](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Controlli di spostamento migliorati

L'esperienza è stata aggiornata per consentire spostamenti più efficienti e con meno distrazioni.

* **Novità della versione 15.4:** Vai a definizione **(** **CTRL+** clic o +  **F12**) Gli utenti del mouse hanno un modo più semplice per passare alla definizione di un membro premendo CTRL e quindi facendo clic sul &ndash; membro.  È possibile premere **CTRL** e passare il mouse su un simbolo del codice per sottolinearlo e trasformarlo in un collegamento. Per altre informazioni, vedere [Vai a definizione e Visualizza definizione](go-to-and-peek-definition.md).

* **Vai a implementazione** (**CTRL** + **F12**) Passare da qualsiasi tipo o membro &ndash; di base alle varie implementazioni.

* **Vai a tutti** (**CTRL** T o CTRL + ) Consente di passare +  direttamente a qualsiasi dichiarazione di  +  &ndash; file/tipo/membro/simbolo. È possibile filtrare l'elenco dei risultati o usare la sintassi di query, ad esempio "f Terminericerca" per i file, "t Terminericerca" per i tipi e così via.

  ![Vai a tutti migliorato](media/vs2017ide-navigation-go-to.png)

* **Trova tutti i riferimenti** (**MAIUSC** + **F12**) Con la colorazione della sintassi, è possibile raggruppare i risultati trova tutti i riferimenti in base a una combinazione di &ndash; progetto, definizione e percorso. È anche possibile "bloccare" i risultati in modo da poter continuare la ricerca di altri riferimenti senza perdere i risultati originali.

  ![Nuovo strumento Trova tutti i riferimenti](media/vs2017ide-find-all-references.png)

* **Visualizzatore di struttura** &ndash; Linee grigie verticali punteggiate (guide di rientro) che fungono da punti di riferimento nel codice per fornire informazioni di contesto all'interno del frame di visualizzazione. Tali guide sono incluse nei famosi Productivity Power Tools. È possibile usarle per visualizzare e individuare il blocco di codice attivo in qualsiasi momento, senza dover scorrere. Al passaggio del mouse sulle linee viene visualizzata una descrizione comando che mostra l'apertura del blocco e dei relativi elementi padre. Questa funzionalità è disponibile per tutti i linguaggi supportati da grammatiche TextMate, nonché per C#, Visual Basic e XAML.

  ![Visualizzatore di struttura di Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Per altre informazioni sulle nuove funzionalità di produttività, vedere il post di blog [Visual Studio 2017: Produttività, prestazioni e](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) partner.

### <a name="visual-c"></a>Visual C++

Sono stati introdotti numerosi miglioramenti in Visual Studio, tra cui la distribuzione delle istruzioni di base di C++ con Visual Studio, l'aggiornamento del compilatore aggiungendo il supporto avanzato per le funzionalità di C++11 e C++, l'aggiunta e l'aggiornamento di funzionalità nelle librerie di C++. Sono stati anche migliorati i carichi di lavoro di installazione, le prestazioni dell'IDE di C++ e altro.

Sono stati corretti anche più di 250 bug e segnalati problemi nel compilatore e negli strumenti, molti inviati dai clienti tramite developer [Community per C++.](https://aka.ms/feedback/report?space=62 "Strumenti Community per sviluppatori per C++")

Per informazioni dettagliate complete, vedere la pagina Novità Visual C++ [visual 2017.](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)

### <a name="debugging-and-diagnostics"></a>Debug e diagnostica

#### <a name="run-to-click"></a>Esegui fino alla riga selezionata

È ora possibile spostarsi più facilmente in avanti durante il debug senza impostare un punto di interruzione in corrispondenza della riga desiderata. Quando il debugger è interrotto, è sufficiente fare clic sull'icona visualizzata accanto alla riga di codice. Il codice verrà eseguito e si interromperà in corrispondenza di tale riga la volta successiva che viene raggiunta nel percorso del codice.

![Debug di Visual Studio 2017 - Esegui fino alla riga selezionata](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nuovo Helper eccezioni

Il nuovo Helper eccezioni consente di visualizzare immediatamente informazioni sulle eccezioni. Le informazioni vengono visualizzate in un formato compatto con accesso immediato alle eccezioni interne. Durante la diagnostica di NullReferenceException è possibile individuare rapidamente i riferimenti Null direttamente nell'Helper eccezioni.

![Nuova finestra di dialogo Helper eccezioni in Visual Studio](media/vs2017ide-ExceptionHelper.png)

Per altre informazioni, vedere il post del blog [Use the new Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) (Usare il nuovo Helper eccezioni in Visual Studio).

#### <a name="snapshots-and-intellitrace-step-back"></a>Snapshot e la funzionalità per tornare indietro di IntelliTrace

**Novità della versione 15.5**: la funzionalità per tornare indietro di IntelliTrace crea automaticamente uno snapshot dell'applicazione in corrispondenza di ogni punto di interruzione e ogni evento di esecuzione di passaggio del debugger. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

È possibile spostarsi e visualizzare gli snapshot  usando i **pulsanti** Indietro e Avanti nella barra degli **strumenti Debug.** Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella scheda **Eventi** della finestra **Strumenti di diagnostica**. Lo spostamento indietro o in avanti su un evento attiva automaticamente il debug cronologico per l'evento selezionato.

![Esempio di passaggio indietro di IntelliTrace in Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Pulsanti Indietro e Avanti")

Per altre informazioni, vedere la pagina [Visualizzare gli snapshot con la funzionalità per tornare indietro di IntelliTrace](../debugger/view-historical-application-state.md).

### <a name="containerization"></a>Creazione di contenitori

I contenitori consentono di ottenere una maggiore densità delle app e di ridurre i costi di distribuzione oltre a offrire miglioramenti della produttività e della flessibilità DevOps.

#### <a name="docker-container-tooling"></a>Strumenti per contenitori Docker

**Novità della versione 15.5:**

* Visual Studio include strumenti per i contenitori Docker che ora supportano i Dockerfile in più fasi, per semplificare la creazione di immagini dei contenitori ottimizzate.
* Per impostazione predefinita, Visual Studio eseguirà automaticamente il pull, la compilazione e l'esecuzione delle immagini dei contenitori necessarie in background quando si apre un progetto con supporto di Docker. È possibile disabilitare questo comportamento tramite l'impostazione **Avvia automaticamente i contenitori in background** in Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Sviluppo di app cloud con Azure

### <a name="azure-functions-tools"></a>Strumenti di Funzioni di Azure

Nell’ambito del carico di lavoro "Sviluppo di Azure", sono stati inclusi strumenti che consentono di sviluppare funzioni di Azure con librerie pre-compilate di classe C#. È possibile compilare, eseguire ed effettuare il debug nel computer di sviluppo locale e pubblicare direttamente in Azure da Visual Studio.

Per altre informazioni, vedere la Funzioni di Azure [strumenti per Visual Studio](/azure/azure-functions/functions-develop-vs) pagina.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Eseguire il debug di app ASP.NET in tempo reale usando punti di ancoraggio e punti di registrazione nelle applicazioni Azure in tempo reale

**Novità della versione 15.5**: Snapshot Debugger crea uno snapshot delle app in produzione, quando viene eseguito il codice a cui si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

La raccolta di snapshot è disponibile per le seguenti app Web in esecuzione in Servizio app di Azure:

* Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
* Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.

Per altre informazioni, vedere [Eseguire il debug di app ASP.NET in tempo reale usando punti di ancoraggio e punti di registrazione](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Sviluppo di applicazioni Windows

### <a name="universal-windows-platform"></a>Piattaforma UWP (Universal Windows Platform)

La piattaforma UWP (Universal Windows) è la piattaforma delle app per Windows 10. È possibile sviluppare app per la piattaforma UWP con un solo set di API, un singolo pacchetto di app e un singolo Store per raggiungere tutti i dispositivi Windows 10, ovvero PC, tablet, telefono, Xbox, HoloLens, Surface Hub e altri. La piattaforma UWP supporta diverse dimensioni dello schermo e svariati modelli di interazione, ad esempio penna, mouse e tastiera, periferica di gioco o penna. Alla base delle app UWP vi è il concetto che gli utenti vogliono avere esperienze mobili su TUTTI i loro dispositivi e la libertà di usare il dispositivo più pratico o produttivo per ogni attività.

![Piattaforma UWP (Universal Windows Platform)](../cross-platform/media/uwp_coreextensions.png)

Scegliere il linguaggio di sviluppo preferito tra C#, Visual Basic, C++ o JavaScript per creare un'app UWP per dispositivi Windows 10. Visual Studio 2017 include un modello di app UWP per ogni linguaggio che consente di creare un unico progetto per tutti i dispositivi. Al termine del lavoro è possibile produrre un pacchetto dell'app e inviarlo a Microsoft Store da Visual Studio per mettere l'app a disposizione dei clienti per qualsiasi dispositivo Windows 10.

**Novità nella versione 15.5**: Visual Studio 2017 versione 15.5 fornisce il miglior supporto per Windows 10 Fall Creators Update SDK (10.0.16299.0). Windows 10 Fall Creators Update introduce anche numerosi miglioramenti per gli sviluppatori UWP. Di seguito sono riportate alcune delle principali modifiche: 

* **Supporto di .NET Standard 2.0**<br/>Oltre a semplificare la distribuzione delle app, Windows 10 Fall Creators Update è la prima versione di Windows 10 a fornire il supporto di .NET 2.0 Standard. In effetti, [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) è un'implementazione di riferimento della libreria di classi base che può essere implementata da qualsiasi piattaforma .NET. L'obiettivo di .NET Standard è semplificare il più possibile la condivisione del codice su qualsiasi piattaforma di lavoro .NET scelta dagli sviluppatori .NET.
* **Il meglio di UWP e Win32**<br/>È stata migliorata la piattaforma Windows 10 con [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) per migliorare Windows 10 per tutti gli sviluppatori .NET, indipendentemente dal fatto che concentrino le loro attività in UWP, WPF, Windows Form o Xamarin. Con il nuovo tipo di progetto per pacchetti di app in Visual Studio 2017 versione 15.5, è possibile creare pacchetti di app Windows per i progetti WPF o Windows Form, esattamente come per i progetti UWP. Dopo aver creato il pacchetto dell'app, diventano disponibili tutti i vantaggi per la distribuzione di app Windows 10 ed è possibile scegliere Microsoft Store (per le app consumer) o Microsoft Store per le aziende e gli istituti di istruzione. Dato che le app in pacchetto hanno accesso sia alla superficie API UWP completa che alle API Win32 su desktop, è ora possibile modernizzare le applicazioni Windows Form e WPF gradualmente con le API UWP e le funzionalità di Windows 10. Inoltre, è possibile includere componenti Win32 nelle applicazioni UWP che possono così essere usate nel desktop con tutte le funzionalità Win32.

Per altre informazioni sulla piattaforma UWP, vedere la pagina [Sviluppare app per la piattaforma UWP (Universal Windows Platform)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md).

## <a name="mobile-app-development"></a>Sviluppo di app per dispositivi mobili

### <a name="xamarin"></a>Xamarin

Nell’ambito del carico di lavoro "Sviluppo per dispositivi mobili con .NET", gli sviluppatori esperti in C#, .NET e Visual Studio possono recapitare App Android, iOS e Windows native con Xamarin. Gli sviluppatori potranno trarre vantaggio dalla stessa potenza e produttività quando lavorano con Xamarin per le app per dispositivi mobili, incluso il debug remoto nei dispositivi Android, iOS e Windows,&mdash;senza dover apprendere linguaggi di codifica nativi come Objective-C o Java.

Per altre informazioni, vedere la pagina [Visual Studio e Xamarin](/xamarin/).

### <a name="entitlements-editor"></a>Editor dei titoli

**Novità nella versione 15.3**: per le esigenze di sviluppo di iOS, è stato aggiunto un editor dei diritti autonomo. Include un'interfaccia utente intuitiva di agevole esplorazione. Per avviarlo, fare doppio clic sul file *entitlements.plist.*

![Editor degli entitlement per Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Strumenti di Visual Studio per Xamarin

**Novità della versione 15.4**: Xamarin Live consente agli sviluppatori di distribuire, testare ed eseguire il debug delle app in modo continuo, direttamente in dispositivi iOS e Android. Dopo aver scaricato Xamarin Live Player, disponibile in App Store o in Google Play, è possibile associare il dispositivo a Visual Studio e rivoluzionare le modalità di compilazione delle app per dispositivi mobili. Questa funzionalità è ora inclusa in Visual Studio e può essere abilitata da **Strumenti** > **Opzioni** > **Xamarin** > **Altro** > **Abilita Xamarin Live Player**.

![Animazione delle modalità di associazione, distribuzione e modifica in tempo reale per Xamarin Player](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Supporto per l'emulatore Android di Google

**Novità della versione 15.8**: quando si usa Hyper-V ora è possibile usare l'emulatore Android di Google insieme ad altre tecnologie basate su Hyper-V, tra cui macchine virtuali Hyper-V, strumenti per Docker, l'emulatore di HoloLens e altro ancora. Questa funzionalità richiede l'aggiornamento del 10 aprile 2018 per Windows 10 o una versione successiva.

![Emulatore Android di Google sulle tecnologie Hyper-V](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Editor con visualizzazione suddivisa per la finestra di progettazione di Xamarin.Android

Un'altra **novità della versione 15.8**: sono stati apportati significativi miglioramenti all'esperienza della finestra di progettazione per Xamarin.Android. Particolarmente rilevante è il nuovo editor con visualizzazione suddivisa che consente di creare, modificare e visualizzare in anteprima i layout contemporaneamente.

![Editor con visualizzazione suddivisa per la finestra di progettazione di Xamarin.Android](media/android-designer-split-view.png)

Per altre informazioni, vedere [Accelerazione hardware per le prestazioni dell'emulatore](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

Novità della versione **15.5:** Visual Studio App Center, ora disponibile a livello generale per le app &mdash; Android, iOS, macOS e Windows, include tutto il necessario per gestire il ciclo di vita delle app, tra cui compilazioni automatizzate, test su dispositivi reali nel cloud, distribuzione a beta tester e app store e monitoraggio dell'utilizzo reale tramite dati di analisi e arresto &mdash; anomalo. Le app scritte in Objective-C, Swift, Java, C#, Xamarin e React Native sono supportate per tutte le funzionalità.

  ![Ambiente di test di Visual Studio App Center](media/app-center-test-env.png)

Per altre informazioni, vedere il post di blog [Introducing App Center: Build, test, distribute and monitor apps in the cloud](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) (Introduzione a: Compilare, testare, distribuire e monitorare le app nel cloud).

## <a name="cross-platform-development"></a>Sviluppo multipiattaforma

### <a name="redgate-data-tools"></a>Redgate Data Tools

Per estendere le funzionalità DevOps all'ambiente di sviluppo di database SQL Server, Visual Studio include ora gli strumenti Redgate Data Tools.

Strumenti inclusi in Visual Studio 2017 Enterprise:

* [Redgate ReadyRoll Core](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs): consente di sviluppare script di migrazione e gestire modifiche del database mediante il controllo del codice sorgente, oltre ad automatizzare in modo sicuro le distribuzioni delle modifiche di database di SQL Server unitamente alle modifiche delle applicazioni.
* [Redgate SQL Prompt Core](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs): consente di scrivere codice SQL più velocemente e con maggiore precisione grazie al supporto del completamento intelligente del codice. SQL Prompt completa automaticamente gli oggetti di database, gli oggetti di sistema e le parole chiave, oltre a offrire suggerimenti per le colonne durante la digitazione. Il codice risultante è quindi più pulito e con meno errori, perché non è necessario ricordare ogni nome di colonna o alias.

Strumenti inclusi in tutte le edizioni di Visual Studio 2017:

* [Redgate SQL Search](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs): consente di aumentare la produttività grazie alla possibilità di individuare rapidamente oggetti e frammenti SQL in più database.

Per altre informazioni, vedere il post di blog [Redgate Data Tools in Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/).

### <a name="net-core"></a>.NET Core

.NET Core è un'implementazione generica, modulare, multi-piattaforma e open source dello Standard .NET e contiene molte delle medesime API di .NET Framework.

La piattaforma .NET Core è costituita da vari componenti, tra cui i compilatori gestiti, il runtime, le librerie di classi base e numerosi modelli applicativi come ASP.NET Core. .NET Core supporta tre sistemi operativi principali: Windows, Linux e macOS. Può essere usata in scenari di dispositivi, cloud e IoT/incorporati.

E include attualmente il supporto di Docker.

**Novità nella versione 15.3**: Visual Studio 2017 versione 15.3 supporta lo sviluppo di .NET Core 2.0. L'uso di .NET Core 2.0 richiede il download e l'installazione separati di SDK 2.0 di .NET Core.

Per altre informazioni, vedere la [pagina della guida di .NET Core.](/dotnet/core/index)

## <a name="games-development"></a>Sviluppo di giochi

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools per Unity

Nell’ambito del carico di lavoro "Sviluppo di giochi per Unity", sono stati inclusi strumenti per semplificare lo sviluppo multipiattaforma per creare giochi 2D e 3D e contenuti interattivi. Puoi creare una sola volta e pubblicare in 21 piattaforme, incluse tutte le piattaforme mobili, WebGL, Mac, computer desktop Windows e Linux, Web o console, tramite Visual Studio 2017 e Unity 5.6.

Per altre informazioni, vedere la pagina [Strumenti di Visual Studio per Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md).

## <a name="ai-development"></a>Sviluppo AI

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools for AI

**Novità della versione 15.5**: usare le funzionalità di produttività di Visual Studio per promuovere sin da subito l'innovazione nel settore dell'intelligenza artificiale. Usare le funzionalità predefinite dell'editor del codice come evidenziazione della sintassi, IntelliSense e formattazione automatica. È possibile testare in modo interattivo l'applicazione per l'apprendimento avanzato nell'ambiente locale usando il debug passo-passo per variabili e modelli locali.

  ![IDE per l'apprendimento avanzato](../ai/media/about/ide.png)

Per altre informazioni, vedere la pagina [Visual Studio Tools for AI](../ai/about-ai-tools.md).

## <a name="whats-next"></a>Passaggi successivi

Visual Studio 2017 viene aggiornato spesso con nuove funzionalità che possono migliorare ulteriormente l'esperienza di sviluppo. Ecco un riepilogo di alcuni degli aggiornamenti più significativi disponibili in anteprima sperimentale:

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)**, un nuovo strumento che consente di condividere una codebase e il relativo contesto con un collega e ottenere collaborazione bidirezionale immediata direttamente all'interno di Visual Studio. Con Live Share un collega può leggere, esplorare, modificare ed eseguire il debug di un progetto condiviso da un altro utente, in modo facile e sicuro.<br><br>Per altre informazioni, vedere le [domande frequenti su Live Share](/visualstudio/liveshare/faq).<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)**, una nuova funzionalità che consente di migliorare lo sviluppo di software usando l'intelligenza artificiale per proporre completamenti del codice con riconoscimento del contesto migliori, guidare gli sviluppatori nella scrittura del codice in base a modelli e stili del team, individuare problemi del codice difficili da intercettare e concentrare le revisioni del codice sulle aree davvero importanti. <br><br>Per altre informazioni, vedere le [domande frequenti su IntelliCode](/visualstudio/intellicode/faq).

Per ulteriori dettagli sulle funzionalità in corso di sviluppo per Visual Studio 2017, vedere la pagina [Visual Studio Roadmap](/visualstudio/productinfo/vs2018-roadmap).

Inoltre, non dimenticare di provare la versione più recente, [Visual Studio 2019](whats-new-visual-studio-2019.md).

## <a name="contact-us"></a>Contatti

È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.

Per inoltrare suggerimenti su come migliorare Visual Studio o per altre informazioni sulle opzioni di supporto tecnico per il prodotto, vedere la pagina [Inviare commenti e suggerimenti](feedback-options.md).

### <a name="report-a-problem"></a>Segnalare un problema

A volte un messaggio non è sufficiente per comunicare il reale impatto di un problema riscontrato. Se si verifica un problema a causa del quale Visual Studio smette di rispondere, si arresta in modo anomalo o un altro problema di prestazioni, è possibile condividere facilmente i passaggi di riproduzione e i file di supporto (ad esempio screenshot e file di traccia e dump dell'heap) con Microsoft usando lo strumento Segnala un problema.  Per altre informazioni su come usare questo strumento, vedere la [pagina Come segnalare un](how-to-report-a-problem-with-visual-studio.md) problema.

## <a name="see-also"></a>Vedi anche

* [Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Novità di Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Novità di Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Novità di C#](/dotnet/csharp/whats-new)
* [Novità per Team Foundation Server](/azure/devops/server/whats-new)
* [Novità di Visual Studio per Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Novità di Visual Studio 2019](whats-new-visual-studio-2019.md)
