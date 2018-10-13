---
title: Scrittura di codice nell'Editor di testo e del codice | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 64b8af9e995dc863fe578f61e22647726da73b35
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220532"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Scrittura di codice nell'Editor di testo e del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
L'editor di Visual Studio fornisce diverse funzionalità che semplificano la scrittura e la gestione del codice. È possibile espandere e comprimere diversi blocchi di codice usando la struttura. Per altre informazioni sul codice in uso, vedere IntelliSense, **Visualizzatore oggetti**e Gerarchia di chiamata. Per spostarsi all'interno del codice, usare funzionalità come **Passa a**, **Vai a definizione**e **Trova tutti i riferimenti**. È possibile inserire i blocchi di codice con i frammenti di codice e generare il codice usando funzionalità come **Generazione dall'utilizzo**. Se non si è mai usato l'editor di Visual Studio 2015 in precedenza, vedere [Modifica del codice](https://www.visualstudio.com/features/ide-vs) per una rapida panoramica.  

 Il codice può essere visualizzato in diversi modi. Per visualizzare una visualizzazione classi della soluzione, è possibile aprire la finestra **Visualizzazione classi** o espandere i nodi in **Esplora soluzioni** nei file di classe.  

 È possibile cercare e sostituire il testo per file singoli o per più file. Per altre informazioni, vedere [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md). Se si usano le espressioni regolari, si noti che la funzionalità di ricerca e sostituzione adesso usa le espressioni regolari di .NET. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 I diversi linguaggi di Visual Studio offrono set di funzionalità diversi e, in alcuni casi, le funzionalità si comportano in modo diverso a seconda del linguaggio. Molte di queste differenze sono specificate nelle descrizioni delle funzionalità, ma per altre informazioni è possibile vedere le sezioni su linguaggi specifici di Visual Studio.  

> [!IMPORTANT]
>  L'edizione di Visual Studio e le impostazioni in uso possono influire sulle funzionalità nell'IDE, che potrebbero essere diverse da quelle descritte in questo argomento.  

## <a name="editor-features"></a>Funzionalità dell'editor  

|||  
|-|-|  
|Colorazione della sintassi|Alcuni elementi della sintassi del codice e dei file di markup sono colorati in modo diverso per distinguerli. Ad esempio, le parole chiave (ad esempio `using` in C# e `Imports` in Visual Basic) sono di un colore, mentre i tipi (ad esempio `Console` e `Uri`) sono di un altro colore. Anche altri elementi della sintassi sono colorati, ad esempio i valori letterali stringa e i commenti. C++ usa i colori per distinguere i tipi, le enumerazioni e le macro dagli altri token.<br /><br /> È possibile visualizzare il colore predefinito per ogni tipo e modificare il colore per ogni specifico elemento della sintassi nella finestra di dialogo [Opzioni, Ambiente, Tipi di carattere](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), che può essere aperta dal menu **Strumenti**.|  
|Contrassegni di errore e di avviso|Quando si aggiunge codice e si compila la soluzione, vengono visualizzate (a) sottolineature ondulate con diversi colori (note come sottolineature a zigzag) o (b) lampadine nel codice. Le sottolineature rosse denotano errori di sintassi, quelle blu errori del compilatore, quelle verdi gli avvisi e quelle viola altri tipi di errore. Le [lampadine](../ide/perform-quick-actions-with-light-bulbs.md) suggeriscono correzioni dei problemi e ne semplificano l'applicazione.<br /><br /> I colori predefiniti per ogni sottolineatura di errore e di avviso possono essere visualizzati nella finestra di dialogo **Strumenti/Opzioni/Ambiente/Tipi di carattere e colori**. Cercare **Errore di sintassi**, **Errore del compilatore**, **Avviso**e **Altro errore**.|  
|Corrispondenza parentesi graffe|Quando il punto di inserimento viene inserito in una parentesi graffa di apertura in un file di codice, il punto e la parentesi graffa di chiusura vengono evidenziati. Questa funzionalità consente di ottenere un feedback immediato sulle parentesi graffe inserite non correttamente o mancanti. È possibile attivare o disattivare la corrispondenza tra parentesi graffe con l'impostazione **Evidenzia delimitatore automatico** (**Strumenti/Opzioni/Editor di testo**). È possibile modificare il colore di evidenziazione nell'impostazione **Tipi di carattere e colori** (**Strumenti/Opzioni/Ambiente**). Cercare **Corrispondenza parentesi (evidenziate)** o **Corrispondenza parentesi (rettangolo)**.|  
|Numeri di riga|I numeri di riga possono essere visualizzati nel margine sinistro della finestra del codice. Non vengono visualizzati per impostazione predefinita. È possibile attivare questa opzione nelle impostazioni **Tutti i linguaggi dell'Editor di testo** (**Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**). È possibile visualizzare i numeri di riga per i singoli linguaggi di programmazione cambiando le impostazioni per i linguaggi (**Strumenti/Opzioni/Editor di testo/\<linguaggio>**). Per stampare i numeri di riga, è necessario selezionare Includi numeri di riga nella finestra di dialogo **Stampa**.|  
|Rilevamento modifiche|Il colore del margine sinistro consente di tenere traccia delle modifiche apportate al file. Le modifiche apportate dall'apertura del file ma non ancora salvate vengono contrassegnate con una barra gialla nel margine sinistro (noto come margine di selezione). Dopo aver salvato le modifiche, ma prima di chiudere il file, la barra diventa verde. Se si annulla una modifica dopo aver salvato il file, la barra diventa arancione. Per attivare e disattivare questa funzionalità, modificare l'opzione **Revisioni** nelle impostazioni **Editor di testo** (**Strumenti/Opzioni/Editor di testo**).|  
|Selezione di codice e testo|È possibile selezionare il testo con la modalità standard a flusso continuo oppure con la modalità riquadro, in cui non viene selezionato un set di righe, ma una porzione rettangolare di testo. Per effettuare una selezione in modalità riquadro, premere ALT mentre si trascina il mouse sulla selezione oppure premere ALT+MAIUSC+\<tasto di direzione>. La selezione include tutti i caratteri nel rettangolo definiti dal primo e dall'ultimo carattere nella selezione. Tutto ciò che viene digitato o incollato nell'area selezionata viene inserito nello stesso punto di ogni riga.|  
|Zoom|È possibile ingrandire o ridurre qualsiasi finestra del codice tenendo premuto CTRL e spostando la rotellina del mouse (oppure CTRL+MAIUSC+. per ingrandire e CTRL+MAIUSC+, per ridurre). Per impostare una specifica percentuale di zoom, è anche possibile usare la casella Zoom nell'angolo in basso a sinistra della finestra del codice. La funzionalità di zoom non funziona nelle finestre degli strumenti.|  
|Spazio virtuale|Per impostazione predefinita, le righe nell'editor di Visual Studio terminano dopo l'ultimo carattere, quindi il tasto freccia DESTRA alla fine della riga sposta il cursore all'inizio della riga successiva. In altri editor, una riga non termina dopo l'ultimo carattere ed è possibile posizionare il cursore in qualsiasi punto della riga. È possibile abilitare lo spazio virtuale nell'editor nelle impostazioni **Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**. È possibile abilitare **Spazio virtuale** o **A capo automatico**, ma non entrambi.|  
|Stampa|È possibile usare le opzioni nella finestra di dialogo **Stampa** per includere i numeri di riga o nascondere le aree di codice compresse quando si stampa un file. Nella finestra di dialogo **Imposta pagina** è possibile scegliere di stampare il percorso completo e il nome del file scegliendo **Intestazione pagina**.<br /><br /> È possibile impostare le opzioni di stampa a colori nella finestra di dialogo **Strumenti/Opzioni/Ambiente/Tipi di carattere e colori**. Scegliere **Stampante** nell'elenco **Mostra impostazioni per** per personalizzare la stampa a colori. Per la stampa di un file è possibile specificare colori diversi rispetto alla modifica di un file.|  
|Fasi di rollforward e rollback globali|I comandi **Annulla ultima azione globale** e **Ripeti ultima azione globale** nel menu **Modifica** annullano o ripetono le azioni globali che interessano più file. Le azioni globali includono la ridenominazione di una classe o di uno spazio dei nomi, l'esecuzione di un'operazione di ricerca e sostituzione in una soluzione, il refactoring di un database o altre azioni che modificano più file. È possibile applicare questi comandi globali alle azioni nella sessione corrente di Visual Studio anche dopo aver chiuso la soluzione alla quale è stata applicata un'azione.|  

## <a name="advanced-editing-features"></a>Funzionalità di modifica avanzate  
 Diverse funzionalità avanzate sono disponibili nel sottomenu **Modifica/Avanzate**. Non tutte le funzionalità sono disponibili per tutti i tipi di file di codice.  

|||  
|-|-|  
|Formatta documento|Imposta il rientro corretto per le righe di codice e sposta le parentesi graffe in righe separate nel documento.|  
|Formatta selezione|Imposta il rientro corretto per le righe di codice e sposta le parentesi graffe in righe separate nella selezione.|  
|Inserisci tabulazione in righe selezionate|Cambia gli spazi iniziali in tabulazioni dove appropriato.|  
|Rimuovi tabulazione da righe selezionate|Cambia le tabulazioni iniziali in spazi. Per convertire tutti gli spazi nel file in tabulazioni (o tutte le tabulazioni in spazi), è possibile usare i comandi `Edit.ConvertSpacesToTabs` e `Edit.ConvertTabsToSpaces`. Questi comandi non vengono visualizzati nei menu di Visual Studio, ma possono essere richiamati dalla finestra di accesso rapido o dalla finestra di comando.|  
|Maiuscole|Converte in maiuscolo tutti i caratteri nella selezione oppure, se non sono state effettuate selezioni, converte in maiuscolo il carattere nel punto di inserimento.|  
|Minuscole|Converte in minuscolo tutti i caratteri nella selezione oppure, se non sono state effettuate selezioni, converte in minuscolo il carattere nel punto di inserimento.|  
|Convalida documento|Convalida i file di codice JScript.|  
|Elimina spazio vuoto superfluo|Elimina le tabulazioni o gli spazi alla fine della riga corrente.|  
|Mostra/Nascondi spazi|Visualizza gli spazi sotto forma di punti mediani e le tabulazioni sotto forma di frecce. La fine di un file viene visualizzata come un glifo rettangolare. Se è selezionato **Strumenti/Opzioni/Editor di testo/Tutti i linguaggi/A capo automatico/Mostra icone per ritorno a capo automatico**, viene visualizzato anche il glifo.|  
|A capo automatico|Rende visibili tutte le righe di un documento nella finestra del codice. È possibile attivare e disattivare il ritorno a capo nelle impostazioni Tutti i linguaggi dell'editor di testo (**Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**).|  
|Rimuovi commento selezione|Aggiunge caratteri di commento alla selezione o alla riga corrente.|  
|Commenta selezione|Rimuove tutti i caratteri di commento dalla selezione o dalla riga corrente.|  
|Aumenta rientro riga|Aggiunge una tabulazione (o gli spazi equivalenti) alle righe selezionate o alla riga corrente.|  
|Riduci rientro riga|Rimuove una tabulazione (o gli spazi equivalenti) dalle righe selezionate o dalla riga corrente.|  
|Seleziona tag|In un documento che contiene tag, ad esempio XML o HTML, seleziona il tag.|  
|Seleziona contenuto tag|In un documento che contiene tag, ad esempio XML o HTML, seleziona il contenuto.|  

## <a name="navigate-in-the-code-window"></a>Spostarsi nella finestra del codice  
 È possibile spostarsi in un documento in diversi modi. Oltre alle operazioni standard, è possibile usare i pulsanti **Posizione precedente** (o CTRL + MENO) e **Posizione successiva** (CTRL + MAIUSC + MENO) nella barra degli strumenti per spostare il punto di inserimento nelle posizioni precedenti o tornare alle posizioni più recenti nel documento attivo. Questi pulsanti conservano le ultime 20 posizioni del punto di inserimento.  

 ![Pulsanti di navigazione per spostarsi avanti e indietro](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")  

 Per una panoramica del codice, è anche possibile usare la barra di scorrimento avanzata in una finestra del codice. In modalità di mapping è possibile visualizzare l'anteprima del codice quando si sposta il cursore verso l'alto e verso il basso nella barra di scorrimento. Per altre informazioni, vedere [How to: Track Your Code by Customizing the Scrollbar](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

 I comandi seguenti sono metodi di spostamento specifici per il codice:  

|||  
|-|-|  
|Vai a \<numero di riga>|(**Modifica/Vai a** o CTRL + G): spostarsi a uno specifico numero di riga nel documento attivo.|  
|Passa a|(**Modifica/Passa a** o CTRL + ,): trova un simbolo o un file nella soluzione attiva. Consente di ottenere un buon numero di risultati corrispondenti da una query. È possibile cercare parole chiave contenute in un simbolo usando la convenzione Camel e i caratteri di sottolineatura per dividere il simbolo in parole chiave.|  
|Trova tutti i riferimenti|(Menu di scelta rapida): trova tutti i riferimenti all'elemento selezionato nella soluzione|  
|Vai a definizione|(Menu di scelta rapida o F12): trova la definizione dell'elemento selezionato.|  
|Visualizza definizione|(Menu di scelta rapida o Alt+F12): trova la definizione dell'elemento selezionato e la visualizza in una finestra popup. Per altre informazioni, vedere [Procedura: Visualizzare e modificare il codice utilizzando la finestra Visualizza definizione (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|  
|Metodo successivo, Metodo precedente|(**Modifica/Metodo successivo, Metodo precedente**) Nei file di codice di Visual Basic, usare questi comandi per spostare il punto di inserimento in metodi diversi.|  
|Evidenziazione di riferimenti|Quando si fa clic su un simbolo nel codice sorgente, tutte le istanze del simbolo vengono evidenziate nel documento. I simboli evidenziati possono includere dichiarazioni e riferimenti e molti altri simboli restituiti da **Trova tutti i riferimenti**. Sono inclusi i nomi di classi, oggetti, variabili, metodi e proprietà. Nel codice Visual Basic vengono evidenziate anche le parole chiave per molte strutture di controlli. Per spostarsi al simbolo evidenziato successivo o precedente, premere CTRL+MAIUSC+ freccia GIÙ o CTRL+MAIUSC+freccia SU. È possibile modificare il colore di evidenziazione in **Strumenti/Opzioni/Ambiente/Tipi di carattere e colori/Riferimento evidenziato.**|  
|Trova informazioni relative al codice|È possibile trovare informazioni relative a codice specifico, ad esempio modifiche, autori delle modifiche, riferimenti, bug, elementi di lavoro, revisioni del codice e stato dello unit test quando si usa CodeLens nell'editor del codice. CodeLens funziona come una visualizzazione preliminare quando si usa Visual Studio Enterprise con Team Foundation Server. Vedere [Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md).|  

 Per spostarsi in un file di codice, è anche possibile usare la **barra di navigazione**, ossia le due caselle a discesa visualizzate in alto nella finestra del codice. Questa barra consente di passare direttamente a un tipo specifico o a uno dei membri in un tipo. La barra di navigazione viene visualizzata con i file di codice Visual Basic, C# e C++.  

 Per nascondere la barra di navigazione, modificare l'opzione **Barra di navigazione** nelle impostazioni Tutti i linguaggi dell'editor di testo (**Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**oppure modificare le impostazioni per i singoli linguaggi). È possibile spostarsi tra le caselle a discesa come segue:  

-   Per spostare lo stato attivo dalla finestra del codice alla barra di spostamento, premere la combinazione di tasti di scelta rapida CTRL+F2.  

-   Per ripristinare lo stato attivo dalla barra di spostamento alla finestra del codice, premere ESC.  

-   Per spostare lo stato attivo da un elemento a un elemento nella barra di spostamento, premere TAB.  

-   Per selezionare l'elemento della barra di navigazione con stato attivo e tornare all'IDE, premere INVIO.  

-   Per spostarsi in una classe o in un tipo, fare clic sul nome nell'elenco a discesa a sinistra.  

-   Per passare direttamente a una procedura in una classe, fare clic su una procedura nell'elenco a discesa a destra.  

 In una classe parziale i membri definiti al di fuori del file di codice corrente possono non essere disponibili.  

## <a name="find-code-using-navigate-to"></a>Trovare codice con Passa a
"Passa a" comando Visual Studio consente di eseguire una ricerca mirata del codice che consentono di trovare rapidamente gli elementi specificati nel file di codice, percorsi di file e i simboli del codice. A differenza di altri strumenti di ricerca nel testo, ad esempio Trova o Cerca nei file, Passa a limita la ricerca alle aree in cui si trova il codice effettivo, ad esempio file, form e moduli di codice. Se ad esempio si cerca una stringa in un'applicazione Web ASP.NET usando Trova o Cerca nei file nell'intera soluzione, si potrebbero ottenere diversi risultati, incluse istanze della stringa nelle note sul codice. Con passa a, tuttavia, si potrebbe ottengono solo una singola funzione, ignorando tutte le istanze della stringa nei commenti del codice.

### <a name="navigate-code-using-navigate-to"></a>Esplorare il codice con Passa a

1. Aprire una soluzione o una cartella in Visual Studio.
1. Nel menu principale scegliere **Modifica**, **Passa a** oppure premere **CTRL + ,**.

    Viene visualizzata una piccola casella di testo nell'angolo superiore dell'editor di codice.
1. Immettere il nome dell'elemento di codice da cercare nella casella di testo.

    ![Finestra Passa a](../ide/media/vside-navigatetowindow.png "Finestra Passa a")

    Durante la digitazione i risultati vengono visualizzati in un elenco a discesa sotto la casella di testo.
1. Per passare a un elemento, selezionarlo nell'elenco.


### <a name="filter-your-search"></a>Filtrare la ricerca

Per limitare la ricerca solo ai simboli del codice, anteporre alla query Passa a un carattere "@". Ad esempio, se si cerca `@application`, Passa a visualizza solo le classi che contengono la parola "application".

Se si usa la convenzione camel per maiuscole e minuscole nel codice, è possibile trovare gli elementi di codice più rapidamente immettendo solo le lettere maiuscole dei nomi degli elementi di codice. Ad esempio, se il codice ha un componente denominato `ViewSwitcher`, è possibile trovarlo immettendo solo le lettere maiuscole del nome (`"VS"`) nella finestra Passa a.

![Finestra Passa a - ricerca con lettere maiuscole](../ide/media/vside-capitalsearch.png "Finestra Passa a - ricerca con lettere maiuscole")

Questa funzionalità è particolarmente utile se il codice contiene nomi lunghi.

## <a name="customize-the-editor"></a>Personalizzare l'editor  
 **Importare ed esportare le impostazioni**: è possibile condividere le impostazioni con un altro sviluppatore, renderle conformi a uno standard o ripristinare le impostazioni predefinite di Visual Studio usando **Importazione/Esportazione guidata delle impostazioni** nel menu **Strumenti** . È possibile modificare le impostazioni generali o le impostazioni specifiche di un linguaggio o di un progetto.  

 **Mapping della tastiera**: è possibile definire i nuovi tasti di scelta o ridefinire quelli esistenti nelle impostazioni Strumenti/Opzioni/Ambiente/Tastiera. Per altre informazioni sui tasti di scelta rapida, vedere [Tasti di scelta rapida predefiniti](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

 Per informazioni sulle opzioni dell'editor specifiche di un linguaggio, vedere:  

-   [Impostazioni di Visual Basic](http://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)  

-   [Using the Visual Studio Development Environment for C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) (Uso dell'ambiente di sviluppo di Visual Studio per C#)  

-   [Opzioni, Editor di testo, JavaScript, formattazione](../ide/reference/options-text-editor-javascript-formatting.md)  

## <a name="in-this-section"></a>Contenuto della sezione  

-   [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)  

-   [Codifiche e interruzioni di riga](../ide/encodings-and-line-breaks.md)  

-   [Struttura](../ide/outlining.md)  

-   [Refactoring](../ide/refactoring-in-visual-studio.md)  

-   [Suggerimenti per la produttività](../ide/productivity-tips-for-visual-studio.md)  

-   [Utilizzo di IntelliSense](../ide/using-intellisense.md)  

-   [Personalizzazione dell'editor](../ide/customizing-the-editor.md)  

-   [Procedura: Tenere traccia del codice personalizzando la barra di scorrimento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)  

-   [Procedura: Visualizzare e modificare il codice utilizzando la finestra Visualizza definizione (ALT+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  

-   [Eseguire azioni rapide con le lampadine](../ide/perform-quick-actions-with-light-bulbs.md)  

-   [Frammenti di codice](../ide/code-snippets.md)  

-   [Utilizzo della Casella degli strumenti](../ide/using-the-toolbox.md)  

-   [Visualizzazione della struttura del codice](../ide/viewing-the-structure-of-code.md)  

-   [Impostazione di segnalibri nel codice](../ide/setting-bookmarks-in-code.md)  

-   [Utilizzo dell'elenco attività](../ide/using-the-task-list.md)  

-   [Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md)  

## <a name="see-also"></a>Vedere anche  
 [IDE di Visual Studio](../ide/visual-studio-ide.md)


