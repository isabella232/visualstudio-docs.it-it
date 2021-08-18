---
title: Cercare e sostituire testo e selezione di più punti di inserimento
description: Informazioni sulla funzionalità Trova e sostituisci e su come usarla per trovare e sostituire istanze di un criterio.
ms.custom: SEO-VS-2020
ms.date: 10/17/2020
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f12d801fc54088c79d22a3c69cd27206a8b667e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048986"
---
# <a name="find-and-replace-text"></a>Cercare e sostituire testo

È possibile trovare e sostituire testo nell'editor di Visual Studio usando [Trova e sostituisci](#find-and-replace-control) (**CTRL**+**F** o **CTRL**+**H**) oppure [Find/Replace in Files](#find-in-files-and-replace-in-files) (Trova/Sostituisci nei file) (**CTRL**+**MAIUSC**+**F** o **CTRL**+**MAIUSC**+**H**). È anche possibile cercare e sostituire solo *alcune* istanze di un modello usando la *[selezione di più punti di inserimento](#multi-caret-selection)*.

> [!TIP]
> Se si stanno rinominando simboli del codice, ad esempio variabili e i metodi, è preferibile *[effettuarne il refactoring](../ide/reference/rename.md)* anziché usare la funzionalità di ricerca e sostituzione. Il refactoring è un'opzione avanzata in grado di rilevare l'ambito, mentre con la ricerca e sostituzione vengono sostituite indifferentemente tutte le istanze.

La funzionalità di ricerca e sostituzione è disponibile nell'editor, in alcune altre finestre basate su testo, ad esempio le finestre dei **risultati della ricerca**, nelle finestre di progettazione, ad esempio la finestra di progettazione XAML e quella di Progettazione Windows Form, e nelle finestre degli strumenti.

È possibile definire l'ambito di ricerca per il documento corrente, la soluzione corrente o un set di cartelle personalizzato. È inoltre possibile specificare un set di estensioni di nomi di file per le ricerche su più file. Personalizzare la sintassi di ricerca usando le [espressioni regolari](../ide/using-regular-expressions-in-visual-studio.md) .NET.

> [!TIP]
> La casella [Trova/Comando](../ide/find-command-box.md) è disponibile nella barra degli strumenti, ma non è visibile per impostazione predefinita. Per visualizzare la casella **Trova/Comando**, selezionare **Aggiungi o rimuovi pulsanti** nella barra degli strumenti **Standard** e quindi selezionare **Trova**.

## <a name="find-and-replace-control"></a>Controllo Trova e sostituisci

- Premere **CTRL** + **F** come collegamento per *trovare* una stringa nel file corrente.
- Premere **CTRL** + **H** come collegamento per *trovare e sostituire* una stringa nel file corrente.

Il controllo **Trova e sostituisci** viene visualizzato nell'angolo superiore destro della finestra dell'editor di codice. Evidenzia immediatamente tutte le occorrenze della stringa di ricerca specificata nel documento corrente. È possibile spostarsi da un'occorrenza all'altra scegliendo il pulsante **Trova successivo** o **Trova precedente** nel controllo di ricerca.

![Trova e sostituisci in Visual Studio](media/find-and-replace-box.png)

È possibile accedere alle opzioni di sostituzione scegliendo il pulsante accanto alla casella di testo **Trova**. Per eseguire una sostituzione per volta, scegliere il pulsante **Sostituisci successivo** accanto alla casella di testo **Sostituisci** . Per sostituire tutte le corrispondenze, scegliere **il pulsante Sostituisci** tutto.

Per modificare il colore di evidenziazione per le corrispondenze, scegliere il menu **Strumenti**, selezionare **Opzioni**, quindi scegliere **Ambiente** e selezionare **Tipi di carattere e colori**. Nell'elenco **Show settings for** (Mostra impostazioni per), selezionare **Editor di testo**, quindi nell'elenco **Elementi visualizzati**, selezionare **Trova evidenziato (estensione)**.

### <a name="search-tool-windows"></a>Finestre degli strumenti di ricerca

È possibile usare il controllo **Trova** nelle finestre di codice o del testo, ad esempio le finestre **Output** e **Risultati ricerca**, selezionando **Modifica** > **Trova e sostituisci** o premendo **CTRL+F**.

Una versione del **controllo Trova** è disponibile anche in alcune finestre degli strumenti. Ad esempio, è possibile filtrare l'elenco di controlli nella finestra **Casella degli strumenti** immettendo il testo nella casella di ricerca. Tra le altre finestre degli strumenti che consentono di cercare il relativo contenuto sono incluse **Esplora soluzioni**, **Proprietà** e **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Cerca nei file e Sostituisci nei file

- Premere **CTRL** + **MAIUSC** + **F** come collegamento per *trovare* una stringa in più file.
- Premere **CTRL** + **MAIUSC** + **H come** collegamento per trovare e *sostituire* una stringa in più file.

**Find/Replace in Files** (Trova/Sostituisci nei file) funziona come il controllo **Trova e sostituisci**, con la differenza che è possibile definire un ambito per la ricerca. Non solo è possibile cercare il file aperto corrente nell'editor, ma anche tutti i documenti aperti, l'intera soluzione, il progetto corrente e gli insiemi di cartelle selezionati. È inoltre possibile eseguire la ricerca in base all'estensione del nome file. Per accedere alla finestra di dialogo **Find/Replace in Files** (Trova/Sostituisci nei file), selezionare **Trova e sostituisci** dal menu **Modifica** o premere **CTRL**+**MAIUSC**+**F**.

![Cerca in File di Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Risultati ricerca

Quando si sceglie **Find All** (Trova tutti), si apre una finestra **Risultati ricerca** che elenca le corrispondenze della ricerca. Selezionando un risultato nell'elenco viene visualizzato il file associato ed evidenziata la corrispondenza. Se il file non è già aperto per la modifica, viene aperto in una scheda di anteprima a destra della finestra scheda. È possibile utilizzare il controllo **Trova** per eseguire la ricerca nell'elenco dei **Risultati ricerca**.

### <a name="create-custom-search-folder-sets"></a>Creare set personalizzati di cartelle di ricerca

È possibile definire un ambito  di ricerca scegliendo il pulsante Scegli cartelle di ricerca (simile a **...**) accanto alla casella Cerca **in.** Nella finestra di dialogo **Seleziona cartelle di ricerca**, è possibile specificare un set di cartelle in cui eseguire la ricerca nonché salvare la specifica in modo da poterla usare di nuovo in un secondo tempo.

> [!TIP]
> Se è stato eseguito il mapping dell'unità di un computer remoto nel computer locale, è possibile specificare cartelle in cui eseguire la ricerca nel computer remoto.

### <a name="create-custom-component-sets"></a>Creare set di componenti personalizzati

È possibile definire set di componenti nell'ambito di ricerca scegliendo il pulsante **Modifica insieme di componenti personalizzato** accanto alla casella **Cerca in**. È possibile specificare i componenti .NET o COM installati, i progetti Visual Studio che sono inclusi nella soluzione, o qualunque assembly o libreria dei tipi (*.dll*, *.tlb*, *.olb*, *.exe* o *.ocx*). Per individuare i riferimenti, selezionare la casella **Cerca in riferimenti**.

## <a name="multi-caret-selection"></a>Selezione di più punti di inserimento

> [!NOTE]
> Questa sezione si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Selezione blocco](/visualstudio/mac/block-selection).

**Introdotta in Visual Studio 2017 versione 15.8**

Usare la *selezione di più punti di inserimento* per apportare la stessa modifica apportata in due o più posizioni nello stesso momento. Ad esempio, è possibile inserire lo stesso testo o modificare il testo esistente in più posizioni nello stesso momento.

Nello screenshot seguente `-0000` è selezionato in tre posizioni; se l'utente preme **Elimina**, vengono eliminate tutte e tre le selezioni:

![Selezione di più punti di inserimento in un file XML in Visual Studio](media/multi-caret-selection.png)

Per selezionare più punti di inserimento, fare clic o effettuare la prima selezione di testo come di consueto, quindi premere **ALT** mentre si fa clic o si seleziona il testo in ogni nuova posizione. È anche possibile aggiungere automaticamente il testo corrispondente come selezioni aggiuntive o selezionare una casella di testo per modificare in modo identico ogni riga.

> [!TIP]
> Se si è scelto **ALT** come tasto di modifica per il clic del mouse di Vai a definizione in **Strumenti** > **Opzioni**, la selezione per più punti di inserimento è disabilitata.

### <a name="commands"></a>Comandi

Usare i tasti e le azioni seguenti per i comportamenti di selezione di più punti di inserimento:

|Tasto di scelta rapida|Azione|
|-|-|
|**CTRL+FRECCIA DESTRA** + **ALT+** clic|Aggiungere un punto di inserimento secondario|
|**CTRL+FRECCIA DESTRA** + **ALT** + doppio clic|Aggiungere una selezione di parola secondaria|
|**CTRL+FRECCIA DESTRA** + **ALT** + clic + trascinamento|Aggiungere una selezione secondaria|
|**MAIUSC** + **ALT** + **.**|Aggiungere il testo successivo corrispondente come selezione|
|**MAIUSC** + **ALT** + **;**|Aggiungere tutto il testo corrispondente come selezione|
|**MAIUSC** + **ALT** + **,**|Rimuovere l'ultima occorrenza selezionata|
|**MAIUSC** + **ALT**+**/**|Ignorare l'occorrenza corrispondente successiva|
|**ALT+** clic|Aggiungere una selezione di casella|
|**ESC** oppure clic|Cancellare tutte le selezioni|

Alcuni comandi sono disponibili anche nel menu **Modifica**, in **Più punti di inserimento**:

:::image type="content" source="media/edit-menu-multiple-carets-find-replace.png" alt-text="Screenshot del menu a comparsa Più punti di selezione in Visual Studio":::

## <a name="see-also"></a>Vedi anche

- [Usare espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refactoring del codice in Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Selezione blocco (Visual Studio per Mac)](/visualstudio/mac/block-selection)
