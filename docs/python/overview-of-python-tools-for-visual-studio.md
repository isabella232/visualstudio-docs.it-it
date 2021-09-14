---
title: Supporto di Python in Visual Studio in Windows
titleSuffix: ''
description: Riepilogo delle funzionalità Python di Visual Studio, il miglior ambiente IDE Python per Windows, noto anche come Python Tools for Visual Studio (PTVS).
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 380a9a038ff48818fec213c86283328e01beb0d9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634339"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Usare Python in Visual Studio in Windows

Python è un linguaggio di programmazione molto diffuso affidabile, flessibile, facile da imparare, il cui uso è gratuito in tutti i sistemi operativi e supportato sia da un'attiva community di sviluppatori che da numerose librerie gratuite. Python supporta tutte le modalità di sviluppo, tra cui applicazioni Web, servizi Web, app desktop, scripting e calcolo scientifico. Viene usato in molte università, nonché da scienziati e sviluppatori, professionisti e non professionisti. Per altre informazioni sul linguaggio, vedere [python.org](https://www.python.org) e [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python per principianti).

Visual Studio è un ambiente IDE Python avanzato per Windows che offre supporto [open source](https://github.com/Microsoft/ptvs) per il linguaggio Python tramite i carichi di lavoro **Sviluppo Python** e **Data science** (Visual Studio 2017 e versioni successive). Visual Studio offre anche l'estensione gratuita Python Tools for Visual Studio (Visual Studio 2015 e versioni precedenti).

Python non è attualmente supportato in Visual Studio per Mac, ma è disponibile su Mac e Linux tramite Visual Studio Code (vedere le [domande e risposte](#questions-and-answers)).

Attività iniziali

- Seguire le istruzioni [di installazione](installing-python-support-in-visual-studio.md) per configurare il carico di lavoro Python.
- Acquisire familiarità con le funzionalità Python di Visual Studio tramite le sezioni in questo articolo.
::: moniker range="vs-2017"
- Eseguire una o più guide introduttive per creare un progetto. In caso di dubbi, iniziare con [Creare un'app Web con Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Eseguire una o più guide introduttive per creare un progetto. In caso di dubbi, iniziare con Avvio [rapido:](quickstart-05-python-visual-studio-open-folder.md) Aprire ed eseguire codice Python in una cartella o Creare un'app Web [con Flask.](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)
::: moniker-end
- Seguire l'esercitazione [Usare Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) per un'esperienza completa.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio supporta Python versione 2.7, nonché dalla versione 3.5 alla 3.7. Sebbene sia possibile usare Visual Studio per modificare anche il codice scritto in altre versioni di Python, queste non sono ufficialmente supportate e alcune funzionalità, tra cui IntelliSense e il debug, potrebbero non funzionare. Il supporto per Python versione 3.8 è ancora in fase di sviluppo. Dettagli specifici sul supporto sono visibili in questo problema di rilevamento [in GitHub](https://github.com/microsoft/PTVS/issues/5822).
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Supporto di più interpreti

La finestra **Ambienti Python** di Visual Studio (illustrata di seguito in un'ampia visualizzazione espansa) rappresenta un'unica posizione da cui gestire tutti gli ambienti Python globali, gli ambienti Conda e gli ambienti virtuali. Visual Studio rileva automaticamente le installazioni di Python in posizioni standard e consente di configurare installazioni personalizzate. Per ogni ambiente, è possibile gestire pacchetti, aprire una finestra interattiva specifica e accedere alle cartelle dell'ambiente con la massima facilità.

::: moniker range="vs-2017"
![Visualizzazione espansa della finestra Ambienti Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Visualizzazione espansa della finestra Ambienti Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Usare il comando **Apri finestra interattiva** per eseguire in modo interattivo Python all'interno del contesto di Visual Studio. Usare il comando **Apri in PowerShell** per aprire una finestra di comando separata nella cartella dell'ambiente selezionato. Da tale finestra di comando è possibile eseguire qualsiasi script Python.

Per altre informazioni:

- [Gestire gli ambienti Python](managing-python-environments-in-visual-studio.md)
- [Informazioni di riferimento sulle schede della finestra Ambienti Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Modifica avanzata, IntelliSense e comprensione del codice

Visual Studio mette a disposizione un editor Python di prima classe, con funzionalità di colorazione della sintassi, completamento automatico in tutto il codice e in tutte le librerie, formattazione del codice, supporto per la firma, refactoring, rilevamento di errori con Lint e suggerimenti relativi al tipo. Visual Studio offre anche funzionalità univoche come visualizzazione classi, **Vai a definizione,** **Trova tutti i** riferimenti e frammenti di codice. L'integrazione diretta [finestra interattiva](#interactive-window) consente di sviluppare rapidamente codice Python già salvato in un file.

![Completamento di codice Python in Visual Studio](media/code-editing-completions-simple.png)

Per altre informazioni:

- Documentazione: [Modificare il codice Python](editing-python-code-in-visual-studio.md)
- Documentazione: [Formattare il codice](formatting-python-code.md)
- Documentazione: [Effettuare il refactoring del codice](refactoring-python-code.md)
- Documentazione: [Usare un linter](linting-python-code.md)
- Documenti generali sulle funzionalità di Visual Studio: [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Finestra Interattiva

Per ogni ambiente Python noto a Visual Studio, è possibile aprire facilmente lo stesso ambiente interattivo (REPL, ciclo Read–Eval–Print) per un interprete Python direttamente all'interno di Visual Studio, anziché usare un prompt dei comandi separato. È anche possibile passare facilmente da un ambiente all'altro. Per aprire un prompt dei comandi separato, selezionare un ambiente nella finestra **Ambienti Python**, quindi selezionare il comando **Apri in PowerShell** come illustrato in precedenza in [Supporto di più interpreti](#support-for-multiple-interpreters).

![Finestra interattiva di Python in Visual Studio](media/interactive-window.png)

Visual Studio offre anche una stretta integrazione tra l'editor di codice Python e la **finestra** interattiva. Il **tasto di** scelta rapida CTRL INVIO invia facilmente la riga di codice corrente (o blocco di codice) nell'editor alla finestra interattiva, quindi passa alla riga successiva +  (o blocco di codice).  **CTRL** + **Invio** consente di eseguire facilmente il codice un'istruzione alla volta senza dover eseguire il debugger. È anche possibile inviare  il codice selezionato alla finestra Interattiva con la stessa sequenza di tasti e incollare facilmente il codice dalla **finestra** interattiva nell'editor. Insieme, queste funzionalità consentono di descrizione dei dettagli  per un segmento di codice nella finestra interattiva e di salvare facilmente i risultati in un file nell'editor.

Visual Studio supporta anche IPython/Jupyter nel ciclo REPL, compresi tracciati inline, .NET e Windows Presentation Foundation (WPF).

Per altre informazioni:

- [finestra interattiva](python-interactive-repl-in-visual-studio.md)
- [IPython in Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Sistema del progetto e modelli di progetto e di elemento

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019 supporta l'apertura di una cartella contenente codice Python e l'esecuzione del codice senza creare file di progetto e soluzione di Visual Studio. Per altre informazioni, vedere [Avvio rapido: Aprire ed eseguire codice Python in una cartella.](quickstart-05-python-visual-studio-open-folder.md) L'uso di un file di progetto offre tuttavia alcuni vantaggi, come illustrato in questa sezione.
::: moniker-end

Visual Studio consente di gestire la complessità di un progetto man mano che le dimensioni di questo aumentano. Un *progetto di Visual Studio* è molto più di una struttura di cartelle, poiché al suo interno sono presenti informazioni sull'uso dei diversi file e sulla loro interazione reciproca. Visual Studio consente di distinguere codice dell'app, codice di test, pagine Web, JavaScript, script di compilazione e così via, abilitando le funzionalità appropriate per ogni file. Una soluzione di Visual Studio, poi, consente di gestire più progetti correlati, ad esempio un progetto Python e un progetto di estensione C++.

![Soluzione di Visual Studio contenente progetti sia Python che C++](media/projects-solution-explorer-two-projects.png)

Grazie ai modelli di progetto e di elemento, è possibile automatizzare il processo di impostazione di tipi di progetti e file diversi, risparmiando tempo prezioso ed evitando di gestire dettagli complessi e soggetti a errori. Visual Studio mette a disposizione modelli per progetti Web, Azure, data science, console e altri tipi di progetti, insieme a modelli per file quali classi, unit test, configurazioni Web di Azure, HTML e persino app Django.

[![Modelli di progetto ed elemento Python in Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Per altre informazioni:

- Documenti: [Gestire i progetti Python](managing-python-projects-in-visual-studio.md)
- Documenti: [Riferimento ai modelli di elemento](python-item-templates.md)
- Documenti: [Modelli di progetto Python](managing-python-projects-in-visual-studio.md#project-templates)
- Documenti: [Usare C++ e Python](working-with-c-cpp-python-in-visual-studio.md)
- Documenti generali sulle funzionalità di Visual Studio: [Modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Documentazione Visual Studio funzionalità generali: [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Debug con funzionalità complete

Uno dei punti di forza di Visual Studio è un debugger avanzato. Specificamente per Python, Visual Studio include funzioni di debug in modalità mista Python/C++, debug remoto in Linux, debug nella finestra **Interattiva** e debug di unit test Python.

![Debugger di Visual Studio per Python con un'eccezione in una finestra popup](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
In Visual Studio 2019, è possibile eseguire il codice ed eseguirne il debug senza un file di progetto di Visual Studio. Per [un esempio, vedere Avvio rapido: Aprire ed eseguire codice Python in](quickstart-05-python-visual-studio-open-folder.md) una cartella.
::: moniker-end

Per altre informazioni:

- Documentazione: [Eseguire il debug di Python](debugging-python-in-visual-studio.md)
- Documenti: [Debug in modalità mista Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Documenti: [Debug remoto in Linux](debugging-python-code-on-remote-linux-machines.md)
- Documentazione Visual Studio funzionalità: [Presentazione delle funzionalità del debugger Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Strumenti di profilatura con funzionalità complete di creazione di report

La profilatura esplora come viene impiegato il tempo all'interno dell'applicazione. Visual Studio supporta la profilatura con interpreti basati su CPython e include la possibilità di confrontare le prestazioni tra esecuzioni diverse della profilatura.

[![Visual Studio profiler per un progetto Python](media/profiling-results.png)](media/profiling-results.png#lightbox)

Per altre informazioni:

- Documenti: [Strumenti di profilatura di Python](profiling-python-code-in-visual-studio.md)
- Documenti generali sulle funzionalità di Visual Studio: [Panoramica delle funzionalità di profilatura](../profiling/profiling-feature-tour.md) (non tutte le funzionalità di profilatura di Visual Studio sono disponibili per Python).

## <a name="unit-testing-tools"></a>Strumenti per unit test

Individuare, eseguire e gestire i test in Esplora Visual Studio **ed** eseguire facilmente il debug di unit test.

![Debug di uno unit test Python in Visual Studio](media/unit-test-debugging.png)

Per altre informazioni:

- Documenti: [Strumenti di esecuzione di unit test per Python](unit-testing-python-in-visual-studio.md)
- Documenti generali sulle funzionalità di Visual Studio: [Eseguire unit test del codice](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Azure SDK per Python

Le librerie di Azure per Python semplificano l'utilizzo dei servizi di Azure da applicazioni Windows, Mac OS X e Linux. È possibile usarle per creare e gestire risorse di Azure, nonché per connettersi ai servizi di Azure. 

Per altre informazioni, vedere [Azure SDK per Python](/azure/python/) e [Librerie di Azure per Python](/azure/python/python-sdk-azure-overview).

## <a name="questions-and-answers"></a>Domande e risposte

**D. Il supporto python è disponibile con Visual Studio per Mac?**

A. Non in questo momento, ma è possibile votare a favore della richiesta nella [community degli sviluppatori](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). La documentazione di [Visual Studio per Mac](/visualstudio/mac/) identifica gli attuali tipi di sviluppo che supporta. Nel frattempo, Visual Studio Code su Windows, Mac e Linux [funziona bene con Python mediante le estensioni disponibili](https://code.visualstudio.com/docs/languages/python).

**D. Cosa è possibile usare per compilare l'interfaccia utente con Python?**

A. La proposta migliore in questo campo è il [progetto Qt](https://www.qt.io/qt-for-application-development/), con le associazioni per Python note come [PySide (l'associazione ufficiale)](https://wiki.qt.io/PySide) (vedere anche [PySide downloads](https://download.qt.io/official_releases/pyside/.)) e [PyQt](https://wiki.python.org/moin/PyQt). Attualmente il supporto di Python in Visual Studio non include strumenti specifici per lo sviluppo dell'interfaccia utente.

**D. Un progetto Python può produrre un eseguibile autonomo?**

A. Python è in genere un linguaggio interpretato, con cui il codice viene eseguito su richiesta in un ambiente in grado di supportare Python, ad esempio Visual Studio e i server Web. Visual Studio attualmente non offre la possibilità di creare un file eseguibile autonomo, ovvero un programma con un interprete Python incorporato. Tuttavia, la community di Python offre diversi modi di creare file eseguibili, come descritto in [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython supporta anche l'incorporamento all'interno di un'applicazione nativa, come descritto nel post di blog [Using CPython's embeddable zip file](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Supporto funzionalità

Le funzionalità di Python possono essere installate nelle edizioni seguenti di Visual Studio, come descritto nella [guida all'installazione](installing-python-support-in-visual-studio.md):

- [Visual Studio 2019 (tutte le edizioni)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (tutte le edizioni)
- Visual Studio 2015 (tutte le edizioni)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express per il Web, Update 2 o versione successiva
- Visual Studio 2013 Express per Desktop, Update 2 o versione successiva
- Visual Studio 2013 (Professional Edition o versione successiva)
- Visual Studio 2012 (Professional Edition o versione successiva)
- Visual Studio 2010 SP1 (Professional Edition o versione successiva; richiede .NET 4.5)

Visual Studio 2015 e versioni precedenti sono disponibili all'indirizzo [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Le funzionalità vengono supportate e mantenute aggiornate in modo completo solo per la versione più recente di Visual Studio. Le funzionalità sono disponibili nelle versioni precedenti, ma non vengono mantenute aggiornate.

|          Supporto per Python          |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Gestione di più interpreti   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Rilevamento automatico degli interpreti più comuni | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Aggiunta di interpreti personalizzati      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Ambienti virtuali       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Installazione Pip/semplificata         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Sistema del progetto         |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive |      2012 Professional e successive       | 2010 SP1 Professional e successive |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Nuovo progetto da codice esistente | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Mostra tutti i file         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Controllo del codice sorgente         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integrazione di Git         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           In fase di modifica            |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Evidenziazione della sintassi      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Completamento automatico         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Supporto per la firma        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Informazioni rapide          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Visualizzatore oggetti/Visualizzazione classi   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Barra di navigazione        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Vai a definizione       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Passa a          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Trova tutti i riferimenti      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Rientro automatico       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formattazione del codice        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refactoring - Ridenominazione       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refactoring - Estrazione del metodo   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refactoring - Aggiunta/rimozione dell'importazione | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Finestra Interattiva     |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Finestra Interattiva     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IPython con grafici inline | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Desktop               |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Applicazione console/Windows     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| WPF IronPython (con finestra di progettazione XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Windows Form IronPython       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Progetto Web Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Progetto Web Bottle  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Progetto Web Flask  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Progetto Web generico | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Community | 2013 Desktop |       2013 Web       |      2013 Professional e successive       |      2012 Professional e successive       |    2010 SP1 Professional e successive     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Distribuzione in sito Web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Distribuzione in ruolo Web   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Distribuzione in ruolo di lavoro  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Esecuzione nell'emulatore di Azure  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Debug remoto    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Collegamento a Esplora server | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Modelli Django           |   2017+   |   2015   | 2013 Community | 2013 Desktop |       2013 Web       |      2013 Professional e successive       | 2012 Professional e successive | 2010 SP1 Professional e successive |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Debug               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Completamento automatico             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Completamento automatico per CSS e JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Debug                  |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Debug                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Debug senza progetto         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Debug - Collegamento a modifica        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Debug in modalità mista             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Debug remoto (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Finestra Debug interattivo           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profilatura |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profilatura | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Test      |   2017+   |   2015   | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Esplora test | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Eseguire test    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Debug di test   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Il supporto Git per Visual Studio 2012 è incluso nell'estensione Visual Studio Tools for Git, disponibile in [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. Per la distribuzione nel sito Web di Azure è necessario [Azure SDK per .NET 2.1 - Visual Studio 2010 SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids). Visual Studio 2010 non è supportato nelle versioni successive.

1. Per il supporto per il ruolo di lavoro e il ruolo Web di Azure è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) o versione successiva.

1. Per il supporto per il ruolo di lavoro e il ruolo Web di Azure è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) o versione successiva.

1. L'editor di modelli Django in Visual Studio 2013 presenta alcuni problemi noti che vengono risolti installando l'Update 2.

1. Richiede Windows 8 o versione successiva. La finestra **Collega a processo** non è disponibile in Visual Studio 2013 Express per il Web, ma è comunque possibile eseguire il debug remoto del sito Web di Azure usando il comando **Collega debugger (Python)** in **Esplora server**. Il debug remoto richiede [Azure SDK per .NET 2.3 - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) o versione successiva.

1. Richiede Windows 8 o versione successiva. **Il comando Attach Debugger (Python)** in **Esplora server** richiede [Azure SDK per .NET 2.3 - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) o versione successiva.

1. Richiede Windows 8 o versione successiva.
::: moniker-end
