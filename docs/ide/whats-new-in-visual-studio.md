---
title: "Novità di Visual Studio 2017 | Microsoft Docs"
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 1e616fb0c223a30152b9cd18e6ea53e989690f9b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="what39s-new-in-visual-studio-2017"></a>Novità di Visual Studio 2017
#### <a name="updated-for-the-154-release"></a>Aggiornato per la versione 15.4
Se si sta valutando l'opportunità di eseguire l'aggiornamento da una versione precedente di Visual Studio, ecco cosa può offrire Visual Studio 2017: produttività senza precedenti per qualsiasi sviluppatore, qualsiasi app e qualsiasi piattaforma. Visual Studio 2017 è perfetto per lo sviluppo di app per Android, iOS, Windows, Linux, Web e cloud. Consente la rapida scrittura del codice, assicura facilità di debug e diagnosi e permette l'esecuzione frequente di test per il rilascio di app affidabili. È inoltre possibile rendere Visual Studio un ambiente "su misura" grazie alla possibilità di creare estensioni personalizzate. Questa versione offre eccezionali vantaggi, inclusi controllo della versione, strumenti e processi Agile ed efficienti funzionalità di collaborazione!

Di seguito è riportato un riepilogo generale delle modifiche apportate dopo la versione precedente, ovvero Visual Studio 2015:

* **Concetti fondamentali ridefiniti**. Una nuova esperienza di installazione offre la possibilità di completare l'installazione più rapidamente e di installare quello che serve all'occorrenza. Indipendentemente dal fatto che si vogliano caricare soluzioni e progetti di grandi dimensioni o lavorare su alcune cartelle di codice o persino su un singolo file di codice, l’avvio di Visual Studio è più veloce. Visual Studio permette anche di rimanere concentrati sul quadro generale, in particolare per i team che adottano la metodologia DevOps.
* **Prestazioni e produttività**. Microsoft si è concentrata sulle funzionalità nuove e moderne di sviluppo per dispositivi mobili, cloud e desktop. Ha inoltre rivolto l’attenzione sul miglioramento complessivo dell'acquisizione, delle prestazioni e delle esperienze di produttività generali per gli sviluppatori. Visual Studio si avvia più velocemente, offre tempi di risposta migliori e usa meno memoria rispetto a prima.
* **Sviluppo di app cloud con Azure**. Un gruppo di strumenti Azure incorporati consentono di creare facilmente app per cloud con tecnologia Microsoft Azure. Visual Studio facilita la configurazione, la compilazione, il debug, l'inserimento in pacchetti e la distribuzione di app e servizi in Azure.
* **Sviluppo di app per dispositivi mobili**. Visual Studio 2017 supporta l'innovazione e permette di ottenere risultati rapidamente con Xamarin, che unifica i requisiti per dispositivi mobili multipiattaforma usando un'unica codebase principale e un singolo set di competenze. È possibile passare allo sviluppo per dispositivi mobili avvalendosi dei team, degli investimenti tecnologici e del codice C# esistenti, per offrire esperienze per consumatori in tempi più brevi e con costi minori del previsto. Ogni passaggio del ciclo di vita dei dispositivi mobili può essere velocizzato per realizzare esperienze per consumatori di alto livello o un portfolio di app di produttività per supportare e agevolare la forza lavoro.
* **Sviluppo multipiattaforma**. Distribuire facilmente software a qualsiasi piattaforma di destinazione. Estendere i processi DevOps a SQL Server con Redgate Data Tools e automatizza in modo sicuro le distribuzioni dei database da Visual Studio. Oppure, utilizzare .NET Core per scrivere app e librerie in modo che vengano eseguite senza modifiche nei sistemi operativi Windows, Linux e macOS. E **novità nella versione 15.3**: supporto di .NET Core 2.0 SDK affiancati.
* **Sviluppo di giochi**. Con Visual Studio Tools per Unity (VSTU) è possibile usare Visual Studio per scrivere script di giochi ed editor in C# e quindi usarne il potente debugger per individuare e correggere gli errori. La versione più recente di VSTU include la colorazione della sintassi per il linguaggio ShaderLab di Unity, un'ottimizzazione delle visualizzazioni del debugger e un miglioramento nella generazione del codice per la procedura guidata MonoBehavior. VSTU integra anche i file di progetto Unity, i messaggi della console e la possibilità di iniziare il gioco in Visual Studio evitando in tal modo di dover passare dall'editor di Unity a Visual Studio e viceversa durante la scrittura del codice.

> [!NOTE]
> Per un elenco completo delle nuove funzionalità in Visual Studio 2017, vedere le [Note sulla versione](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Ecco informazioni più dettagliate su alcuni dei più importanti miglioramenti e delle nuove funzionalità di Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Concetti fondamentali ridefiniti
### <a name="a-new-setup-experience"></a>Una nuova esperienza di installazione

[Scaricare Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) o [verificare i requisiti di sistema di Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Con Visual Studio è ancora più semplice e veloce installare solo le funzionalità necessarie, all'occorrenza. E in più la disinstallazione non presenta problemi.

 La modifica più importante da notare quando si installa Visual Studio è la nuova esperienza di installazione. Nella scheda **Carichi di lavoro** sono visualizzate le opzioni di installazione raggruppate in modo da rappresentare i framework, i linguaggi e le piattaforme più comuni, in grado di supportare qualsiasi attività, dallo sviluppo desktop .NET allo sviluppo di applicazioni C++ in Windows, Linux e iOS.

Scegliere i carichi di lavoro necessari e modificarli all'occorrenza.

 ![Finestra di dialogo di installazione di Visual Studio 2017](../install/media/install-visual-studio-enterprise.png "Schermata dell'installazione di Visual Studio 2017")

Si vuole scegliere i propri componenti anziché usare i carichi di lavoro? Selezionare la scheda **Singoli componenti** nel programma di installazione. Si vuole installare i Language Pack anche senza modificare l'opzione lingua di Windows? Scegliere la scheda **Language Pack** del programma di installazione.  

Per altre informazioni sulla nuova esperienza di installazione, incluse le istruzioni dettagliate per eseguirla, vedere la pagina [Installare Visual Studio](../install/install-visual-studio.md).

### <a name="a-focus-on-accessibility"></a>Informazioni sull'accessibilità
**Nella versione 15.3** sono state apportate oltre 1700 correzioni mirate a migliorare la compatibilità tra Visual Studio e i dispositivi di Assistive Technology usati da molti clienti Microsoft. Molti scenari, inoltre, sono stati resi ancora più compatibili con utilità di lettura dello schermo, temi a contrasto elevato e altri dispositivi di Assistive Technology. Anche il debugger, l'editor e la shell hanno tutti subito considerevoli miglioramenti.

Per altre informazioni, visitare il post di blog sui [miglioramenti dell'accessibilità di Visual Studio 2017 (versione 15.3)](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/).

## <a name="performance-and-productivity"></a>Prestazioni e produttività
### <a name="sign-in-across-multiple-accounts"></a>Accedere a più account  
È stato introdotto in Visual Studio un nuovo servizio di identità che consente di condividere gli account utente in Team Explorer, strumenti di Azure, pubblicazione in Microsoft Store e altri strumenti.

È anche possibile rimanere connessi più a lungo. Non verrà richiesto di accedere nuovamente ogni 12 ore. Per altre informazioni, vedere il post del blog relativo alla [riduzione del numero di richieste di accesso a Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="start-visual-studio-faster"></a>Avviare Visual Studio più rapidamente
Il nuovo strumento Controllo prestazioni di Visual Studio può essere utile per ottimizzare i tempi di avvio dell'IDE. In Controllo prestazioni sono elencate tutte le estensioni e le finestre degli strumenti che potrebbero rallentare l'avvio dell'IDE. È possibile usare la funzionalità per migliorare le prestazioni di avvio, stabilendo quando avviare le estensioni o se le finestre degli strumenti vengono aperte all'avvio.

### <a name="decrease-solution-load-time"></a>Ridurre i tempi di caricamento delle soluzioni
Lavorare su soluzioni che contengono molti progetti non significa che sia necessario usare tutti i file o progetti contemporaneamente. Ora è possibile modificare ed eseguire il debug senza attendere che Visual Studio carichi ogni progetto. Per provare questa procedura con i progetti gestiti, attivare il **caricamento leggero delle soluzioni** da Strumenti-> Opzioni-> Progetti e soluzioni.

  ![Finestra di dialogo Opzioni in Visual Studio 2017](../ide/media/vs2017ide-lightweight-solution-load.png "Visual Studio 2017 - Finestra di dialogo Opzioni - Caricamento leggero di tutte le soluzioni")

### <a name="faster-on-demand-loading-of-extensions"></a>Caricamento su richiesta delle estensioni più rapido
Le estensioni di Visual Studio (così come le estensioni di terze parti) sono state spostate in modo da poter essere caricate su richiesta, invece che all'avvio dell'IDE. Le informazioni sulle estensioni che hanno un impatto sulle prestazioni di avvio, caricamento delle soluzioni e digitazione, sono disponibili in ? -> Gestisci prestazioni di Visual Studio.

  ![Finestra di dialogo Opzioni in Visual Studio 2017](../ide/media/vs2017ide-manage-vs-perf.png "Finestra di dialogo Guida di Visual Studio - Gestisci prestazioni")

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gestire le estensioni con Gestione roaming estensioni
È ancora più semplice configurare ogni ambiente di sviluppo usando le estensioni preferite quando si accede a Visual Studio. Il nuovo strumento Gestione roaming estensioni tiene traccia di tutte le estensioni preferite creando un elenco sincronizzato nel cloud.  

Per visualizzare rapidamente un elenco delle estensioni in Visual Studio, fare clic su Strumenti > Estensioni e aggiornamenti e quindi scegliere Gestione roaming estensioni.

![Visual Studio 2017 - Finestra di dialogo Estensioni e aggiornamenti](../ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 - Strumenti > finestra di dialogo Estensioni e aggiornamenti")

Gestione roaming estensioni tiene traccia di tutte le estensioni installate, ma è possibile scegliere quelle che si vuole aggiungere all'elenco di roaming.

![Visual Studio 2017 - Finestra di dialogo Estensioni e aggiornamenti](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Gestione roaming estensioni")

Quando si usa Gestione roaming estensioni sono disponibili tre tipi di icona nell'elenco:
* ![Icona In roaming](../ide/media/vs2017ide-roamedicon.png "Icona In roaming") ***In roaming***: un'estensione che fa parte dell'elenco di roaming, ma non è installata nel computer.
  Per eseguire l'installazione usare il pulsante **Download**.
* ![Icona In roaming e installata](../ide/media/vs2017ide-roamedinstalledicon.png "Icona In roaming e installata") ***In roaming e installata***: tutte le estensioni incluse nell'elenco di roaming e installate nell'ambiente di sviluppo.
  Se si decide di evitare il roaming, è possibile rimuovere le estensioni usando il pulsante **Arresta roaming**.
* ![Icona Installata](../ide/media/vs2017ide-installedicon.png "Icona Installata") ***Installata***: tutte le estensioni installate nell'ambiente, ma non incluse nell'elenco di roaming.
  Per aggiungere le estensioni all'elenco di roaming, usare il pulsante **Avvia roaming**.

Qualsiasi estensione scaricata quando si è connessi verrà aggiunta all'elenco come **in roaming e installata** e sarà inclusa nell'elenco di roaming. In questo modo sarà possibile accedere all'estensione da qualsiasi computer.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Convalida delle dipendenze architetturali in tempo reale e Live Unit Testing
Mentre si digita il codice nell’editor di testo, Visual Studio invia notifiche in tempo reale in caso di violazioni delle regole di dipendenza architetturale, usando diagrammi di Convalida delle dipendenze, noti anche come diagrammi di livello.

Gli errori vengono visualizzati nell'Elenco errori e le sottolineature ondulate nell'editor di testo mostrano la posizione esatta della violazione. In questo modo si riducono le probabilità di introdurre dipendenze indesiderate.

![Convalida dell'architettura in tempo reale](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Convalida dell'architettura in tempo reale")

#### <a name="live-unit-testing"></a>Live unit testing
In Visual Studio Enterprise 2017, questa funzionalità mostra i risultati dei live unit test e del code coverage direttamente nell'editor mentre si scrive il codice. Funziona con i progetti C# e Visual Basic per .NET Framework e .NET Core e supporta tre framework di test di MSTest, xUnit e NUnit.

![Live Unit Testing](../ide/media/lut-codewindow.png "Esempio della nuova funzionalità Live Unit Testing nell'edizione Enterprise di Visual Studio")

Per altre informazioni, vedere [Introduzione a Live Unit Testing](../test/live-unit-testing-intro.md). Per un elenco delle nuove funzionalità aggiunte in ogni versione di Visual Studio Enterprise 2017, vedere [Novità di Live Unit Testing](../test/live-unit-testing-whats-new.md).

#### <a name="set-up-a-cicd-pipeline-to-run-automated-tests-efficiently"></a>Configurare una pipeline CI/CD per eseguire test automatizzati in modo efficiente
I test automatizzati sono componenti fondamentali di qualsiasi pipeline DevOps. Consente di testare in modo coerente e attendibile e di rilasciare la soluzione in cicli più brevi. I flussi CI/CD (Integrazione continua e Recapito continuo) consentono di rendere più efficiente il processo.

Per altre informazioni sui test automatizzati, vedere il post di blog [CI/CD pipeline for automated tests in DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) (Pipeline CI/CD per test automatizzati in DevOps).

Per altre informazioni sulle novità dell'estensione DevLabs [Strumenti di recapito continuo per Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio), vedere il post di blog [Committing with Confidence: Commit Time Code Quality](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/) (Eseguire il commit in sicurezza: qualità del codice in fase di commit).

### <a name="visual-studio-ide-enhancements"></a>Miglioramenti dell'IDE di Visual Studio
#### <a name="use-new-refactorings"></a>Utilizzare i nuovi refactoring
**Nella versione 15.3** sono stati aggiunti alcuni nuovi refactoring per:
*   Risolvere i conflitti di unione
*   Aggiungere un parametro (da CallSite)
*   Generare sostituzioni
*   Aggiungere un argomento denominato
*   Aggiungere il controllo Null per i parametri
*   Inserire separatori di cifre in valori letterali
*   Modificare la base per i valori letterali numerici (ad esempio da esadecimale a binario)
*   Convertire if-to-switch
*   Rimuovere la variabile non usata

Per maggiori informazioni, consultare la pagina [Refactoring, generazione di codice e azioni rapide in Visual Studio](refactoring-code-generation-quick-actions.md).  

#### <a name="interact-with-git"></a>Interagire con Git
Quando si lavora con un progetto in Visual Studio, è possibile configurare il codice ed eseguirne rapidamente il commit e la pubblicazione in un servizio GIT. È anche possibile gestire i repository GIT tramite i menu visualizzati facendo clic sui pulsanti nell'angolo inferiore destro dell'IDE.

![Visual Studio 2017 interagisce con la finestra di dialogo GIT](../ide/media/vsIDE-GitInteraction.png "Strumenti GIT nell'IDE di Visual Studio")

#### <a name="experience-improved-navigation-controls"></a>Controlli di spostamento migliorati
L'esperienza è stata aggiornata per consentire spostamenti più efficienti e con meno distrazioni.

* **Novità della versione 15.4**: **Vai a definizione (CTRL+clic o F12)** &ndash; Gli utenti che usano il mouse hanno a disposizione un modo più semplice per passare alla definizione di un membro premendo **CTRL** e facendo quindi clic sul membro. È possibile premere **CTRL** e passare il mouse su un simbolo del codice per sottolinearlo e trasformarlo in un collegamento. Per altre informazioni, vedere [Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md).  

* **Vai a implementazione (CTRL+F12)** &ndash; consente di spostarsi da qualsiasi tipo o membro di base alle varie implementazioni corrispondenti.

* **Vai a tutti (CTRL+T o CTRL+,)** &ndash; consente di passare direttamente a qualsiasi dichiarazione di file/tipo/membro/simbolo. È possibile filtrare l'elenco dei risultati o usare la sintassi di query, ad esempio "f Terminericerca" per i file, "t Terminericerca" per i tipi e così via.

 ![Vai a tutti migliorato](../ide/media/vs2017ide-navigation-go-to.png "Esempio della funzionalità Vai a tutti migliorata")

* **Trova tutti i riferimenti (MAIUSC+F12)** &ndash; Con colorazione della sintassi, consente di raggruppare i risultati di Trova tutti i riferimenti in base a una combinazione di progetto, definizione e percorso. È anche possibile "bloccare" i risultati in modo da poter continuare la ricerca di altri riferimenti senza perdere i risultati originali.

 ![Nuovo strumento Trova tutti i riferimenti](../ide/media/vs2017ide-find-all-references.png "Esempio del nuovo strumento Trova tutti i riferimenti")

* **Visualizzatore di struttura** &ndash; Linee grigie verticali punteggiate (guide di rientro) che fungono da punti di riferimento nel codice per fornire informazioni di contesto all'interno del frame di visualizzazione. Tali guide sono incluse nei famosi Productivity Power Tools. È possibile usarle per visualizzare e individuare il blocco di codice attivo in qualsiasi momento, senza dover scorrere. Al passaggio del mouse sulle linee viene visualizzata una descrizione comando che mostra l'apertura del blocco e dei relativi elementi padre. Questa funzionalità è disponibile per tutti i linguaggi supportati da grammatiche TextMate, nonché per C#, Visual Basic e XAML.  

![Visualizzatore di struttura di Visual Studio 2017](../ide/media/vsIDE-StructureVisualizer.png "Visualizzatore di struttura in Visual Studio")

Per altre informazioni sulle nuove funzionalità per la produttività, vedere il post di blog [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) (Produttività in Visual Studio 2017) di Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++
Sono stati introdotti numerosi miglioramenti in Visual Studio, tra cui la distribuzione delle istruzioni di base di C++ con Visual Studio, l'aggiornamento del compilatore aggiungendo il supporto avanzato per le funzionalità di C++11 e C++, l'aggiunta e l'aggiornamento di funzionalità nelle librerie di C++. Sono stati anche migliorati i carichi di lavoro di installazione, le prestazioni dell'IDE di C++ e altro.

Sono stati anche corretti più di 250 bug e problemi nel compilatore e negli strumenti, molti dei quali sono stati segnalati dai clienti attraverso [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

Per informazioni dettagliate, vedere la pagina [Novità di Visual C++ in Visual Studio 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  

### <a name="debugging-and-diagnostics"></a>Debug e diagnostica
#### <a name="run-to-click"></a>Eseguire fino alla riga selezionata:
È ora possibile spostarsi più facilmente in avanti durante il debug senza impostare un punto di interruzione in corrispondenza della riga desiderata. Quando il debugger è interrotto, è sufficiente fare clic sull'icona visualizzata accanto alla riga di codice. Il codice verrà eseguito e si interromperà in corrispondenza di tale riga la volta successiva che viene raggiunta nel percorso del codice.

![Debug in Visual Studio 2017 - Esecuzione fino alla riga selezionata](../ide/media/vs2017ide-RunToClick.png "Esecuzione fino alla riga selezionata in debug e diagnostica di Visual Studio")

#### <a name="the-new-exception-helper"></a>Nuovo supporto eccezione:
Il nuovo Helper eccezioni consente di visualizzare immediatamente informazioni sulle eccezioni. Le informazioni vengono visualizzate in un formato compatto con accesso immediato alle eccezioni interne. Durante la diagnostica di NullReferenceException è possibile individuare rapidamente i riferimenti Null direttamente nell'Helper eccezioni.

![Finestra di dialogo del nuovo Helper eccezioni in Visual Studio](../ide/media/vs2017ide-ExceptionHelper.png "Finestra di dialogo del nuovo Helper eccezioni")

Per altre informazioni, vedere il post del blog relativo all'[uso del nuovo supporto eccezione in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

## <a name="cloud-app-development-with-azure"></a>Sviluppo di app cloud con Azure
### <a name="azure-functions-tools"></a>Strumenti per Funzioni di Azure
Nell’ambito del carico di lavoro "Sviluppo di Azure", sono stati inclusi strumenti che consentono di sviluppare funzioni di Azure con librerie pre-compilate di classe C#. È possibile compilare, eseguire ed effettuare il debug nel computer di sviluppo locale e pubblicare direttamente in Azure da Visual Studio.

Per altre informazioni, vedere la pagina [Strumenti delle Funzioni di Azure per Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs).

## <a name="mobile-app-development"></a>Sviluppo di app per dispositivi mobili
### <a name="xamarin"></a>Xamarin
Nell’ambito del carico di lavoro "Sviluppo per dispositivi mobili con .NET", gli sviluppatori esperti in C#, .NET e Visual Studio possono recapitare App Android, iOS e Windows native con Xamarin. Gli sviluppatori potranno trarre vantaggio dalla stessa potenza e produttività quando lavorano con Xamarin per le app per dispositivi mobili, incluso il debug remoto nei dispositivi Android, iOS e Windows,&mdash;senza dover apprendere linguaggi di codifica nativi come Objective-C o Java.

Per altre informazioni, vedere la pagina [Visual Studio e Xamarin](../cross-platform/visual-studio-and-xamarin.md).

### <a name="entitlements-editor"></a>Editor dei titoli
**Novità nella versione 15.3**: per le esigenze di sviluppo di iOS, è stato aggiunto un editor dei diritti autonomo. Include un'interfaccia utente intuitiva di agevole esplorazione. Per avviare il programma, fare doppio clic sul file entitlements.plist.

![Editor dei diritti per Xamarin](../ide/media/xamarin-entitlements-editor.png "eEditor dei diritti per Xamarin")

## <a name="cross-platform-development"></a>Sviluppo di più piattaforme
### <a name="redgate-data-tools"></a>Redgate Data Tools
Per estendere le funzionalità DevOps all'ambiente di sviluppo di database SQL Server, Visual Studio include ora gli strumenti Redgate Data Tools.

Strumenti inclusi in Visual Studio 2017 Enterprise:
- [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs): consente di sviluppare script di migrazione e gestire modifiche del database mediante il controllo del codice sorgente, oltre ad automatizzare in modo sicuro le distribuzioni delle modifiche di database di SQL Server unitamente alle modifiche delle applicazioni.
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs): consente di scrivere codice SQL più velocemente e con maggiore precisione grazie al supporto del completamento intelligente del codice. SQL Prompt completa automaticamente gli oggetti di database, gli oggetti di sistema e le parole chiave, oltre a offrire suggerimenti per le colonne durante la digitazione. Il codice risultante è quindi più pulito e con meno errori, perché non è necessario ricordare ogni nome di colonna o alias.

Strumenti inclusi in tutte le edizioni di Visual Studio 2017:
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs): consente di aumentare la produttività grazie alla possibilità di individuare rapidamente oggetti e frammenti SQL in più database.

Per altre informazioni, vedere il post di blog [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/).

### <a name="net-core"></a>.NET Core
.NET Core è un'implementazione generica, modulare, multi-piattaforma e open source dello Standard .NET e contiene molte delle medesime API di .NET Framework.

La piattaforma .NET Core è costituita da vari componenti, tra cui i compilatori gestiti, il runtime, le librerie di classi base e numerosi modelli applicativi come ASP.NET Core. .NET Core supporta tre sistemi operativi principali: Windows, Linux e macOS. Può essere usata in scenari di dispositivi, cloud e IoT/incorporati.

E include attualmente il supporto di Docker.  

**Novità nella versione 15.3**: Visual Studio 2017 versione 15.3 supporta lo sviluppo di .NET Core 2.0. L'uso di .NET Core 2.0 richiede il download e l'installazione separati di SDK 2.0 di .NET Core.  

Per altre informazioni, vedere la pagina della [Guida .NET Core](https://docs.microsoft.com/dotnet/core/index).

## <a name="games-development"></a>Sviluppo di giochi
### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools per Unity
Nell’ambito del carico di lavoro "Sviluppo di giochi per Unity", sono stati inclusi strumenti per semplificare lo sviluppo multipiattaforma per creare giochi 2D e 3D e contenuti interattivi. Puoi creare una sola volta e pubblicare in 21 piattaforme, incluse tutte le piattaforme mobili, WebGL, Mac, computer desktop Windows e Linux, Web o console, tramite Visual Studio 2017 e Unity 5.6.

Per altre informazioni, vedere la pagina [Strumenti di Visual Studio per Unity](../cross-platform/visual-studio-tools-for-unity.md).

## <a name="talk-to-us"></a>Comunicazioni con Microsoft  
 È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.  

Per inoltrare suggerimenti su come migliorare Visual Studio o per segnalare un problema, consultare la pagina [Comunicazioni con Microsoft](../ide/talk-to-us.md).  

### <a name="report-a-problem"></a>Segnalare un problema  
 A volte un messaggio non è sufficiente per comunicare il reale impatto di un problema riscontrato. Se si verifica un blocco, un arresto anomalo del sistema o un altro problema di prestazioni, è possibile condividere facilmente con Microsoft la procedura per riprodurre il problema e i file di supporto, ad esempio screenshot e file dump di traccia e heap, usando lo strumento **Segnala un problema**. Per altre informazioni su come utilizzare questo strumento, vedere la pagina relativa alla [segnalazione dei problemi](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Tenere traccia del problema in Connect  
 Se si desidera tenere traccia dello stato del commento inviato su Visual Studio, passare al sito [Connect](http://connect.microsoft.com/) e segnalare il bug. Dopo aver effettuato la segnalazione è possibile tornare a Connect per tenere traccia dello stato.  

## <a name="see-also"></a>Vedere anche
* [Note sulla versione di Visual Studio 2017](https://www.visualstudio.com/news/vs2015-vs)
* [Novità di Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Novità di C#](https://docs.microsoft.com/dotnet/csharp/csharp-7)  
* [What's New for Team Foundation Server](https://www.visualstudio.com/docs/whats-new) (Novità per Team Foundation Server)
* [Novità di Visual Studio per Mac](https://www.visualstudio.com/vs/visual-studio-mac/)
