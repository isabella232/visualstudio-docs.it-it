---
title: Modificare il codice R
description: Visual Studio offre un'esperienza di modifica su misura per R, pur mantenendo tutte le funzionalità e la possibilità di usare le estensioni.
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 27db2b3b5edfe5fbaed9899927f7e9e866bd7d7a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628271"
---
# <a name="edit-r-code-in-visual-studio"></a>Modificare il codice R in Visual Studio

R Tools per Visual Studio (RTVS) consente di adattare l'esperienza di modifica di Visual Studio in modo specifico per R, mantenendo tutte le funzionalità e la possibilità di usare le estensioni. Se si preferiscono i tasti di scelta rapida VIM, è ad esempio possibile installare l'[estensione VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) gratuita da Visual Studio Marketplace.

Oltre alle funzionalità in questo articolo, vedere anche [IntelliSense](r-intellisense.md), [lint](linting-r-code.md), [frammenti di codice](code-snippets-for-r.md) e [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Evidenziazione della sintassi

Oltre ad applicare un colore alle diverse parti del codice, ad esempio stringhe, commenti e parole chiave, RTVS evidenzia e abilita anche i collegamenti nei commenti:

![Colorazione della sintassi per il codice R](media/editing-syntax-colors.png)

Per personalizzare i tipi di carattere e alcuni colori di evidenziazione, selezionare il comando Opzioni strumenti, passare a Tipi di carattere e colori dell'ambiente e quindi modificare le impostazioni per gli elementi correlati a R nella  >     >   **casella Elementi** visualizzati:

![Tipi di carattere e opzioni di colore per il codice R](media/editing-syntax-colors-options.png)

Visual Studio sottolinea anche gli errori di sintassi nell'editor:

![Evidenziazione degli errori di sintassi nel codice R](media/editing-syntax-error.png)

Per modificare questo comportamento, vedere l'impostazione **Controllo**  >  **sintassi avanzata** in Opzioni [dell'editor.](#editor-options)

## <a name="edit-and-organize-code"></a>Modificare e organizzare il codice

Durante la digitazione del codice, RTVS offre il completamento automatico come descritto nella pagina su [IntelliSense](r-intellisense.md). Esegue anche la formattazione automatica, completando ad esempio il codice con graffe e parentesi:

![Animazione della formattazione inline](media/editing-inline-formatting.gif)

Quando si digitano chiamate a funzioni con molti parametri, spesso si vuole allineare i parametri per semplificare la lettura del codice. RTVS ricorda il rientro impostato per i parametri e lo applica automaticamente alle righe successive:

![Animazione del rientro automatico](media/editing-auto-indentation.gif)

Per modificare questo comportamento, vedere le [opzioni dell'editor](#editor-options) per il gruppo **Tabulazioni**.

Le aree di codice comprimibili consentono di nascondere temporaneamente parte del codice nell'editor. Visual Studio automaticamente diverse aree, come per le istruzioni su più righe, a meno che l'opzione Struttura codice struttura avanzata non sia impostata  >    >   su Off.

Per creare un'area personalizzata, racchiudere il codice interessato con commenti che terminano con `---`. Il piccolo controllo + /- a sinistra del codice consente di espandere e comprimere le aree:

![Creazione di un'area comprimibile con commenti](media/editing-collapsible-regions.gif)

Per impostazione predefinita, Visual Studio inserisce spazi quando si preme **TAB.** Anche in questo caso è possibile modificare tale comportamento, seguendo le istruzioni descritte in [Opzioni, Editor di testo, Tutti i linguaggi](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Esplorazione del codice

Grazie all'esplorazione del codice è possibile accedere rapidamente al codice sorgente del programma R e alle sue librerie. Queste funzionalità consentono di restare nel flusso di lavoro senza dover eseguire manualmente ricerche nel codice.

**Vai a definizione** consente di passare rapidamente a una definizione di funzione o di visualizzare un editor inline ridotto per leggere il codice sorgente di una funzione di libreria. È sufficiente fare clic con il pulsante destro del mouse sulla funzione di interesse e scegliere **Vai a** definizione oppure posizionare il cursore nella funzione e premere **F12.**

Questo comando apre una nuova finestra dell'editor contenente il codice sorgente per la funzione. Per praticità, il cursore viene posizionato all'inizio della definizione della funzione.

**Visualizza definizione**, richiamato dal menu di scelta rapida o **alt** + **F12,** inserisce un'area scorrevole di sola lettura contenente il codice sorgente della funzione sotto la chiamata di funzione:

![Animazione per Visualizza definizione](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Inviare codice alla finestra interattiva

Molti sviluppatori preferiscono scrivere il codice nell'editor e inviarlo alla [finestra interattiva](interactive-repl-for-r-in-visual-studio.md) per eseguire immediatamente il test, noto anche come ciclo Read–Eval–Print o REPL. Premendo **CTRL** + **INVIO** nell'editor R, la riga di codice corrente viene inviata alla finestra interattiva, quindi il cursore viene posizionato sulla riga successiva. Con **CTRL** INVIO è quindi possibile eseguire il codice un'istruzione alla volta + dall'editor.

È anche possibile selezionare il codice e premere **CTRL** + **INVIO** per applicare l'intera selezione. In alternativa, fare clic con il pulsante destro del mouse sul codice selezionato e scegliere **Esegui in interattivo**.

## <a name="format-code"></a>Codice formato

La formattazione automatica di Visual Studio consente di usare la formattazione definita nelle preferenze per il codice che si sta scrivendo e per il codice incollato nell'editor. È anche possibile effettuare una selezione, fare clic con il pulsante destro del mouse e selezionare **Formatta** selezione (**CTRL** + **K**,**F**) per applicare tali preferenze. Ad esempio, se la definizione di funzione era interamente su una singola riga:

```R
f<-function  (a){  return(a + 1) }
```

Applicando la formattazione, il codice viene pulito:

```R
f <- function(a) { return(a + 1) }
```

Per riformattare l'intero file di codice, selezionare **Modifica**  >  **documento**  >  **di formato avanzato** (**CTRL** + **E**,**D**).

La formattazione automatica è un'operazione distinta che può essere annullata. Ad esempio, se si incolla il codice nell'editor e si applica la formattazione, selezionando Modifica annulla o premendo CTRL Z una volta inverte la formattazione. Un secondo comando Annulla inverte l'operazione  >    +  incollata. 

Le opzioni di formattazione(inclusa la disattivazione della formattazione) vengono impostate tramite **Opzioni** strumenti nella scheda  >   R Avanzate **dell'editor**  >    >  **di** testo. È possibile passare direttamente a questa pagina usando il comando opzioni editor di **R Tools** oppure facendo clic con il pulsante destro del mouse nell'editor e selezionando Opzioni  >   di **formattazione**. Vedere la sezione relativa alle [opzioni dell'editor](#editor-options) per informazioni dettagliate.

## <a name="inserting-roxygen-comments"></a>Inserimento di commenti Roxygen

RTVS offre un collegamento per la generazione di commenti [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) che usa i nomi dei parametri di una funzione. È sufficiente digitare `###` in una riga vuota sopra la definizione della funzione:

![Animazione dell'inserimento di un commento Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opzioni dell'editor

Le opzioni specifiche dell'editor vengono impostate tramite il comando Opzioni degli strumenti, passando all'Editor di testo R oppure usare il comando di scelta rapida Opzioni editor  >   di R   >     >  **Tools.**

Le opzioni contenute nelle schede **Generale**, **Barre di scorrimento** e **Tabulazioni** non sono specifiche di R, ma piuttosto sono impostazioni generali di Visual Studio disponibili per tutti i linguaggi, ma che vengono applicate a seconda del linguaggio. Per informazioni dettagliate, vedere gli articoli seguenti:

- [Opzioni, Editor di testo, Tutti i linguaggi](../ide/reference/options-text-editor-all-languages.md)
- [Procedura: Tenere traccia del codice personalizzando la barra di scorrimento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opzioni, Editor di testo, Tutti i linguaggi, Tabulazioni](../ide/reference/options-text-editor-all-languages-tabs.md)

Le opzioni nella **scheda**  >  **R Avanzate** sono specifiche di RTVS:

| Group | Opzione | Predefinito | Descrizione |
| --- | --- | --- | --- |
| Formattazione | Formattazione automatica | On | Riformatta il codice durante la digitazione. Non condiziona i comandi **Formatta selezione** o **Formatta documento**. |
| | Parentesi graffe espanse | Off | Inserisce una { aperta in una nuova riga. |
| | Formatta dopo Incolla | On | Applica la formattazione dopo aver incollato. |
| | Formatta ambito dopo } | On | Formatta l'ambito dopo aver digitato una } chiusa. |
| | Spazio dopo la virgola | On | Inserisce uno spazio dopo le virgole. |
| | Spazio dopo parola chiave | On | Inserisce uno spazio dopo parole chiave come `if`, `while` e `repeat`. |
| | Spazio prima di { | On | Inserisce uno spazio prima di una { aperta. |
| | Spazio prima e dopo = | On | Inserisce spazi prima e dopo un segno di uguale. |
| IntelliSense | Esegui il commit quando si preme INVIO | Off | Esegue il commit della selezione di completamento automatico **quando si preme** INVIO. |
| | Esegui il commit quando si preme la BARRA SPAZIATRICE | Off | Esegue il commit della selezione di completamento automatico quando **viene premuto** spazio.|
| | Elenco di completamento dopo la digitazione del primo carattere | On | Visualizza l'elenco di completamento dopo aver digitato i primi caratteri. Se disattivata, viene visualizzato un elenco di completamento con **Modifica**  >  **membri elenco IntelliSense**(  >   **CTRL** + **J**). |
| | Elenco di completamento sul **tasto** TAB | Off | Richiama l'elenco di completamento digitando uno o più caratteri e premendo **TAB.** |
| | Corrispondenza con nomi di argomento parzialmente digitati | Off | Quando si digitano i nomi degli argomenti in una chiamata di funzione, la guida alla firma mostra una descrizione per l'argomento che rappresenta la corrispondenza migliore. |
| Finestra interattiva | Controllo della sintassi nella console R | Off | Applica il controllo della sintassi nella finestra interattiva. Il controllo della sintassi non funziona correttamente se viene applicato a istruzioni su più righe. |
| struttura | Struttura del codice | On | Crea automaticamente aree comprimibili in caso di istruzioni su più righe. |
| Controllo della sintassi | Mostra errori di sintassi | On | Abilita il controllo automatico della sintassi del codice. |
