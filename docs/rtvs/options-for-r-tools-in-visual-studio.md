---
title: Opzioni di R Tools
description: Informazioni di riferimento per le opzioni in Visual Studio per il linguaggio R e funzionalità associate.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: fc46d7ed1e369d31a9d0675f0595073f51f28d17
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2021
ms.locfileid: "114679793"
---
# <a name="r-tools-for-visual-studio-options"></a>Opzioni di R Tools per Visual Studio

Impostazioni'accesso tramite il menu R Tools Options (Opzioni strumenti **R)** o Tools Options (Opzioni strumenti) e  >     >   scorrendo fino a **R Tools**:

  ![Finestra di dialogo Opzioni per R Tools](media/options-dialog.png)

Le opzioni e le impostazioni specifiche di R sono accessibili tramite i metodi indicati di seguito. È necessario selezionare la casella **Mostra tutte le impostazioni** nella parte inferiore della finestra di dialogo **Opzioni** per visualizzare tutte queste sezioni.

- Opzioni di formattazione del codice (vedere [Opzioni editor](editing-r-code-in-visual-studio.md#editor-options): menu **Strumenti** > **Opzioni**, quindi selezionare **Editor di testo** > **R** > **Formattazione**
- Opzioni linter (vedere [Lint](linting-r-code.md)): menu **Strumenti** > **Opzioni**, quindi selezionare **Editor di testo** > **R** > **Lint**
- Opzioni dell'editor avanzate ([descritte in questo articolo](#text-editor--r--advanced-options)): menu **Strumenti** > **Opzioni**, quindi selezionare **Editor di testo** > **R** > **Avanzate**
- Opzioni di comportamento ([descritte in questo articolo](#r-tools--advanced-options)): menu **R Tools** > **Opzioni** oppure **Strumenti** > **Opzioni** e quindi scorrere fino a **R Tools**.

Il **comando R Tools** Data Science  >  **Impostazioni** influisce anche su diverse impostazioni in Visual Studio generale. Questo comando viene descritto nella sezione successiva.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>R Tools > Impostazioni di Data Science

La voce di menu **R Tools > Impostazioni di Data Science** configura l'IDE di Visual Studio con un layout ottimizzato per le esigenze dei data scientist. In particolare, questa opzione consente di aprire le finestre [R interattivo](interactive-repl-for-r-in-visual-studio.md), [Esplora variabili](variable-explorer.md) e [Aree di lavoro](r-workspaces-in-visual-studio.md):

![Layout delle finestre per data scientist in Visual Studio](media/installation-data-scientist-layout-result.png)

Per ripristinare le altre impostazioni Visual Studio in un secondo momento, usare prima di tutto il comando Importa ed esporta Impostazioni strumenti, selezionare Esporta impostazioni di ambiente selezionate e specificare un nome  >   file.  Per ripristinare tali impostazioni, usare lo stesso comando e selezionare **Importa le impostazioni di ambiente selezionate**. È possibile usare gli stessi comandi anche se si modifica il layout per i data scientist e si vuole tornarvi in un secondo momento, anziché usare direttamente il comando **Impostazioni di Data Science**.

## <a name="text-editor--r--advanced-options"></a>Editor di testo > R > Opzioni avanzate

Queste opzioni controllano il comportamento di formattazione, IntelliSense, struttura, rientri e controllo della sintassi per R.

![Finestra di dialogo delle opzioni avanzate per l'editor di testo R](media/options-dialog-advanced-text-editor.png)

Ogni opzione può essere impostata su On o Off per controllare il comportamento in questione. Per informazioni dettagliate sugli effetti di ogni opzione, vedere il riquadro della Guida nella parte inferiore della finestra di dialogo. Si noti che è possibile trascinare il lato superiore del riquadro della Guida per ingrandirlo.

![Riquadro della Guida ingrandito nella finestra di dialogo delle opzioni avanzate dell'editor di testo R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>R Tools > Opzioni avanzate

Il **comando di** menu Opzioni di R Tools apre la finestra  >   **di** dialogo Opzioni per le opzioni R:

  ![Finestra di dialogo Opzioni per R Tools](media/options-dialog.png)

Le sezioni seguenti descrivono le diverse opzioni disponibili in questa pagina.

### <a name="debugging"></a>Debug

Queste opzioni controllano la gestione dei valori in [Esplora variabili](variable-explorer.md) e all'interno di finestre del debugger quali Espressioni di controllo e Variabili locali. Vedere [Debug di codice R](debugging-r-in-visual-studio.md).

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Valuta associazioni attive | `True` | Se `True`, è sempre possibile visualizzare il valore più aggiornato durante il controllo di variabili e proprietà. Il rischio è che la valutazione delle espressioni possa causare effetti collaterali, a seconda della modalità di implementazione delle espressioni stesse. |
| Mostra variabili che includono un punto come prefisso | `False` | Specifica se devono essere visualizzate le variabili con prefisso `.`. |

### <a name="grid-view"></a>Visualizzazione griglia

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Valutazione dinamica | `False` | Per impostazione predefinita, la funzione `View(<expression>)` crea uno snapshot dei dati come frame di dati e ciò può comportare un consumo notevole della memoria con set di dati di grandi dimensioni. Con l'impostazione di questa opzione su `True`, l'espressione viene valutata in concomitanza con l'aggiornamento della griglia per recuperare solo i dati visualizzati. Tuttavia, se cambia l'espressione cambiano anche i dati e ciò potrebbe non essere appropriato per espressioni dplyr pipe. |

### <a name="help"></a>Help

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Web browser F1 | `Internal` | Controlla la modalità di visualizzazione della Guida durante la ricerca di un termine usando **CTRL** + **F1.** Se l'opzione è impostata su `Internal`, il rendering della Guida viene eseguito all'interno di una finestra degli strumenti in Visual Studio. Se l'opzione è impostata su `External`, la Guida viene visualizzata nel Web browser predefinito. |
| Stringa di ricerca sul Web F1 | `R site:stackoverflow.com` | Controlla il modo in cui i termini di ricerca vengono passati al motore di ricerca quando si preme **CTRL** + **F1** su un termine nell'editor. Per impostazione predefinita la stringa è `R site:stackoverflow.com`, che aggiunge `R` al termine di ricerca. `site:stackoverflow.com` è una direttiva che indica al motore di ricerca di definire come ambito della ricerca le pagine all'interno del dominio `stackoverflow.com`. |
| Browser della Guida di R | `Automatic` | Controlla la modalità di visualizzazione della Guida quando si sta effettuando una ricerca all'interno della documentazione di R tramite **F1**, **?** o **??**. Se l'opzione è impostata su `Automatic`, il rendering della Guida viene eseguito nella finestra appropriata. Ad esempio, la Guida di HTML viene visualizzata all'interno di una finestra degli strumenti di Visual Studio, mentre i PDF vengono visualizzati nel programma per PDF predefinito. Se l'opzione è impostata su `External`, il rendering della Guida viene effettuato nel Web browser predefinito. |

### <a name="history"></a>Cronologia

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Salva sempre cronologia | `True` | Controlla se RTVS deve scrivere la cronologia dei comandi in un file con estensione *RHistory* nella directory di lavoro ogni volta che il progetto viene chiuso. Il salvataggio della cronologia avviene anche se non si salva il progetto prima di uscire. |
| Ripristina filtro di ricerca | `True` | Determina se la finestra Cronologia può filtrare la cronologia dei comandi per visualizzare solo i comandi con sottostringhe corrispondenti al termine di filtro nella finestra di dialogo Cronologia di R. Questa impostazione determina se il filtro di ricerca della cronologia deve essere reimpostato ogni volta che si esegue un nuovo comando o si passa a un nuovo progetto, attivando il caricamento di un file con estensione *RHistory* diverso. L'impostazione predefinita, `True`, riduce al minimo i casi in cui si esegue un comando con un set di filtri e questo non compare nella cronologia. |
| Usa selezione multilinea | `True` | Specifica se nella cronologia è possibile selezionare un'istruzione multilinea con un solo clic. Consente anche di spostarsi con le frecce su/giù nella finestra interattiva da un'istruzione all'altra anziché da una riga all'altra. |

### <a name="html"></a>HTML

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Browser di pagine HTML | `External` | Determina dove eseguire il rendering di contenuto quale un tracciato `ggvis` o un'applicazione `shiny`. `Internal` visualizza l'output HTML all'interno di una finestra degli strumenti in Visual Studio. `External` visualizza l'output HTML nel browser predefinito. |

### <a name="logging"></a>Registrazione

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Eventi log | `Normal` | Controlla il livello di dettaglio della registrazione usata per la diagnostica di RTVS. L'impostazione predefinita, `Normal`, crea un file di log nella directory `TEMP`. Se l'opzione è impostata su `Traffic`, RTVS registra tutti i comandi e tutte le risposte della sessione corrente. Questi file di log non escono mai dal computer ma potrebbero risultare utili per la diagnosi di problemi in RTVS. |

### <a name="markdown"></a>Markdown

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Browser di anteprima Markdown | `External` | Determina dove visualizzare l'output HTML R Markdown. `Internal` visualizza il documento HTML R Markdown all'interno di una finestra degli strumenti in Visual Studio. `External` visualizza il documento HTML R Markdown tramite il browser predefinito. |

### <a name="r-engine"></a>Motore R

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Tabella codici | `(OS Default)` | Imposta la tabella codici (impostazioni locali) per R. Per impostazione predefinita vengono usate le impostazioni locali sottostanti del sistema operativo. |
| Mirror CRAN | `(Use .Rprofile)` | Imposta il mirror CRAN predefinito per l'installazione di pacchetti. L'impostazione predefinita, `Use .Rprofile`, rispetta le impostazioni mirror CRAN del file con estensione *RProfile*. |

### <a name="workspace"></a>Area di lavoro

| Opzione | Valore predefinito | Descrizione |
| --- | --- | --- |
| Carica area di lavoro all'apertura di un progetto | `No` | L'impostazione `Yes` abilita il caricamento dei dati della sessione dal file con estensione *RData* nell'ambiente globale all'apertura del progetto. |
| Richiedi salvataggio area di lavoro al ripristino | `Yes` | L'impostazione `No` disabilita la richiesta di salvataggio dell'area di lavoro quando si fa clic sul pulsante Reimposta nella finestra interattiva. |
| Salva area di lavoro alla chiusura di un progetto | `No` | L'impostazione `Yes` abilita il salvataggio dell'ambiente globale nel file con estensione *RData* alla chiusura del progetto. |
| Mostra finestra di conferma prima di passare da un'area di lavoro all'altra | `Yes` | L'impostazione `No` disabilita la richiesta di conferma all'utente prima del passaggio da un'area di lavoro all'altra. Vedere [Passare da un'area di lavoro all'altra](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Mostra indicatore del carico del computer | `False` | Controlla la visibilità dell'indicatore di carico di CPU/memoria/rete nella barra di stato. Dato che questo indicatore genera traffico di rete, può essere utile mantenerlo impostato su `False` negli scenari remoti a consumo. La modifica di questa opzione rende necessario il riavvio di Visual Studio. |
