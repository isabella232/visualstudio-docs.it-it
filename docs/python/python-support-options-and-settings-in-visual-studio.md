---
title: Opzioni e impostazioni per Python
description: Informazioni di riferimento per le varie impostazioni di Visual Studio correlate al codice e ai progetti Python.
ms.date: 03/13/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 1449e4acc3c7b2c9ef438d85fe9640406b9b3867
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636956"
---
# <a name="options-for-python-in-visual-studio"></a>Opzioni di Python in Visual Studio

Per visualizzare le opzioni di Python, usare **il** comando di menu Strumenti Opzioni, assicurarsi che l'opzione Mostra tutte le impostazioni sia selezionata e quindi passare a  >   **Python:** 

::: moniker range="vs-2017"
![Finestra di dialogo Opzioni di Python, scheda Generale](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Finestra di dialogo Opzioni di Python, scheda Generale](media/options-general-2019.png)
::: moniker-end

Sono disponibili anche altre opzioni specifiche di Python nella scheda Avanzate python **dell'editor** di testo e nella scheda Tipi di carattere e colori  >    >   dell'ambiente all'interno del gruppo Editor  >   **di** testo.

> [!Note]
> Il gruppo **Sperimentale** contiene le opzioni per le funzionalità che sono ancora in fase di sviluppo e che non sono qui documentate. Sono spesso discusse in post nel [blog Python engineering at Microsoft](https://devblogs.microsoft.com/python/) (Progettazione Python in Microsoft).

## <a name="general-options"></a>Opzioni generali

(**Strumenti**  >  **Opzioni**  >  **Scheda Python.**

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Mostra la finestra di output durante la creazione degli ambienti virtuali**| On | Deselezionare per impedire che venga visualizzata la **finestra di output**. |
| **Mostra la finestra di output durante l'installazione o la rimozione di pacchetti** | On | Deselezionare per impedire che venga visualizzata la **finestra di output**. |
| **Mostra la barra di notifica per la creazione di ambienti** | On | *Solo Visual Studio 2019.* Quando questa opzione è impostata e l'utente apre un progetto che contiene un file *requirements.txt* oppure *environment.yml*, Visual Studio visualizza una barra informazioni con i suggerimenti per creare rispettivamente un ambiente virtuale o un ambiente conda, invece di usare l'ambiente globale predefinito. |
| **Mostra la barra di notifica per l'installazione di pacchetti** | On | *Solo Visual Studio 2019.* Quando questa opzione è impostata e l'utente apre un progetto che contiene un file *requirements.txt* (e non usa l'ambiente globale predefinito) Visual Studio confronta tali requisiti con i pacchetti installati nell'ambiente corrente. Se mancano pacchetti, Visual Studio visualizza un prompt per installare tali dipendenze. |
| **Esegui sempre strumenti di gestione pacchetti come amministratore** | Off | Eleva sempre i privilegi per `pip install` e operazioni di gestione pacchetti simili per tutti gli ambienti. Durante l'installazione dei pacchetti, Visual Studio richiede i privilegi di amministratore se l'ambiente si trova in un'area protetta del file system, come *c:\Programmi*. In questo prompt è possibile scegliere di elevare sempre i privilegi del comando di installazione solo per tale specifico ambiente. Vedere la [scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab). |
| **Genera automaticamente il database di completamento al primo utilizzo** | On | *Si applica a Visual Studio 2017 versione 15.5 e versioni precedenti quando si usa un database di IntelliSense.* Assegna la priorità del completamento del database per una libreria, quando si scrive un codice che ne fa uso. Per altre informazioni, vedere [Scheda Intellisense](python-environments-window-tab-reference.md?view=vs-2017&preserve-view=true#intellisense-tab). |
| **Ignora variabili PYTHONPATH a livello di sistema** | On | PYTHONPATH viene ignorato per impostazione predefinita perché Visual Studio offre un mezzo più diretto per specificare i percorsi di ricerca negli ambienti e nei progetti. Per altri dettagli, vedere [Percorsi di ricerca](search-paths.md). |
| **Aggiorna percorsi di ricerca quando vengono aggiunti file collegati** | On | Se impostata, l'aggiunta di [](search-paths.md) un [file](managing-python-projects-in-visual-studio.md#linked-files) collegato a un progetto aggiorna i percorsi di ricerca in modo che IntelliSense possa includere il contenuto della cartella del file collegato nel database di completamento. Deselezionare questa opzione per escludere tale contenuto dal database di completamento. |
| **Avvisa quando non è possibile trovare il modulo importato** | On | Deselezionare questa opzione per non visualizzare gli avvisi quando si è certi che un modulo importato non è attualmente disponibile, ma non influisce comunque sul funzionamento del codice. |
| **Segnala rientro incoerente come** | **Avvisi** | Poiché l'interprete di Python dipende fortemente da un rientro corretto per determinare l'ambito, Visual Studio per impostazione predefinita genera dei messaggi di avviso quando rileva rientri incoerenti che potrebbero indicare errori di codifica. Per maggiore precisione, impostare su **Errori**, opzione che provoca la chiusura del programma in casi di questo tipo. Per disabilitare completamente questo comportamento, selezionare **No**. |
| **Controlla disponibilità di sondaggi/novità** | **Una volta alla settimana** | *Visual Studio 2017 e versioni precedenti.* Imposta la frequenza con cui si consente a Visual Studio di aprire una finestra contenente una pagina web con sondaggi e notizie relativi a Python, qualora disponibili. Le opzioni sono **Mai**, **Una volta al giorno**, **Una volta alla settimana** e **Una volta al mese**. |
| Pulsante **Ripristina tutte le finestre di dialogo nascoste in modo permanente** | n/d | Diverse finestre di dialogo presentano opzioni quali **Non visualizzare più questo messaggio**. Usare questo pulsante per cancellare tali opzioni e visualizzare nuovamente le finestre di dialogo. |

::: moniker range="vs-2017"
![Finestra di dialogo Opzioni di Python, scheda Generale](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Finestra di dialogo Opzioni di Python, scheda Generale](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Opzioni Conda

(**Strumenti** > **Opzioni** > **Python** > **Scheda Conda.**

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Percorso dell'eseguibile di Conda** | (vuoto) | Specifica un percorso esatto per l'eseguibile *conda.exe* anziché basarsi sull'installazione di Miniconda predefinita inclusa nel carico di lavoro di Python. Se si specifica un altro percorso in questa posizione, avrà la precedenza sull'installazione predefinita e su eventuali altri eseguibili conda.exe specificati nel Registro di sistema. Può essere utile modificare questa impostazione se si installa manualmente una versione più recente di Anaconda o Miniconda oppure si vuole usare una distribuzione a 32-bit piuttosto che la distribuzione predefinita a 64 bit. |

![Screenshot della finestra di Strumenti di Visual Studio opzioni con Conda selezionato nelle opzioni Python e il campo Percorso eseguibile Conda visualizzato nel riquadro di destra.](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Opzioni di debug

(**Strumenti**  >  **Opzioni**  >  **Python**  >  **Scheda** Debug.

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Chiedi conferma prima dell'esecuzione quando sono presenti errori** | On | Se impostato, viene chiesto di confermare che si desidera eseguire il codice contenente errori. Deselezionare questa opzione per disabilitare l'avviso. |
| **Attendi input quando il processo viene chiuso in modo anomalo**<br/><br/>**Attendi input quando il processo viene chiuso normalmente** | Attivato (per entrambi) | Un programma Python avviato da Visual Studio viene eseguito nella propria finestra della console. Per impostazione predefinita, la finestra attende che venga premuto un tasto prima di chiudere il programma, indipendentemente dalla modalità con cui viene chiuso il programma. Per rimuovere il prompt e chiudere la finestra automaticamente, deselezionare una o entrambe le opzioni. |
| **Output del programma tee nella finestra di output del debug** | On | Visualizza l'output del programma in una finestra della console separata e nella **finestra di output** di Visual Studio. Deselezionare questa opzione per visualizzare l'output solo nella finestra della console separata. |
| **Interrompi in caso di eccezione SystemExit con codice di uscita zero** | Off | Se l'opzione è selezionata, il debugger viene arrestato su questa eccezione. Se è deselezionata, il debugger viene chiuso senza interruzioni. |
| **Abilita il debug della libreria standard Python** | Off | Consente di eseguire il codice sorgente della libreria standard durante il debug, ma aumenta il tempo necessario all'avvio del debugger.|
| **Mostra il valore restituito della funzione** | On | *Solo Visual Studio 2019.* Consente di visualizzare i valori restituiti della funzione nella finestra **Variabili locali** e quindi di eseguire una chiamata di funzione nel debugger (F10) |
| **Usa debugger legacy** | Off | *Solo Visual Studio 2019.* Indica a Visual Studio di usare il debugger legacy per impostazione predefinita. Per altre informazioni, vedere [Debug - Usare il debugger legacy](debugging-python-in-visual-studio.md#use-the-legacy-debugger). |

::: moniker range="vs-2017"
![Finestra di dialogo Opzioni di Python, scheda Debug](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Finestra di dialogo Opzioni di Python, scheda Debug](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Opzioni di diagnostica

(**Strumenti**  >  **Opzioni**  >  **Python**  >  **Scheda** Diagnostica.

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Includi log di analisi** | On | Include log dettagliati relativi all'analisi di ambienti Python installati durante il salvataggio della diagnostica in un file o la copia negli Appunti tramite i pulsanti. Questa opzione può aumentare notevolmente le dimensioni del file generato, ma spesso è necessaria per diagnosticare problemi di IntelliSense. |
| **Pulsante Salva diagnostica su** file | n/d | Richiede un nome di file, quindi salva il log in un file di testo. |
| **Pulsante Copia diagnostica negli** Appunti | n/d | Inserisce l'intero contenuto del log negli Appunti. Questa operazione potrebbe richiedere tempo a seconda delle dimensioni del log. |

![Finestra di dialogo Opzioni di Python, scheda Diagnostica](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Opzioni della finestra interattiva

(**Strumenti**  >  **Opzioni**  >  **Python**  >  **Scheda Windows** interattiva.

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Script** | n/d | Specifica una cartella generale per gli script di avvio valida per le finestre **interattive** per tutti gli ambienti. Vedere [Script di avvio.](python-environments-window-tab-reference.md#startup-scripts) Si noti, tuttavia, che questa funzionalità non è attualmente supportata. |
| **Spostarsi nella cronologia con le frecce su/giù** | On | Usare i tasti freccia per spostarsi nella cronologia nella finestra **interattiva**. Deselezionare questa impostazione per usare i tasti freccia per spostarsi invece all'interno dell'output della finestra **interattiva**. |
| **Modalità di completamento** | **Valuta solo le espressioni senza chiamate di funzione** | Il processo di determinazione dei membri disponibili su un'espressione nella finestra **interattiva** può richiedere la valutazione dell'espressione incompleta corrente, con la conseguente chiamata ripetuta di effetti collaterali o funzioni. L'impostazione predefinita, **Valuta solo le espressioni senza chiamate di funzione** esclude le espressioni che sembrano chiamare una funzione, ma valuta altre espressioni. Ad esempio, valuta `a.b` ma non `a().b`.  **Non valutare mai le espressioni** evita tutti gli effetti collaterali e usa solo il motore di IntelliSense normale per i suggerimenti. **Valuta tutte le espressioni** valuta l'espressione completa per ottenere suggerimenti, indipendentemente dagli effetti collaterali. |
| **Nascondi suggerimenti analisi statica** | Off | Se è impostata questa opzione, vengono visualizzati solo i suggerimenti ottenuti dalla valutazione dell'espressione. Se è associata alla **modalità di completamento****Non valutare mai le espressioni**, non viene visualizzato alcun completamento utile nella finestra **interattiva**. |

![Finestra di dialogo delle opzioni di Python, scheda Finestre interattive](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Opzioni Server di linguaggio

(**Strumenti** > **Opzioni** > **Python** > **Scheda Del server di** linguaggio.

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Disabilita completamenti da Typeshed** | Off | IntelliSense per Visual Studio usa in genere una versione in bundle di Typeshed (un set di file con estensione *pyi*) per trovare suggerimenti relativi al tipo per la libreria standard e le librerie di terze parti per Python 2 e Python 3. Impostando questa opzione viene disabilitato il comportamento di Typeshed in bundle. |
| **Percorso personalizzato di Typeshed** | (vuoto) | Se si imposta questa opzione, Visual Studio usa i file Typeshed in questo percorso invece della versione in bundle. L'opzione viene ignorata se si imposta **Disabilita completamenti da Typeshed**. |

![Screenshot della finestra Strumenti di Visual Studio opzioni avanzate con l'opzione Server del linguaggio selezionata nelle opzioni Python e le opzioni del server di linguaggio visualizzate nel riquadro destro.](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Opzioni avanzate dell'editor di Python

(**Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **Python**  >  **Scheda** Avanzate.

### <a name="completion-results"></a>Risultati del completamento

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Il completamento dei membri visualizza l'intersezione dei membri** | Off | Se l'opzione è impostata, vengono visualizzati solo i completamenti supportati da tutti i tipi possibili. |
| **Filtra elenco in base alla stringa di ricerca** | On | Applica il filtro dei suggerimenti di completamento durante la digitazione (l'opzione è selezionata per impostazione predefinita). |
| **Mostra automaticamente i completamenti per tutti gli identificatori** | On | Deselezionare questa opzione per disabilitare i completamenti sia nell'editor che nelle finestre **interattive**. |

### <a name="selection-in-completion-list"></a>Selezione negli elenchi di completamento

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Commit alla digitazione dei caratteri seguenti** | **{}\[\]().,:;+-*/%&&#124;^~=<> #@\\** | Questi caratteri seguono in genere un identificatore che può essere selezionato da un elenco di completamento, pertanto è consigliabile eseguire il commit del completamento semplicemente digitando un carattere. È possibile rimuovere o aggiungere caratteri specifici all'elenco in base alle esigenze.  |
| **Immetti completamento corrente dei commit** | On | Se impostato,  il tasto INVIO sceglie e applica il completamento attualmente selezionato come con i caratteri precedenti (ma naturalmente non è presente un carattere per **INVIO,** quindi non è stato possibile accedere direttamente all'elenco). |
| **Aggiungi nuova riga quando si preme Invio alla fine della parola digitata** | Off | Per impostazione predefinita, se si digita l'intera parola visualizzata nel popup di completamento e si preme **INVIO,** si esegue il commit del completamento. Impostando questa opzione, si esegue effettivamente il commit dei completamenti al termine della digitazione dell'identificatore, in modo che **invio** inserisca una nuova riga. |

### <a name="miscellaneous-options"></a>Opzioni varie

| Opzione | Predefinito | Descrizione |
| --- | --- | --- |
| **Attiva modalità struttura all'apertura dei file** | On | Attiva automaticamente la funzionalità di struttura nell'editor di Visual Studio all'apertura di un file di codice Python. |
| **Paste removed REPL prompts (Incolla prompt REPL rimossi)** | On | Rimuove **>>>** e ... **dal** testo incollato, consentendo un facile trasferimento del codice dalla **finestra** interattiva all'editor. Deselezionare questa opzione se è necessario conservare tali caratteri provenienti da altre origini. |
| **Nomi dei colori in base ai tipi** | On | Abilita la colorazione della sintassi nel codice Python. |

![Finestra di dialogo delle opzioni dell'editor di Python, scheda avanzate](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Opzioni Tipi di carattere e colori

(**Ambiente**  >  **Scheda Tipi di carattere e** colori nel gruppo Editor **di** testo.

I nomi delle opzioni di Python sono preceduti tutti dal prefisso **Python** e sono autoesplicativi. Il tipo di carattere predefinito per tutti Visual Studio colori è 10 pt Consolas normale (non in grassetto). I colori predefiniti variano a seconda del tema. In genere, si modifica un tipo di carattere o un colore se la leggibilità del testo non è adeguata con le impostazioni predefinite.

![Opzioni per tipo di carattere e colori di Python](media/options-fonts-and-colors.png)
