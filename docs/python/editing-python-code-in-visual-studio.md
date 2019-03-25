---
title: Modificare il codice Python
description: Per Python, Visual Studio offre funzionalità IntelliSense avanzate, frammenti di codice e funzionalità di navigazione, nonché formattazione, rilevamento di errori con Lint e refactoring.
ms.date: 03/13/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0c7091a55487f83c88323d68ae8075630d39d471
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155524"
---
# <a name="edit-python-code"></a>Modificare il codice Python

Poiché si passa molto tempo nell'editor di codice, il [supporto per Python in Visual Studio](installing-python-support-in-visual-studio.md) offre funzionalità che consentono di migliorare la produttività. Le funzionalità includono evidenziazione della sintassi di IntelliSense, completamento automatico, supporto per la firma digitale, override dei metodi, ricerca e navigazione.

L'editor è anche integrato con la finestra **interattiva** in Visual Studio, semplificando così lo scambio di codice tra i due prodotti. Per i dettagli, vedere il [Passaggio 3 dell'esercitazione: Usare la finestra interattiva REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) e [Usare la finestra interattiva - Comando Invia a finestra interattiva](python-interactive-repl-in-visual-studio.md#send-to-interactive-command).

Per informazioni generali sulla modifica del codice in Visual Studio, vedere [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md). Vedere anche [Struttura](../ide/outlining.md) per informazioni su questa funzionalità che consente di concentrarsi su sezioni specifiche del codice.

È anche possibile usare il **Visualizzatore oggetti** di Visual Studio (**Visualizza** > **Altre finestre** > **Visualizzatore oggetti** o **CTRL**+**W** > **J**) per esaminare le classi di Python definite in ogni modulo e le funzioni definite in tali classi.

## <a name="intellisense"></a>IntelliSense

IntelliSense offre [completamenti](#completions), [informazioni della Guida per le firme](#signature-help), [informazioni rapide](#quick-info) e [colorazione del codice](#code-coloring). Visual Studio 2017 versione 15.7 e versioni successive supporta anche i [suggerimenti relativi al tipo](#type-hints).

Per migliorare le prestazioni, IntelliSense in **Visual Studio 2017 versione 15.5** e versioni precedenti dipende da un database di completamento generato per ogni ambiente Python nel progetto. Può essere necessario aggiornare i database se si aggiungono, si rimuovono o si aggiornano i pacchetti. Lo stato dei database viene visualizzato nella finestra **Ambienti Python**, elemento di pari livello di **Esplora soluzioni**, nella scheda **IntelliSense** (vedere [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md#intellisense-tab)).

**Visual Studio 2017 versione 15.6** e versioni successive usano modi diversi per fornire i completamenti IntelliSense, non dipendenti dal database.

### <a name="completions"></a>Completamenti

I completamenti vengono visualizzati come istruzioni, identificatori e altre parole che possono essere immessi in modo corretto nella posizione corrente nell'editor. Il contenuto dell'elenco dipende dal contesto e viene filtrato per omettere opzioni non corrette o fonte di distrazione. I completamenti vengono spesso attivati digitando istruzioni (ad esempio `import`) e operatori (incluso un punto) diversi, ma è possibile visualizzarli in qualsiasi momento digitando **CTRL**+**J** > **BARRA SPAZIATRICE**.

![Completamento dei membri nell'editor di Visual Studio](media/code-editing-completions-simple.png)

Quando viene aperto un elenco di completamento, è possibile cercare il completamento desiderato usando i tasti di direzione, il mouse oppure continuando a digitare. Digitando altre lettere l'elenco viene ulteriormente filtrato per mostrare i completamenti probabili. È anche possibile usare i tasti di scelta rapida, ad esempio:

- Digitare lettere che non si trovano all'inizio del nome, come 'parse' per trovare 'argparse'
- Digitare solo le lettere che si trovano all'inizio di parole, come 'abc' per trovare 'AbstractBaseClass' o 'air' per trovare 'as_integer_ratio'
- Omettere lettere, ad esempio 'b64' per trovare 'base64'

Ecco alcuni esempi:

![Completamento dei membri con i filtri nell'editor di Visual Studio](media/code-editing-completion-filtering.png)

I completamenti dei membri appaiono automaticamente quando si digita un punto dopo una variabile o un valore, insieme ai metodi e agli attributi dei tipi potenziali. Se una variabile può avere più di un tipo, l'elenco include tutte le possibilità per tutti i tipi, con informazioni aggiuntive per indicare quali tipi supportano ogni completamento. Nel caso un completamento sia supportato da tutti i tipi possibili, viene visualizzato senza annotazione.

![Completamento dei membri su più tipi nell'editor di Visual Studio](media/code-editing-completion-types.png)

Per impostazione predefinita, non vengono visualizzati i cosiddetti membri "dunder", il cui nome inizia e termina con un doppio carattere di sottolineatura. In generale, non si deve accedere direttamente a tali membri. Se tuttavia è necessario un membro di questo tipo, digitando un doppio carattere di sottolineatura iniziale i seguenti completamenti vengono aggiunti all'elenco:

![Completamento dei membri privati nell'editor di Visual Studio](media/code-editing-completion-dunder.png)

Le istruzioni `import` e `from ... import` visualizzano un elenco dei moduli che possono essere importati. Con `from ... import`, l'elenco include i membri che possono essere importati dal modulo specificato.

![Completamento dell'importazione nell'editor di Visual Studio](media/code-editing-completion-import.png)

Per le istruzioni `raise` e `except` vengono visualizzati gli elenchi di classi che probabilmente sono tipi di errore. L'elenco può non includere tutte le eccezioni definite dall'utente, ma consente di trovare rapidamente le eccezioni predefinite appropriate:

![Completamento delle eccezioni nell'editor di Visual Studio](media/code-editing-completion-exception.png)

È possibile digitare @ per iniziare un elemento Decorator e visualizzare gli elementi Decorator potenziali. Molti di questi elementi non possono essere usati come elementi Decorator. Consultare la documentazione della libreria per determinare quali usare.

![Completamento di elementi Decorator nell'editor di Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> È possibile configurare il comportamento dei completamenti tramite **Strumenti** > **Opzioni** > **Editor di testo** > **Python** > **Avanzate**. Tra le opzioni disponibili, **Filtra elenco in base alla stringa di ricerca** consente di applicare il filtro ai suggerimenti per il completamento durante la digitazione. Questa opzione è selezionata per impostazione predefinita. L'opzione **Il completamento dei membri visualizza l'intersezione dei membri** consente di visualizzare solo i completamenti supportati da tutti i tipi possibili (deselezionata per impostazione predefinita). Vedere [Opzioni - Risultati del completamento](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Suggerimenti relativi al tipo

*Visual Studio 2017 15.7 e versioni successive.*

I "suggerimenti relativi al tipo" in Python 3.5+ ([PEP 484](https://www.python.org/dev/peps/pep-0484/) (python.org) rappresentano una sintassi di annotazione per le funzioni e le classi che indicano i tipi di argomenti, valori restituiti e attributi di classi. IntelliSense visualizza i suggerimenti relativi al tipo quando si passa il mouse su chiamate di funzioni, argomenti e variabili che presentano tali annotazioni.

Nell'esempio seguente la classe `Vector` viene dichiarata come `List[float]` e la funzione `scale` contiene suggerimenti relativi al tipo sia per gli argomenti sia per il valore restituito. Con il passaggio del mouse su una chiamata a tale funzione vengono visualizzati i suggerimenti relativi al tipo:

![Passaggio del mouse su una chiamata di funzione per visualizzare i suggerimenti relativi al tipo](media/code-editing-type-hints1.png)

Nell'esempio seguente è possibile visualizzare il modo in cui gli attributi con annotazioni della classe `Employee` vengono visualizzati nella finestra popup di completamento di IntelliSense per un attributo:

![Suggerimenti relativi al tipo visualizzati nel completamento di IntelliSense](media/code-editing-type-hints2.png)

È inoltre utile convalidare i suggerimenti relativi al tipo in tutto il progetto, poiché gli errori in genere non vengono visualizzati prima dell'esecuzione. A tale scopo, Visual Studio integra lo strumento MyPy standard del settore attraverso il comando del menu di scelta rapida **Python** > **Esegui Mypy** in **Esplora soluzioni**:

![Eseguire il comando MyPy del menu di scelta rapida in Esplora soluzioni](media/code-editing-type-hints-run-mypy.png)

Con l'esecuzione del comando viene richiesta l'installazione del pacchetto mypy, se necessario. Visual Studio esegue quindi mypy per convalidare i suggerimenti relativi al tipo in ogni file Python del progetto. Gli errori vengono visualizzati nella finestra **Elenco errori** di Visual Studio. Se si seleziona un elemento nella finestra, si passa alla riga appropriata nel codice.

Come esempio semplice, la seguente definizione di funzione contiene un suggerimento relativo al tipo per indicare che l'argomento `input` è di tipo `str`, mentre la chiamata a tale funzione tenta di passare un numero intero:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Se si usa il comando **Esegui Mypy** su questo codice, viene generato l'errore seguente:

![Esempio di risultato di mypy che convalida i suggerimenti relativi al tipo](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Per le versioni di Python precedenti alla 3.5, Visual Studio visualizza anche i suggerimenti relativi al tipo specificati nei *file stub* (con estensione *pyi*) di Typeshed. I file stub possono essere usati quando non si vuole includere i suggerimenti relativi al tipo direttamente nel codice o quando si vogliono creare suggerimenti relativi al tipo per una libreria che non li usa direttamente. Per altre informazioni, vedere [Create Stubs for Python Modules](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) (Creare stub per i moduli Python) nel wiki del progetto mypy.
>
> Al momento Visual Studio non supporta i suggerimenti relativi al tipo nei commenti.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Per le versioni di Python precedenti alla 3.5, Visual Studio visualizza anche i suggerimenti relativi al tipo specificati nei *file stub* (con estensione *pyi*) di Typeshed. I file stub possono essere usati quando non si vuole includere i suggerimenti relativi al tipo direttamente nel codice o quando si vogliono creare suggerimenti relativi al tipo per una libreria che non li usa direttamente. Per altre informazioni, vedere [Create Stubs for Python Modules](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) (Creare stub per i moduli Python) nel wiki del progetto mypy.
>
> Visual Studio include un set di file Typeshed in bundle per Python 2 e 3, in modo che non siano necessari ulteriori download. Tuttavia, se si vuole usare un diverso set di file, è possibile specificare il percorso nelle opzioni **Strumenti** > **Opzioni** > **Python**  >  **Server di linguaggio**. Vedere [Opzioni - Server di linguaggio](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> Al momento Visual Studio non supporta i suggerimenti relativi al tipo nei commenti.
::: moniker-end

### <a name="signature-help"></a>Supporto per la firma

Se si scrive codice che chiama una funzione, la guida per la firma digitale appare quando si digita la parentesi di apertura (`(`) e visualizza le informazioni della documentazione e sui parametri disponibili. Per visualizzare queste informazioni è anche possibile usare **CTRL**+**MAIUSC**+**BARRA SPAZIATRICE** all'interno di una chiamata di funzione. Le informazioni visualizzate dipendono dalle stringhe di documentazione nel codice sorgente della funzione, ma includono eventuali valori predefiniti.

![Guida per la firma nell'editor di Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Per disabilitare le informazioni della Guida per le firme, passare a **Strumenti** > **Opzioni** > **Editor di testo** > **Python** > **Generale** e deselezionare **Completamento istruzioni** > **Informazioni parametri**.

### <a name="quick-info"></a>Informazioni rapide

Al passaggio del mouse su un identificatore viene visualizzata una descrizione comando delle informazioni rapide. In base all'identificatore, le informazioni rapide possono visualizzare i valori o i tipi potenziali, eventuale documentazione disponibile, i tipi restituiti e i percorsi delle definizioni:

![Informazioni rapide nell'editor di Visual Studio](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Colorazione del codice

La funzionalità di colorazione del codice usa le informazioni dall'analisi del codice per colorare variabili, istruzioni e altre parti del codice. Ad esempio, le variabili che fanno riferimento a moduli o classi possono essere visualizzate in un colore diverso rispetto alle funzioni o altri valori e i nomi dei parametri vengono visualizzati in un colore diverso rispetto alle variabili locali o globali. Le funzioni non appaiono in grassetto per impostazione predefinita:

![Colorazione del codice e della sintassi nell'editor di Visual Studio](media/code-editing-code-coloring.png)

Per personalizzare i colori, accedere a **Strumenti** > **Opzioni** > **Ambiente** > **Tipi di carattere e colori** e modificare le voci per **Python** nell'elenco **Elementi visualizzati**:

![Opzioni di Tipi di carattere e colori in Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Per disabilitare la colorazione del codice, passare a **Strumenti** > **Opzioni** > **Editor di testo** > **Python** > **Avanzate** e deselezionare **Opzioni varie** > **Nomi dei colori in base ai tipi**. Vedere [Opzioni - Miscellaneous options (Opzioni varie)](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Frammenti di codice

I frammenti di codice sono parti di codice che possono essere inserite nei file digitando una scelta rapida e premendo **TAB** oppure tramite i comandi **Modifica** > **IntelliSense** > **Inserisci frammento di codice** e **Racchiudi tra**, selezionando **Python** e quindi il frammento desiderato.

Ad esempio, `class` è una scelta rapida per un frammento di codice che inserisce una definizione di classe. Il frammento viene visualizzato nell'elenco di completamento automatico quando si digita `class`:

![Frammento di codice per la scelta rapida per la classe](media/code-editing-code-snippet-class.png)

Premendo **TAB** viene generato il resto della classe. È quindi possibile digitare sull'elenco dei nomi e delle basi, spostarsi tra i campi evidenziati tramite **TAB** e quindi premere **INVIO** per iniziare a digitare il corpo.

![Evidenziazioni nelle aree di un frammento di codice da completare](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Comandi di menu

Quando si usa il comando di menu **Modifica** > **IntelliSense** > **Inserisci frammento di codice**, selezionare prima di tutto **Python** e quindi selezionare un frammento di codice:

![Selezione di un frammento di codice tramite il comando Inserisci frammento di codice](media/code-editing-code-snippet-insert.png)

Il comando **Modifica** > **IntelliSense** > **Racchiudi tra**, in modo analogo, posiziona la selezione corrente nell'editor di testo all'interno di un elemento strutturale scelto. Ad esempio, si supponga di avere a disposizione un blocco di codice simile al seguente:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Se si seleziona questo codice e si sceglie il comando **Racchiudi tra**, viene visualizzato un elenco dei frammenti disponibili. Se si sceglie **def** nell'elenco, il codice selezionato viene posizionato all'interno di una definizione di funzione ed è possibile spostarsi con **TAB** tra il nome della funzione e gli argomenti evidenziati:

![Uso del comando Racchiudi tra per i frammenti di codice](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Esaminare i frammenti di codice disponibili

È possibile visualizzare i frammenti di codice disponibili in **Gestione frammenti di codice**. A tale scopo, usare il comando di menu **Strumenti** > **Gestione frammenti di codice** e quindi selezionare **Python** come linguaggio:

![Gestione frammenti di codice in Visual Studio](media/code-editing-code-snippets-manager.png)

Per creare frammenti personalizzati, vedere [Procedura dettagliata: Creare un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md).

Se si scrive un frammento di codice particolarmente utile e si vuole condividerlo, pubblicarlo in un gist e [segnalarlo a Microsoft](https://github.com/Microsoft/PTVS/issues). È possibile che venga incluso in una versione futura di Visual Studio.

## <a name="navigate-your-code"></a>Esplorare il codice

Il supporto di Python in Visual Studio offre diversi strumenti per spostarsi rapidamente all'interno del codice, incluse le librerie per cui è disponibile codice sorgente: la [barra di spostamento](#navigation-bar), [**Vai a definizione**](#go-to-definition), [**Passa a**](#navigate-to) e [**Trova tutti i riferimenti**](#find-all-references). È anche possibile usare il [**Visualizzatore oggetti**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) di Visual Studio.

### <a name="navigation-bar"></a>Barra di navigazione

La barra di spostamento viene visualizzata nella parte superiore di ogni finestra dell'editor e include un elenco di definizioni su due livelli. L'elenco a discesa a sinistra contiene le definizioni di classi e funzioni di primo livello nel file corrente. L'elenco a discesa a destra visualizza un elenco di definizioni all'interno dell'ambito indicato a sinistra. Spostandosi nell'editor, gli elenchi vengono aggiornati in modo da indicare il contesto corrente ed è anche possibile selezionare una voce dagli elenchi per passarvi direttamente.

![Barra di spostamento nell'editor di Visual Studio](media/code-editing-navigation-bar.png)

> [!Tip]
> Per nascondere la barra di spostamento, passare a **Strumenti** > **Opzioni** > **Editor di testo** > **Python** > **Generale** e deselezionare **Impostazioni** > **Barra di spostamento**.

### <a name="go-to-definition"></a>Vai a definizione

Il comando **Vai a definizione** consente di passare velocemente dall'uso di un identificatore (ad esempio, un nome di funzione, una classe o una variabile) al codice sorgente in cui è definito. Per chiamare questo comando, è possibile fare clic con il pulsante destro del mouse su un identificatore e selezionare **Vai a definizione** oppure posizionare il punto di inserimento nell'identificatore e premere **F12**. Il comando viene applicato a tutto il codice e alle librerie esterne, a condizione che sia disponibile il codice sorgente. Se il codice sorgente della libreria non è disponibile, il comando **Vai a definizione** passa all'istruzione `import` pertinente per un riferimento al modulo o visualizza un errore.

![Comando Vai a definizione in Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Passa a

Il comando **Modifica** > **Passa a** (**CTRL**+**,**) consente di visualizzare una casella di ricerca nell'editor in cui è possibile digitare qualsiasi stringa e vedere le possibili corrispondenze nel codice che definisce una funzione, una classe o una variabile contenente tale stringa. La funzionalità di questo comando è simile a **Vai a definizione**, ma non richiede l'individuazione di un uso di un identificatore.

Per passare alla definizione dell'identificatore, fare doppio clic su qualsiasi nome oppure selezionarlo con i tasti di direzione e premere **INVIO**.

![Comando Passa a in Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Trova tutti i riferimenti

**Trova tutti i riferimenti** è un modo utile per individuare le posizioni in cui un qualsiasi identificatore specificato viene sia definito che usato, incluse importazioni e assegnazioni. Per chiamare questo comando, è possibile fare clic con il pulsante destro del mouse su un identificatore e scegliere **Trova tutti i riferimenti** o posizionare il punto di inserimento nell'identificatore e premere **MAIUSC**+**F12**. È possibile fare doppio clic su un elemento nell'elenco per passare alla relativa posizione.

![Risultati di Trova tutti i riferimenti](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Vedere anche

- [Formattazione](formatting-python-code.md)
- [Refactoring](refactoring-python-code.md)
- [Usare un linter](linting-python-code.md)
