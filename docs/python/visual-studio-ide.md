---
description: L'ambiente di sviluppo integrato (IDE) di Visual Studio è un'area di avvio creativa per Python e altri linguaggi, che consente di modificare il codice, eseguire il debug e il test del codice e quindi pubblicare un'app.
title: Panoramica di Visual Studio per sviluppatori Python
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: a81616e50cc4f7a3aab5fc4ccfa52d378eeb34d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027279"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Benvenuti all'IDE di Visual Studio | Python

L'*ambiente di sviluppo integrato (IDE)* di Visual Studio è un'area di avvio creativa per Python e altri linguaggi, che consente di modificare il codice, eseguire il debug e il test del codice e quindi pubblicare un'app. Un ambiente di sviluppo integrato (IDE) è un programma con numerose funzionalità che può essere usato per molti aspetti dello sviluppo software. A differenza dell'editor e del debugger standard disponibili nella maggior parte degli ambienti IDE, Visual Studio include strumenti di completamento codice, ambienti REPL interattivi e altre funzionalità che semplificano il processo di sviluppo del software.

[![Visual Studio con un progetto Python](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Questa immagine presenta Visual Studio con un progetto Python aperto e varie finestre degli strumenti di base che probabilmente verranno usate:

- [**Esplora soluzioni**](../ide/solutions-and-projects-in-visual-studio.md) (in alto a destra) consente di visualizzare, esplorare e gestire i file di codice. **Esplora soluzioni** possibile organizzare il codice raggruppando i file in [soluzioni e progetti](../get-started/tutorial-projects-solutions.md).
  - Oltre a **Esplora soluzioni** è disponibile [**Ambienti Python**](managing-python-environments-in-visual-studio.md), in cui è possibile gestire i diversi interpreti Python installati nel computer.

  ::: moniker range=">=vs-2019"
  - È anche possibile aprire ed eseguire codice Python in una cartella senza creare file di progetto e soluzione di Visual Studio. Per altre informazioni, vedere [Avvio rapido: Aprire ed eseguire codice Python in una cartella](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- La [finestra dell'editor](../ide/writing-code-in-the-code-and-text-editor.md) (al centro), uno degli strumenti più usati, visualizza il contenuto dei file. In questa finestra è possibile [modificare il codice Python](editing-python-code-in-visual-studio.md), spostarsi nella struttura del codice e impostare punti di interruzione durante le sessioni di debug. Con Python è anche possibile selezionare codice e premere CTRL+INVIO per eseguire il codice selezionato in una [finestra REPL interattiva](python-interactive-repl-in-visual-studio.md).

- La finestra [Output](../ide/reference/output-window.md) (in basso al centro) è la finestra in cui Visual Studio invia le notifiche, ad esempio messaggi di errore e di debug, avvisi, messaggi di stato di pubblicazione e altro. Ogni origine dei messaggi ha una scheda separata.
  - Una [finestra REPL interattiva di Python](python-interactive-repl-in-visual-studio.md) viene visualizzata nella stessa area della finestra Output.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (in basso a destra) consente di tenere traccia degli elementi di lavoro e di condividere il codice con altri utenti usando tecnologie di controllo della versione come [Git](https://git-scm.com/) e [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true).

## <a name="editions"></a>Edizioni

Visual Studio è disponibile per Windows e Mac, ma il supporto di Python è disponibile solo in Visual Studio per Windows.

Sono disponibili tre edizioni di Visual Studio Windows: Community, Professional e Enterprise. Vedere [Confronta gli IDE di Visual Studio](https://visualstudio.microsoft.com/vs/compare/) per informazioni sulle funzionalità supportate in ogni edizione.

## <a name="popular-productivity-features"></a>Funzionalità di produttività più note

Le funzionalità più note di Visual Studio che offrono una maggiore produttività nello sviluppo del software includono:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense è un termine che indica diverse funzionalità che visualizzano le informazioni sul codice direttamente nell'editor e, in alcuni casi, scrivono automaticamente piccole parti di codice. È come se si avesse a disposizione la documentazione di base all'interno dell'editor senza dover cercare le informazioni sul tipo altrove. Le funzionalità IntelliSense variano in base al linguaggio; l'articolo [Modifica del codice Python](editing-python-code-in-visual-studio.md#intellisense) contiene informazioni dettagliate per Python. La figura seguente mostra come IntelliSense visualizza un elenco di membri per un tipo:

   ![Completamento dei membri con Visual Studio IntelliSense](media/code-editing-completions-simple.png)

- [Refactoring](refactoring-python-code.md)

   Se si fa clic con il pulsante destro del mouse su una sezione di codice e si seleziona **Azioni rapide e refactoring**, Visual Studio visualizza operazioni come la ridenominazione intelligente delle variabili, l'estrazione di una o più righe di codice in un nuovo metodo, la modifica dell'ordine dei parametri dei metodi e altro ancora.

   ![Effettuare il refactoring in Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Rilevamento di errori con Lint](refactoring-python-code.md)

   Il rilevamento errori con Lint trovare problemi comuni nel codice Python e consiglia soluzioni di creazione di codice Python ottimali.

   ![Comando PyLint nel menu di scelta rapida per i progetti Python](media/code-pylint-command.png)

- Casella di ricerca

   La quantità di menu, opzioni e proprietà disponibili in Visual Studio può sembrare a volte eccessiva. La casella di ricerca è un ottimo modo per trovare rapidamente quello che serve in Visual Studio. Quando si inizia a digitare il nome di un elemento da cercare, Visual Studio visualizza risultati che consentono di passare esattamente all'elemento desiderato. Se si vuole aggiungere una funzionalità a Visual Studio, ad esempio il supporto di un altro linguaggio di programmazione, la casella di ricerca fornisce risultati che consentono di aprire il programma di installazione di Visual Studio per installare un carico di lavoro o un singolo componente.

   ![Casella di ricerca in Visual Studio](media/tour-ide-quick-launch.png)

- Controllo ortografia durante la digitazione e [azioni rapide](../ide/quick-actions.md)

   Il controllo ortografia durante la digitazione visualizza sottolineature ondulate che segnalano errori o problemi potenziali nel codice in tempo reale. Questi indizi visivi consentono di risolvere i problemi immediatamente senza attendere che l'errore venga rilevato durante la compilazione o quando si esegue il programma. Se si passa il mouse su una linea ondulata, vengono visualizzate informazioni aggiuntive sull'errore. Sul margine sinistro può essere visualizzata anche una lampadina con le azioni, denominate azioni rapide, per risolvere l'errore.

   ![Controllo ortografia durante la digitazione in Visual Studio](media/tour-ide-squiggles.png)

- [Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md)

   La funzionalità **Vai a definizione** consente di passare direttamente alla posizione in cui viene definita una funzione o un tipo. Il comando **Visualizza definizione** presenta la definizione in una finestra senza aprire un file separato. Anche il comando **Trova tutti i riferimenti** è utile per trovare dove viene definito e usato qualsiasi identificatore specificato.

   ![Comandi di spostamento per il codice](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Potenti funzionalità per Python

::: moniker range=">=vs-2019"
- [Eseguire codice senza un progetto](quickstart-05-python-visual-studio-open-folder.md)

    A partire da Visual Studio 2019 è possibile aprire una cartella contenente codice Python per usufruire di funzionalità quali IntelliSense e debug, senza dover creare un progetto di Visual Studio per il codice.
::: moniker-end

- [Collaborare usando Visual Studio](/visualstudio/liveshare/)

    Visual Studio Live Share consente di modificare ed eseguire il debug in collaborazione con altri utenti in tempo reale, indipendentemente dal linguaggio di programmazione in uso o dai tipi di app che si sta creando.

- [Finestra REPL interattiva per Python](python-interactive-repl-in-visual-studio.md)

    In Visual Studio è disponibile una finestra REPL (Read-Evaluate-Print Loop) per ogni ambiente Python, che costituisce un miglioramento rispetto alla funzionalità REPL disponibile con *python.exe* dalla riga di comando. Nella finestra **interattiva** è possibile immettere codice Python arbitrario e visualizzare immediatamente i risultati.

    ![Finestra interattiva di Python](media/interactive-window.png)

- [Debug](debugging-python-in-visual-studio.md)

    Visual Studio offre un'esperienza di debug completa per Python, inclusa la connessione ai  processi in esecuzione, la valutazione delle espressioni nelle finestre **Espressioni** di controllo e Controllo immediato, l'ispezione di variabili locali, punti di interruzione, istruzioni di esecuzione/uscita/uscita/over, **l'istruzione Set Next** e altro ancora. È anche possibile eseguire il debug di codice Python remoto in esecuzione su computer Linux.

    ![Debug di Python in Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Interazione con C++](working-with-c-cpp-python-in-visual-studio.md)

    Molte librerie create per Python sono scritte in C++ per garantire prestazioni ottimali. Visual Studio include strumenti avanzati per lo sviluppo di estensioni C++, tra cui il [debug in modalità mista](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Debug in modalità mista di Python e C++ in un'unica soluzione](media/mixed-mode-debugging.png)

- [Profilatura](profiling-python-code-in-visual-studio.md)

    Quando si usa un interprete basato su CPython, è possibile valutare le prestazioni del codice Python in Visual Studio.

    ![Report di prestazioni del profiler](media/profiling-results.png)

- [Testing unità](unit-testing-python-in-visual-studio.md)

    Visual Studio offre supporto integrato per il rilevamento, l'esecuzione e il debug di unit test nel contesto dell'IDE.

    ![Unit test con stato del test non superato](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Passaggi successivi

Per approfondire altri aspetti di Python in Visual Studio, eseguire una delle esercitazioni seguenti:

> [!div class="nextstepaction"]
> [Guida introduttiva: Creare un'app Web con Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [usare Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Introduzione al framework Web Django in Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Introduzione al framework Web Flask in Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Vedi anche

- Scoprire [altre funzionalità di Visual Studio](../ide/advanced-feature-overview.md)
- Visitare [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Leggere il [Blog di Visual Studio](https://devblogs.microsoft.com/visualstudio/)
