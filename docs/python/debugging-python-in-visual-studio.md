---
title: Debug del codice Python
description: Visual Studio offre funzionalità di debug avanzate per il codice Python, tra cui l'impostazione dei punti di interruzione, l'esecuzione di istruzioni, il controllo dei valori, l'analisi delle eccezioni e il debug nella finestra interattiva.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3ef8fc7ef3de032d4c4fba25e0e3b64a47b76ac1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636980"
---
# <a name="debug-your-python-code"></a>Eseguire il debug del codice Python

Visual Studio offre un'esperienza di debug completa per Python, tra cui il collegamento a  processi in esecuzione, la valutazione delle espressioni nelle finestre **Espressioni** di controllo e Controllo immediato, l'analisi di variabili locali, punti di interruzione, istruzioni step-in/out/over, **Set Next Statement** e altro ancora.

Vedere anche gli articoli seguenti sul debug nei vari scenari:

- [Debug remoto di Linux](debugging-python-code-on-remote-linux-machines.md)
- [Debug in modalità mista di Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Simboli per il debug in modalità mista](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python in Visual Studio supporta il debug senza un progetto. Con un file Python autonomo aperto, fare clic con il pulsante destro del mouse nell'editor, scegliere Avvia con debug e Visual Studio avvia lo script con l'ambiente predefinito globale (vedere [Ambienti Python)](managing-python-environments-in-visual-studio.md)e nessun argomento. Da questo momento però sono disponibili tutte le opzioni di debug.
>
> Per controllare l'ambiente e gli argomenti, creare un progetto per il codice. Questa operazione viene eseguita facilmente con il modello di progetto [Da codice Python esistente](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files).

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Debug di base

Il flusso di lavoro del debug di base include l'impostazione dei punti di interruzione, l'esecuzione di codice istruzione per istruzione, il controllo dei valori e la gestione delle eccezioni, come descritto nelle sezioni seguenti.

Una sessione di debug viene avviata con il **comando Debug** Avvia debug, il pulsante Avvia sulla barra degli strumenti o il tasto  >   **F5.**  Queste azioni eseguono il file di avvio del progetto (visualizzato in grassetto in **Esplora soluzioni**) con l'ambiente attivo del progetto ed eventuali argomenti della riga di comando o percorsi di ricerca specificati in **Proprietà progetto** (vedere [Opzioni di debug del progetto](#project-debugging-options)). In Visual Studio 2017 versione 15.6 e versioni successive viene generato un avviso se non è impostato un file di avvio. Nelle versioni precedenti è possibile che venga visualizzata una finestra di output con l'interprete Python in esecuzione o che la finestra di output venga visualizzata brevemente e poi scompaia. In qualsiasi caso, fare clic con il pulsante destro del mouse sul file appropriato e scegliere **Imposta come file di avvio**.

> [!Note]
> Il debugger viene sempre avviato con l'ambiente Python attivo per il progetto. Per cambiare ambiente, attivarne uno diverso come descritto in [Selezionare un ambiente Python per un progetto](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Punti di interruzione

Con i punti di interruzione l'esecuzione del codice viene arrestata in corrispondenza di un punto contrassegnato per consentire il controllo dello stato del programma. Impostare i punti di interruzione facendo clic sul margine sinistro dell'editor di codice oppure facendo clic con il pulsante destro del mouse su una riga di codice e scegliendo **Punto** di  >  **interruzione Inserisci punto di interruzione**. Accanto a ogni riga con un punto di interruzione verrà visualizzato un punto rosso.

![Punti di interruzione visualizzati in Visual Studio](media/debugging-breakpoints.png)

Facendo clic sul punto rosso o facendo clic con il pulsante destro del mouse sulla riga di codice e scegliendo **Punto** di interruzione Elimina punto di  >  **interruzione** viene rimosso il punto di interruzione. È anche possibile disabilitarlo senza rimuoverlo usando il comando **Punto** di interruzione  >  **Disabilita punto di** interruzione.

> [!Note]
> Alcuni punti di interruzione in Python possono risultare sorprendenti per gli sviluppatori che hanno lavorato con altri linguaggi di programmazione. In Python l'intero file è codice eseguibile, di conseguenza Python esegue il file quando viene caricato per elaborare tutte le definizioni di classe o di funzione di primo livello. Se è stato impostato un punto di interruzione, è possibile che l'esecuzione del debugger si interrompa durante una dichiarazione di classe. Questo comportamento è corretto, anche se è a volte sorprendente.

È possibile personalizzare le condizioni per l'attivazione di un punto di interruzione, ad esempio per interrompere l'esecuzione solo quando una variabile viene impostata su un valore o su un intervallo di valori specifico. Per impostare le condizioni, fare con il pulsante destro del mouse sul punto rosso del punto di interruzione, scegliere **Condizione** e quindi creare espressioni con il codice Python. Per informazioni dettagliate su questa funzionalità in Visual Studio, vedere [Condizioni per i punti di interruzione](../debugger/using-breakpoints.md#breakpoint-conditions).

Quando si impostano le condizioni, è anche possibile impostare un'**azione** e creare un messaggio da registrare nella finestra di output, nonché scegliere se continuare automaticamente l'esecuzione. La registrazione di un messaggio crea un cosiddetto *punto di analisi* senza aggiungere codice di registrazione direttamente nell'applicazione:

![Creazione di un punto di analisi con un punto di interruzione](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Esecuzione del codice un'istruzione alla volta

Quando l'esecuzione del codice viene arrestata in corrispondenza di un punto di interruzione, sono disponibili varie opzioni per eseguire il codice istruzione per istruzione oppure eseguire blocchi di codice prima di una nuova interruzione. Questi comandi sono disponibili in diverse posizioni, tra cui la barra degli strumenti di debug superiore, il menu **Debug**, il menu di scelta rapida nell'editor del codice e tramite i tasti di scelta rapida, tenendo presente però che non tutti i comandi sono accessibili da tutte le posizioni:

| Funzionalità | Combinazioni di tasti | Descrizione |
| --- | --- | --- |
| **Continua** | **F5** | Esegue il codice fino a quando non viene raggiunto il punto di interruzione successivo. |
| **Esegui istruzione** | **F11** | Esegue l'istruzione successiva e si arresta. Se l'istruzione successiva è una chiamata a una funzione, il debugger si arresta in corrispondenza della prima riga della funzione chiamata. |
| **Esegui istruzione/routine** | **F10** | Esegue l'istruzione successiva, effettuando anche una chiamata a una funzione (ed eseguendone tutto il relativo codice) ed applicando l'eventuale valore restituito. Questo comando consente di ignorare facilmente le funzioni di cui non è necessario eseguire il debug. |
| **Esci da istruzione/routine** | **MAIUSC** + **F11** | Esegue il codice fino alla fine della funzione corrente, quindi passa all'istruzione di chiamata.  Questo comando è utile quando non è necessario eseguire il debug della parte restante della funzione corrente. |
| **Esegui fino al cursore** | **CTRL** + **F10** | Esegue il codice fino alla posizione del punto di inserimento nell'editor. Questo comando consente di ignorare facilmente un segmento di codice di cui non è necessario eseguire il debug. |
| **Imposta istruzione successiva** | **CTRL** + **MAIUSC** + **F10** | Imposta il punto di esecuzione corrente nel codice in corrispondenza della posizione del punto di inserimento. Questo comando consente di evitare l'esecuzione di un segmento di codice, ad esempio quando si sa già che contiene errori o produce effetti collaterali indesiderati. |
| **Mostra istruzione successiva** | **ALT** + **Num** **&#42;**| Riporta alla successiva istruzione da eseguire. Questo comando è utile per individuare all'interno del codice il punto in cui il debugger è stato arrestato. |

### <a name="inspect-and-modify-values"></a>Esaminare e modificare i valori

Quando il debugger non è in esecuzione, è possibile controllare e modificare i valori delle variabili. È anche possibile usare la finestra **Espressioni di controllo** per monitorare singole variabili oltre a espressioni personalizzate. Per informazioni di carattere generale, vedere [Controllare le variabili](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows).

Per visualizzare un valore usando i **suggerimenti dati**, è sufficiente passare il puntatore del mouse su una qualsiasi variabile nell'editor. È possibile fare clic sul valore per modificarlo:

![Suggerimenti dati nel debugger di Visual Studio](media/debugging-quick-tips.png)

La finestra **Auto** (**Debug** > **Finestre** > **Auto**) contiene variabili ed espressioni vicine all'istruzione corrente. È possibile fare doppio clic nella colonna del valore oppure selezionare e premere **F2** per modificare il valore:

![Finestra Auto nel debugger di Visual Studio](media/debugging-autos-window.png)

La finestra **Variabili locali** (**Debug** > **Finestre** > **Variabili locali**) visualizza tutte le variabili presenti nell'ambito corrente che è possibile modificare nuovamente:

![Finestra Variabili locali nel debugger di Visual Studio](media/debugging-locals-window.png)

Per altre informazioni sull'uso di **Auto** e **Variabili locali**, vedere [Controllare le variabili nelle finestre Auto e Variabili locali](../debugger/autos-and-locals-windows.md).

Le finestre **Espressioni di controllo** (**Debug** > **Finestre** > **Espressioni di controllo** > **Espressione di controllo 1-4**) consentono di immettere espressioni Python arbitrarie e di visualizzare i risultati. Le espressioni vengono valutate nuovamente per ogni passaggio:

![Finestra Espressioni di controllo nel debugger di Visual Studio](media/debugging-watch-window.png)

Per altre informazioni sull'uso di **Espressioni di controllo**, vedere [Impostare un'espressione di controllo nelle variabili usando le finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md).

Durante il controllo di un valore stringa (a questo scopo `str`, `unicode`, `bytes` e `bytearray` sono tutti considerati stringhe), a destra del valore compare l'icona di una lente di ingrandimento. Se si fa clic sull'icona, il valore stringa senza virgolette viene visualizzato in una finestra di dialogo popup con wrapping e scorrimento, funzioni utili in caso di stringhe lunghe. In più, se si fa clic sulla freccia giù sull'icona è possibile scegliere tra le visualizzazioni testo normale, HTML, XML e JSON:

![Visualizzatori di stringa nel debugger di Visual Studio](media/debugging-string-visualizers.png)

Le visualizzazioni HTML, XML e JSON sono disponibili in finestre popup separate, che supportano visualizzazioni albero ed evidenziazione della sintassi.

### <a name="exceptions"></a>Eccezioni

Se si verifica un errore nel programma durante il debug e non si dispone di un gestore di eccezioni per risolverlo, l'esecuzione del debugger si interrompe in corrispondenza del punto in cui si è verificata l'eccezione:

![Popup delle eccezioni nel debugger di Visual Studio](media/debugging-exception-popup.png)

A questo punto è possibile controllare lo stato del programma, incluso lo stack di chiamate. Se tuttavia si prova a eseguire il codice istruzione per istruzione, l'eccezione continua a essere generata fino a quando non viene gestita o il programma non viene chiuso.

Il **comando** di menu Windows eccezioni Impostazioni visualizza una finestra in cui è  >    >   possibile espandere **Eccezioni Python:**

![Finestra delle eccezioni nel debugger di Visual Studio](media/debugging-exception-settings.png)

La casella di controllo relativa alle singole eccezioni consente di controllare se l'esecuzione del debugger deve essere *sempre* interrotta quando viene generata l'eccezione. Selezionare questa casella se si vuole interrompere più spesso l'esecuzione per una particolare eccezione.

Per impostazione predefinita, la maggior parte delle eccezioni causa un'interruzione quando nel codice sorgente non viene trovato alcun gestore di eccezioni. Per modificare questo comportamento, fare clic con il pulsante destro del mouse su una qualsiasi eccezione e modificare l'opzione **Continua se non gestita nel codice utente**. Deselezionare questa casella se si vuole interrompere meno spesso l'esecuzione per un'eccezione.

Per configurare un'eccezione che non compare nell'elenco, fare clic sul pulsante **Aggiungi** per aggiungerla. Il nome deve corrispondere al nome completo dell'eccezione.

## <a name="project-debugging-options"></a>Opzioni di debug del progetto

Per impostazione predefinita, il debugger avvia il programma con l'utilità di avvio standard di Python, senza argomenti della riga di comando e altri percorsi o condizioni speciali. Le opzioni di avvio vengono modificate tramite le proprietà di debug del progetto a cui si accede facendo clic **con** il pulsante destro del mouse sul progetto in Esplora soluzioni , scegliendo **Proprietà** e selezionando la **scheda Debug** .

![Proprietà di debug del progetto nel debugger di Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opzioni di Modalità di avvio

| Opzione | Descrizione |
| --- | --- |
| **Utilità di avvio Python standard** | Usa il codice di debug scritto in Python portabile che è compatibile con CPython, IronPython e varianti quali Stackless Python. Offre un'esperienza ottimale per il debug di codice Python puro. Si tratta dell'utilità di avvio usata quando ci si collega a un processo *python.exe* in esecuzione. Questa utilità di avvio include anche il [debug in modalità mista](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) per CPython, che consente di passare in modo trasparente dal codice C/C++ al codice Python e viceversa. |
| **Utilità di avvio Web** | Esegue il browser predefinito all'avvio e consente di eseguire il debug di modelli. Per altre informazioni, vedere la sezione [Web template debugging](python-web-application-project-templates.md#debugging) (Debug di modelli Web). |
| **Utilità di avvio Web Django** | È identica a quella di avvio Web e viene visualizzata solo per garantire la compatibilità con le versioni precedenti. |
| **Utilità di avvio IronPython (.NET)** | Usa il debugger di .NET, che funziona solo con IronPython ma consente di passare a qualsiasi progetto in linguaggio .NET, tra cui C# e VB. Questa utilità di avvio viene usata se ci si connette a un processo .NET in esecuzione che ospita IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opzioni di esecuzione (percorsi di ricerca, argomenti di avvio e variabili di ambiente)

| Opzione | Descrizione |
| --- | --- |
| **Percorsi di ricerca** | Questi valori corrispondono a quanto visualizzato  nel nodo Percorsi di ricerca del progetto in **Esplora soluzioni**. È possibile modificare qui questo valore, ma è più facile usare **Esplora soluzioni** che consente di sfogliare le cartelle e converte automaticamente i percorsi nel formato relativo. |
| **Argomenti script** | Questi argomenti vengono aggiunti al comando usato per avviare lo script e vengono visualizzati dopo il nome del file di script. Il primo elemento definito qui risulta disponibile per lo script come `sys.argv[1]`, il secondo come `sys.argv[2]`e così via. |
| **Argomenti dell'interprete** | Questi argomenti vengono aggiunti alla riga di comando dell'utilità di avvio prima del nome dello script. Qui gli argomenti comuni sono `-W ...` per controllare gli avvisi, `-O` per ottimizzare leggermente il programma e `-u` per usare I/O non memorizzato nel buffer. È probabile che gli utenti di IronPython usino questo campo per passare le opzioni di `-X`, ad esempio `-X:Frames` o `-X:MTA`. |
| **Percorso dell'interprete** | Esegue l'override del percorso associato all'ambiente corrente. Il valore può essere utile per avviare lo script con un interprete non standard. |
| **Variabili di ambiente** | In questa casella di testo a più righe aggiungere voci nel formato \<NAME> = \<VALUE> . Poiché questa impostazione viene applicata per ultima, oltre a qualsiasi variabile di ambiente globale esistente e dopo viene impostata in base all'impostazione Percorsi di ricerca, può essere usata per eseguire manualmente l'override di qualsiasi altra `PYTHONPATH` variabile.  |

## <a name="immediate-and-interactive-windows"></a>Finestra interattiva e finestra di controllo immediato

Durante una sessione di debug è possibile usare due finestre interattive: la finestra **Controllo immediato** standard di Visual Studio e la finestra **Debug interattivo Python**.

La finestra **Controllo immediato** (**Debug** > **Finestre** > **Controllo immediato**) viene usata per una rapida valutazione delle espressioni di Python e per il controllo o l'assegnazione di variabili all'interno del programma in esecuzione. Per informazioni dettagliate, vedere l'articolo generale [Controllo immediato (finestra)](../ide/reference/immediate-window.md).

La finestra **Debug interattivo Python** (**Debug** > **Finestre** > **Debug interattivo Python**) è più completa perché consente di accedere a tutte le funzionalità dell'esperienza [REPL interattivo](python-interactive-repl-in-visual-studio.md) durante il debug, inclusa la scrittura e l'esecuzione di codice. Si connette automaticamente a qualsiasi processo avviato nel debugger usando l'utilità di avvio Python Standard (inclusi i processi collegati tramite **Debug**  >  **Connetti a processo**). Non è però disponibile quando si usa il debug C/C++ in modalità mista.

![Finestra Debug interattivo Python](media/debugging-interactive.png)

La finestra **Debug interattivo** supporta speciali metacomandi in aggiunta ai [comandi REPL standard](python-interactive-repl-in-visual-studio.md#meta-commands):

| Comando | Argomenti | Descrizione |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Avvia l'esecuzione del programma a partire dall'istruzione corrente. |
| `$down`, `$d` | Sposta il frame corrente di un livello verso il basso nell'analisi dello stack. |
| `$frame` | | Visualizza l'ID frame corrente.
| `$frame` | ID frame | Consente di passare dal frame corrente a quello con l'ID frame specificato.
| `$load` | Carica i comandi dal file e viene eseguito fino al completamento. |
| `$proc` |  | Visualizza l'ID processo corrente. |
| `$proc` | ID processo | Consente di passare dal processo corrente a quello con l'ID processo specificato. |
| `$procs` | | Visualizza l'elenco di processi di cui è in corso il debug. |
| `$stepin`, `$step`, `$s` | Esegue, se possibile, la chiamata di funzione successiva. |
| `$stepout`, `$return`, `$r` | Esce dalla funzione corrente. |
| `$stepover`, `$until`, `$unt` | Esegue la chiamata di funzione successiva. |
| `$thread` | | Visualizza l'ID thread corrente. |
| `$thread` | ID thread | Consente di passare dal thread corrente a quello con l'ID thread specificato. |
| `$threads` | | Visualizza l'elenco dei thread di cui è in corso il debug. |
| `$up`, `$u` | | Sposta il frame corrente di un livello verso l'alto nell'analisi dello stack. |
| `$where`, `$w`, `$bt` | Visualizza l'elenco dei frame per il thread corrente. |

Si noti che le finestre standard del debugger, ad esempio **Processi**, **Thread** e **Stack di chiamate**, non vengono sincronizzate con la finestra **Debug interattivo**. La modifica del processo, del thread o del frame attivo nella finestra **Debug interattivo** non influisce sulle altre finestre del debugger. Analogamente, la modifica del processo, del thread o del frame attivo nelle finestre del debugger non influisce sulla finestra **Debug interattivo**.

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Usare il debugger legacy

La versione 15.8 e successive di Visual Studio 2017 usano un debugger basato sulla versione ptvsd 4.1 +. Visual Studio 2019 versione 16.5 e successive usa un debugger basato su debugpy. Queste versioni del debugger sono compatibili con Python 2.7 e Python 3.5+. Se si usa Python 2.6, dalla versione 3.1 a 3.4 o IronPython, Visual Studio mostra l'errore **Il debugger non supporta questo ambiente Python**:

![Errore Il debugger non supporta questo ambiente Python quando si usa il debugger](media/debugging-experimental-incompatible-error.png)

In questi casi è necessario usare il debugger precedente, ovvero quello predefinito in Visual Studio 2017 versioni 15.7 e precedenti. Selezionare il **comando di** menu  >  **Opzioni** strumenti, passare a **Debug Python** e  >  selezionare **l'opzione Usa debugger** legacy.

Se nell'ambiente corrente è stata installata una versione precedente di ptvsd, ad esempio una versione 4.0.x o una versione 3.x precedente necessaria per il debug remoto, Visual Studio potrebbe mostrare un errore o un avviso.

L'errore **Non è stato possibile caricare il pacchetto del debugger** viene visualizzato dopo aver installato ptvsd 3.x:

![Errore Non è stato possibile caricare il pacchetto del debugger quando si usa il debugger](media/debugging-experimental-version-error.png)

In questo caso selezionare **Use the legacy debugger** (Usa debugger legacy) per impostare l'opzione **Use the legacy debugger** (Usa debugger legacy) e riavviare il debugger.

L'avviso **Il pacchetto del debugger è obsoleto** viene visualizzato dopo aver installato una versione 4.x precedente di ptvsd:

![Avviso Il pacchetto del debugger è obsoleto quando si usa il debugger](media/debugging-experimental-version-warning.png)

> [!Important]
> Anche se è possibile scegliere di ignorare l'avviso per alcune versioni di ptvsd, Visual Studio potrebbe non funzionare correttamente.

Per gestire l'installazione di ptvsd:

1. Passare alla scheda **Pacchetti** nella finestra **Ambienti Python**.

1. Immettere "ptvsd" nella casella di ricerca ed esaminare la versione di ptvsd installata:

    ![Controllo della versione di ptvsd nella finestra Ambienti Python](media/debugging-experimental-check-ptvsd.png)

1. Se la versione è precedente a 4.1.1a9, ovvero la versione in bundle con Visual Studio, selezionare la **X** a destra del pacchetto per disinstallare la versione precedente. Visual Studio usa quindi la versione in bundle. È anche possibile eseguire la disinstallazione da PowerShell usando `pip uninstall ptvsd`.

1. In alternativa, è possibile aggiornare il pacchetto ptvsd alla versione più recente seguendo le istruzioni nella sezione [Risoluzione dei problemi](#troubleshooting).

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="for-visual-studio-2019-version-164-and-earlier-upgrade-ptvsd"></a>Per Visual Studio 2019 (versione 16.4 e precedenti) aggiornare ptvsd
Se si verificano problemi con il debugger, aggiornare prima di tutto la versione del debugger come indicato di seguito:

1. Passare alla scheda **Pacchetti** nella finestra **Ambienti Python**.

1. Immettere `ptvsd --upgrade` nella casella di ricerca, quindi selezionare **Esegue il comando: pip install ptvsd --upgrade**. È anche possibile usare lo stesso comando di PowerShell.

    ![Invio del comando di aggiornamento di ptvsd nella finestra Ambienti Python](media/debugging-experimental-upgrade-ptvsd.png)

   Se i problemi persistono, segnalare il problema nel [repository GitHub di PTVS](https://github.com/Microsoft/ptvs/issues).

   > [!NOTE]
   > Per Visual Studio 2019 versione 16.5 e successive, debugpy fa parte del carico di lavoro python di Visual Studio e viene aggiornato insieme Visual Studio.

### <a name="enable-debugger-logging"></a>Abilitare la registrazione del debugger

Durante l'analisi di un problema del debugger, Microsoft potrebbe chiedere di abilitare e raccogliere i log del debugger utili per la diagnosi.

La procedura seguente abilita il debug nella sessione corrente di Visual Studio:

1. Aprire una finestra di comando in Visual Studio il **comando di** menu  >  **Visualizza Windows** di  >  **comando.**

1. Immettere il comando seguente:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Avviare il debug ed eseguire tutti i passaggi necessari per riprodurre il problema. Mentre si eseguono queste operazioni, i log del debug vengono visualizzati nella finestra **Output** in **Log dell'host dell'adattatore di debug**. È quindi possibile copiare i log da tale finestra e incollarli in una segnalazione in GitHub, un messaggio di posta elettronica e così via.

    ![Output di registrazione del debugger nella finestra Output](media/debugger-logging-output.png)

1. Se Visual Studio smette di rispondere o non si è in grado di accedere alla finestra **Output,** riavviare Visual Studio, aprire una finestra di comando e immettere il comando seguente:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Avviare il debug e riprodurre di nuovo il problema. I log del debugger sono disponibili in `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Vedi anche

Per informazioni dettagliate sul debugger di Visual Studio, vedere [Debug in Visual Studio](../debugger/debugger-feature-tour.md).
