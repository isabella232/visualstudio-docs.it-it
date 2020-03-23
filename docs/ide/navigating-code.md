---
title: Comandi di spostamento per il codice
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: tglee
ms.workload:
- multiple
ms.openlocfilehash: 0216a71b675473d54aec9738ea7bdc85b7643841
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585821"
---
# <a name="navigate-code"></a>Spostarsi all'interno del codice

Visual Studio offre diversi modi per spostarsi all'interno del codice nell'editor. Questo argomento contiene un riepilogo dei vari metodi di passaggio da una parte all'altra del codice e indica i collegamenti ad argomenti che scendono più in dettaglio.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Comandi Posizione precedente e Posizione successiva

È possibile utilizzare i pulsanti **Sposta indietro** (**CTRL**+**-**) e **Sposta avanti** (**Ctrl**+**MAIUSC**+**-**) sulla barra degli strumenti per spostare il punto di inserimento nelle posizioni precedenti o per tornare a una posizione più recente da una posizione precedente. Questi pulsanti conservano le ultime 20 posizioni del punto di inserimento. Questi comandi sono disponibili anche nel menu **Visualizza**, in **Posizione precedente** e **Posizione successiva**.

![Pulsanti di spostamento per spostarsi avanti e indietro](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Barra di navigazione

Per spostarsi all'interno di una codebase, è anche possibile usare la **barra di spostamento**, ovvero le caselle a discesa nella parte superiore della finestra del codice e scegliere un tipo o un membro per accedervi direttamente. La barra di spostamento viene visualizzata quando si modifica il codice in una codebase Visual Basic, C# o C++. In una classe parziale i membri definiti all'esterno del file di codice corrente potrebbero essere disabilitati (visualizzati in grigio).

![Barra di spostamento per il codice](../ide/media/vside_navigation_bar.png)

È possibile spostarsi tra le caselle a discesa come segue:

- Per passare a un altro progetto a cui appartiene il file corrente, selezionarlo nell'elenco a discesa a sinistra.

- Per spostarsi in una classe o un tipo, scegliere la classe o il tipo nell'elenco a discesa a sinistra.

- Per passare direttamente a una routine o a un altro membro di una classe, scegliere l'elemento nell'elenco a discesa a destra.

- Per spostare lo stato attivo dalla finestra del codice alla barra di spostamento, premere la combinazione di tasti di scelta rapida **Ctrl**+**F2.**

- Per spostare lo stato attivo da una casella all'altra nella barra di spostamento, premere **TAB**.

- Per selezionare l'elemento della barra di spostamento con stato attivo e tornare alla finestra del codice, premere **INVIO**.

- Per ripristinare lo stato attivo dalla barra di spostamento alla finestra del codice senza effettuare selezioni, premere **ESC**.

Per nascondere la barra di spostamento, modificare l'opzione **Barra di spostamento** nelle impostazioni Editor di testo tutti i **linguaggi** **(Opzioni di** > **opzioni** > **dell'editor** > **Tutti i linguaggi)** oppure è possibile modificare le impostazioni per le singole lingue.

## <a name="find-all-references"></a>Trova tutti i riferimenti

Trova tutti i riferimenti all'elemento selezionato nella soluzione. Con questa opzione è possibile verificare i possibili effetti collaterali di un refactoring esteso o la presenza di codice non usato. Premere **F8** per passare ai risultati. Per altre informazioni, vedere [Ricerca di riferimenti nel codice](finding-references.md).

Input | Funzione
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo e premere **Maiusc**+**F12**
**Mouse** | Scegliere **Trova tutti i riferimenti** dal menu di scelta rapida

## <a name="reference-highlighting"></a>Evidenziazione dei riferimenti

Quando si fa clic su un simbolo nel codice sorgente, tutte le istanze del simbolo vengono evidenziate nel documento. I simboli evidenziati possono includere dichiarazioni e riferimenti e molti altri simboli restituiti da **Trova tutti i riferimenti**. Sono inclusi i nomi di classi, oggetti, variabili, metodi e proprietà. Nel codice Visual Basic vengono evidenziate anche le parole chiave per molte strutture di controlli. Per passare al simbolo evidenziato successivo o precedente, premere **CTRL**+**Maiusc**+**freccia giù** o **Ctrl**+**Maiusc**+freccia**su**. È possibile modificare il colore di evidenziazione in **Opzioni strumenti** > **Opzioni** > **Caratteri** > e**colori** > **evidenziati Riferimento**.

## <a name="go-to-commands"></a>Comandi Vai a

Per Vai a sono disponibili i comandi seguenti, a cui si accede dal menu **Modifica** sotto **Vai a**:

- **Vai alla riga** (**CTRL**+**G**): consente di passare al numero di riga specificato nel documento attivo.

- **Vai a tutti** **(Ctrl**+**T** o **Ctrl**+**),**: consente di passare alla riga, al tipo, al file, al membro o al simbolo specificati.

- **Vai al file** **(Ctrl**+**1**, **Ctrl**+**F):** consente di passare al file specificato nella soluzione.

- **Vai a file recente** **(Ctrl**+**1**, **Ctrl**+**R):** consente di passare al file specificato visitato di recente nella soluzione.

- **Vai al tipo** (**Ctrl**+**1**, **Ctrl**+**T**): Consente di passare al tipo specificato nella soluzione.

- **Vai al membro** **(Ctrl**+**1**, **Ctrl**+**M**): Sposta al membro specificato nella soluzione.

- **Vai al simbolo** **(Ctrl**+**1**, **Ctrl**+**S**): Consente di passare al simbolo specificato nella soluzione.

In Visual Studio 2017 versione 15.8 e versioni successive, sono disponibili anche i comandi di spostamento **Vai a** seguenti:

- **Go To Next Issue in File** (Vai al problema successivo nel file) o **ALT**+**PGGIÙ** e **Go To Previous Issue in File** (Vai al problema precedente nel file) o **ALT**+**PGSU**

- **Vai alla posizione dell'ultima modifica** o **CTRL**+**MAIUSC**+**BACKSPACE**

Per altre informazioni su questi comandi, vedere l'argomento relativo alla [ricerca di codice con i comandi Vai a](../ide/go-to.md).

## <a name="go-to-definition"></a>Vai a definizione

Vai a definizione consente di accedere alla definizione dell'elemento selezionato. Per altre informazioni, vedere [Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md).

Input | Funzione
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo e premere **F12**
**Mouse** | Fare clic con il pulsante destro del mouse sul nome del tipo e selezionare **Vai a definizione** OPPURE premere **CTRL** e fare clic sul nome del tipo

## <a name="peek-definition"></a>Visualizza definizione

Consente di visualizzare la definizione dell'elemento selezionato in una finestra senza spostarsi dalla posizione corrente nell'editor di codice. Per ulteriori informazioni, vedere [Procedura: visualizzare e modificare il codice utilizzando Visualizza definizione](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) e [Vai a definizione e visualizza definizione](../ide/go-to-and-peek-definition.md).

Input | Funzione
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo e premere **Alt**+**F12**
**Mouse** | Fare clic con il pulsante destro del mouse sul nome del tipo e selezionare **Visualizza definizione** o premere **CTRL** e fare clic sul nome del tipo (se l'opzione **Apri definizione in visualizzazione rapida** è selezionata)

## <a name="go-to-implementation"></a>Vai all'implementazione

Vai all'implementazione consente di passare da una classe o un tipo di base alle relative implementazioni. Se esistono più implementazioni, vengono elencate nella finestra **Risultati ricerca simbolo**:

Input | Funzione
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto all'interno del nome del tipo e premere **CTRL**+**F12**
**Mouse** | Fare clic con il pulsante destro del mouse sul nome del tipo e selezionare **Vai all'implementazione**

## <a name="go-to-base"></a>Vai a base

Utilizzando Vai a base, è possibile spostarsi verso l'alto nella catena di ereditarietà dell'elemento selezionato. Se sono presenti più risultati, verranno visualizzati elencati nella finestra **Vai alla base:**

Input | Funzione
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo e premere **Alt**+**Home**
**Mouse** | Fare clic con il pulsante destro del mouse sul nome del tipo e selezionare **Vai alla base**

## <a name="call-hierarchy"></a>Gerarchia delle chiamate

È possibile visualizzare le chiamate da e verso un metodo nella [finestra Gerarchia di chiamata](../ide/reference/call-hierarchy.md):

Input | Funzione
------------ | ---
**Tastiera** | Posizionare il cursore di testo in un punto all'interno del nome del tipo e premere **Ctrl**+**K**, **Ctrl**+**T**
**Mouse** | Fare clic con il pulsante destro sul nome del membro e selezionare **Visualizza gerarchia delle chiamate**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Comandi Metodo successivo e Metodo precedente (Visual Basic)

Nei file di codice di Visual Basic usare questi comandi per spostare il punto di inserimento in metodi diversi. Scegliere **Modifica** > **metodo successivo** o **Modifica** > metodo**precedente**.

## <a name="structure-visualizer"></a>Visualizzatore di struttura

Nella funzionalità Visualizzatore di struttura dell'editor del codice sono visualizzate le *guide per strutture*, ovvero linee verticali tratteggiate che indicano la presenza di parentesi graffe corrispondenti nella codebase. In questo modo risulta più agevole visualizzare l'inizio e la fine dei blocchi logici.

![Visualizzatore di struttura](../ide/media/vside_structure_visualizer.png)

Per disattivare le linee guida della struttura, passare a **Strumenti** > **Opzioni** > Editor > **testo****generale** e deselezionare la casella Mostra linee **guida struttura** .

## <a name="enhanced-scroll-bar"></a>Barra di scorrimento ottimizzata

Per una panoramica del codice, è possibile usare la barra di scorrimento avanzata in una finestra del codice. In modalità di mapping è possibile visualizzare l'anteprima del codice quando si sposta il cursore verso l'alto e verso il basso nella barra di scorrimento. Per ulteriori informazioni, vedere [Procedura: tenere traccia del codice personalizzando la barra](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)di scorrimento .

## <a name="codelens-information"></a>Informazioni CodeLens

È possibile trovare informazioni relative a codice specifico, ad esempio modifiche, autori delle modifiche, riferimenti, bug, elementi di lavoro, revisioni del codice e stato dello unit test quando si usa CodeLens nell'editor del codice. CodeLens funziona come una visualizzazione preliminare quando si usa Visual Studio Enterprise con Team Foundation Server. Vedere [Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Vedere anche

- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
- [Visualizzare la gerarchia di chiamata](../ide/reference/call-hierarchy.md)
