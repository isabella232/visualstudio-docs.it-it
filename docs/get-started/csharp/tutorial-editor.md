---
title: 'Esercitazione: Modifica per sviluppatori C#'
description: In questa introduzione all'editor di codice di Visual Studio della durata di 10 minuti viene illustrato in che modo Visual Studio semplifica la scrittura, la navigazione e la comprensione del codice C#.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c75a5e83ebdabd814e37f601979e0e8b5e808cec
ms.sourcegitcommit: f07b737f43a29e30d040cc5793437f462fedb595
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2021
ms.locfileid: "127964847"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>Informazioni sull'uso dell'editor di codice con C\#

In questa introduzione di 10 minuti all'editor di codice in Visual Studio verrà aggiunto codice a un file per esaminare alcuni dei modi in cui Visual Studio semplifica la scrittura, lo spostamento e la comprensione del codice C#.

::: moniker range="vs-2017"

> [!TIP]
> Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

Questa articolo presuppone una certa familiarità con C#. Se non si possiede questa familiarità, è consigliabile seguire prima un'esercitazione, ad esempio [Introduzione a C# e ad ASP.NET Core in Visual Studio](tutorial-aspnet-core.md).

> [!TIP]
> Per poter seguire questo articolo, assicurarsi che le impostazioni di C# siano selezionate per Visual Studio. Per informazioni sulla selezione delle impostazioni per l'ambiente di sviluppo integrato (IDE), vedere [Select environment settings](visual-studio-ide.md#select-environment-settings) (Selezionare le impostazioni di ambiente).

## <a name="create-a-new-code-file"></a>Creare un nuovo file di codice

Per iniziare si crea un nuovo file e si aggiunge codice al file.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

1. Scegliere **Nuovo file** dal menu  File sulla barra dei menu oppure > premere **CTRL** + **N.**

1. Nella finestra di dialogo **Nuovo file**, nella categoria **Generale**, scegliere **Classe di Visual C#** e quindi scegliere **Apri**.

   Nell'editor viene aperto un nuovo file con lo scheletro di una classe C#. Si noti che non è necessario creare un progetto di Visual Studio completo per ottenere alcuni dei vantaggi che offre l'editor di codice. È sufficiente un file di codice.

   ![Screenshot di un file di codice C# in Visual Studio.](../media/tutorial-editor.png)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio. Premere **ESC o** fare clic su Continua senza **codice** nella finestra iniziale per aprire l'ambiente di sviluppo.

1. Scegliere **Nuovo file** dal menu  File sulla barra dei menu oppure > premere **CTRL** + **N.**

1. Nella finestra di dialogo **Nuovo file**, nella categoria **Generale**, scegliere **Classe di Visual C#** e quindi scegliere **Apri**.

   Nell'editor viene aperto un nuovo file con lo scheletro di una classe C#. Si noti che non è necessario creare un progetto di Visual Studio completo per ottenere alcuni dei vantaggi che offre l'editor di codice. È sufficiente un file di codice.

   ![Screenshot di un file di codice C# in Visual Studio.](../media/tutorial-editor.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio. Premere **ESC** o scegliere **Continua senza codice** nella finestra iniziale per aprire l'ambiente di sviluppo.

1. Scegliere **Nuovo file** dal menu  File sulla barra dei menu oppure > premere **CTRL** + **N.**

1. Nella finestra di dialogo **Nuovo file**, nella categoria **Generale**, scegliere **Classe di Visual C#** e quindi scegliere **Apri**.

   Nell'editor viene aperto un nuovo file con lo scheletro di una classe C#. Non è necessario creare un progetto Visual Studio completo per ottenere alcuni dei vantaggi offerti dall'editor di codice è un &mdash; file di codice.

   :::image type="content" source="media/vs-2022/tutorial-editor.png" alt-text="Screenshot di un file di codice C# in Visual Studio 2022.":::

::: moniker-end

## <a name="use-code-snippets"></a>Usare frammenti di codice

Visual Studio offre *frammenti di codice* utili che è possibile usare per generare in modo semplice e rapido blocchi di codice di uso comune. [I frammenti di codice](../../ide/code-snippets.md) sono disponibili per vari linguaggi di programmazione, tra cui C#, Visual Basic e C++.

Ora si aggiunge il frammento C# `void Main` al file.

::: moniker range="<=vs-2019"

1. Posizionare il cursore appena sopra la parentesi graffa di chiusura **finale }** nel file e digitare i caratteri (che sta per non preoccuparsi troppo se non si sa cosa `svm` `static void Main` &mdash; significa).

   Verrà visualizzata una finestra di dialogo a comparsa con le informazioni sul frammento di codice `svm`.

   ![Screenshot di un popup IntelliSense per un frammento di codice in Visual Studio.](../media/tutorial-intellisense-snippet.png)

1. Premere due volte **TAB** per inserire il frammento di codice.

   La firma del metodo `static void Main()` viene aggiunta al file. Il metodo [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) è il punto di ingresso per le applicazioni C#.

I frammenti di codice disponibili variano a seconda del linguaggio di programmazione. È possibile esaminare i frammenti di codice disponibili per il linguaggio scegliendo Modifica frammento di codice  >  **IntelliSense** o premendo  >   **CTRL** + **K,** **CTRL** X e quindi scegliendo la cartella + del linguaggio. Per C# l'elenco ha l'aspetto seguente:

![Screenshot di un popup IntelliSense per un elenco di frammenti di codice C#.](../media/tutorial-code-snippet-list.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Posizionare il cursore appena sopra la parentesi graffa di **`}`** chiusura finale nel file e digitare i caratteri `svm` . `svm`è `static void Main` &mdash; l'acronimo di don't worry if you don't know what that means yet.

   Verrà visualizzata una finestra di dialogo a comparsa con le informazioni sul frammento di codice `svm`.

   :::image type="content" source="media/vs-2022/tutorial-intellisense-snippet.png" alt-text="Screenshot di un popup IntelliSense per un frammento di codice in Visual Studio 2022.":::

1. Premere due volte **TAB** per inserire il frammento di codice.

   Verrà aggiunta la `static void Main()` firma del metodo al file. Il metodo [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) è il punto di ingresso per le applicazioni C#.

I frammenti di codice disponibili variano per linguaggi di programmazione diversi. È possibile esaminare i frammenti di codice disponibili per il linguaggio scegliendo Modifica frammento di codice  >  **IntelliSense** Inserisci frammento di codice o premendo CTRL K , CTRL X e quindi scegliendo la cartella per il  >    +   + linguaggio di programmazione. Per C#, l'elenco di frammenti di codice è simile al seguente:

:::image type="content" source="media/vs-2022/tutorial-code-snippet-list.png" alt-text="Screenshot di un popup IntelliSense per un elenco di frammenti di codice C#.":::

::: moniker-end

L'elenco include frammenti per la creazione di una [classe](/dotnet/csharp/fundamentals/types/classes), un [costruttore](/dotnet/csharp/programming-guide/classes-and-structs/constructors), un ciclo [for](/dotnet/csharp/language-reference/statements/iteration-statements#the-for-statement), un'istruzione [if](/dotnet/csharp/language-reference/statements/selection-statements#the-if-statement) o [switch](/dotnet/csharp/language-reference/statements/selection-statements#the-switch-statement) e altro ancora.

## <a name="comment-out-code"></a>Codice di impostazione come commento

::: moniker range="<=vs-2019"

La barra degli strumenti, ovvero la riga di pulsanti sotto la barra dei menu di Visual Studio, contribuisce ad aumentare la produttività in fase di creazione del codice. Ad esempio, è possibile attivare o disattivare la modalità di completamento IntelliSense ([IntelliSense](../../ide/using-intellisense.md) è un ausilio per la scrittura del codice che visualizza un elenco di metodi corrispondenti, tra le altre cose), aumentare o ridurre un rientro di riga o impostare come commento il codice che non si vuole compilare. In questa sezione, una porzione del codice verrà impostata come commento.

![Screenshot della barra degli strumenti dell'editor in Visual Studio.](../media/tutorial-editor-toolbar.png)

1. Incollare il codice seguente nel corpo del metodo `Main()`.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. In questa fase non si usa la variabile `morewords` ma, poiché potrebbe risultare utile in seguito, non la si elimina. Invece si impostano le linee corrispondenti come commento. Selezionare l'intera definizione di per il punto e virgola di chiusura e quindi scegliere il pulsante Impostare come commento le righe `morewords` selezionate sulla barra degli strumenti.  Se si preferisce usare la tastiera, premere **CTRL** + **K**, **CTRL** + **C**.

   ![Screenshot del pulsante Commenta nella barra degli strumenti dell'editor in Visual Studio.](../media/tutorial-comment-out.png)

   I caratteri del commento di C# `//` vengono aggiunti all'inizio di ogni linea selezionata per impostare la linea come codice.

::: moniker-end

::: moniker range=">=vs-2022"

La barra degli strumenti, ovvero la riga di pulsanti sotto la barra dei menu in Visual Studio, consente di migliorare la produttività durante il codice. Ad esempio, è possibile attivare o disattivare la modalità di [completamento IntelliSense,](../../ide/using-intellisense.md) aumentare o ridurre un rientro di riga o impostare come commento il codice che non si vuole compilare.

:::image type="content" source="media/vs-2022/tutorial-editor-toolbar.png" alt-text="Screenshot della barra degli strumenti dell'editor di testo Visual Studio 2022.":::

Aggiungere il codice come commento.

1. Incollare il codice seguente nel corpo del metodo `Main()`.

    ```csharp
    // someWords is a string array.
    string[] someWords = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] moreWords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    // Alphabetically sort the words.
    IEnumerable<string> query = from word in someWords
                                orderby word
                                select word;
    ```

1. Non si usa la variabile, ma è possibile usarla in un secondo momento, quindi non `moreWords` è consigliabile eliminarla. Queste righe verranno invece commentate. Selezionare l'intera definizione di fino al punto e virgola di chiusura e quindi scegliere il pulsante Impostare come commento le righe `moreWords` selezionate sulla barra degli strumenti.  Se si preferisce usare la tastiera, premere **CTRL** + **E**, **CTRL** + **C**.

   :::image type="content" source="media/vs-2022/tutorial-comment-out.png" alt-text="Screenshot del pulsante Commenta nella barra degli strumenti dell'editor di testo in Visual Studio 2022.":::

   I caratteri del commento di C# `//` vengono aggiunti all'inizio di ogni linea selezionata per impostare la linea come codice.

::: moniker-end

## <a name="collapse-code-blocks"></a>Comprimere i blocchi di codice

Non si vuole visualizzare il [](/dotnet/csharp/programming-guide/classes-and-structs/constructors) costruttore vuoto generato per , quindi per annullare la visualizzazione del `Class1` codice, è possibile comprimerlo. Scegliere la piccola casella grigia contenente il segno meno sul margine della prima riga del costruttore. In caso contrario, se si preferisce usare la tastiera, posizionare il cursore in un punto qualsiasi del codice del costruttore e premere **CTRL** + **M**, **CTRL** + **M**.

::: moniker range="<=vs-2019"

![Screenshot del pulsante Comprimi struttura nella barra degli strumenti dell'editor di testo Visual Studio.](../media/tutorial-collapse.png)

Il blocco di codice viene compresso e visualizza solo la prima riga seguita dai puntini di sospensione (`...`). Per espandere di nuovo il blocco di codice, fare clic sulla stessa casella grigia in cui è ora presente un segno più oppure premere **di** nuovo CTRL + **M**, **CTRL** + **M.** Questa funzionalità è [denominata Struttura ed](../../ide/outlining.md) è particolarmente utile quando si comprendono metodi lunghi o intere classi.

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/tutorial-collapse.png" alt-text="Screenshot del pulsante Comprimi struttura nella barra degli strumenti dell'editor di testo Visual Studio 2022.":::

Il blocco di codice viene compresso e visualizza solo la prima riga seguita dai puntini di sospensione (`...`). Per espandere di nuovo il blocco di codice, selezionare la stessa casella grigia in cui è ora presente un segno più oppure premere **di** nuovo CTRL + **M**, **CTRL** + **M.** Questa funzionalità è [denominata Struttura ed](../../ide/outlining.md) è particolarmente utile quando si comprendono metodi lunghi o intere classi.

::: moniker-end

## <a name="view-symbol-definitions"></a>Visualizzare le definizioni dei simboli

::: moniker range="<=vs-2019"

L Visual Studio editor semplifica l'ispezione della definizione di un tipo, di un metodo e così via. Un modo è passare al file che contiene la definizione, ad esempio scegliendo **Vai** a definizione o premendo **F12** in qualsiasi punto in cui viene fatto riferimento al simbolo. Un metodo ancora più veloce che non sposta lo stato attivo dal file in uso è rappresentato da [Visualizza definizione](../../ide/go-to-and-peek-definition.md#peek-definition). Di seguito si procede a visualizzare la definizione del tipo `string`.

1. Fare clic con il pulsante destro del mouse su una qualsiasi ricorrenza di `string` e scegliere **Visualizza definizione** dal menu del contenuto. In caso contrario, **premere ALT** + **F12.**

   Viene visualizzata una finestra popup con la definizione della classe `String`. È possibile scorrere all'interno della finestra popup o anche esaminare la definizione di un altro tipo dal codice visualizzato.

   ![Screenshot di una finestra Visualizza definizione in Visual Studio.](../media/tutorial-peek-definition.png)

1. Chiudere la finestra di visualizzazione della definizione scegliendo la piccola casella contenente una "x" nell'angolo in alto a destra della finestra popup.

::: moniker-end

::: moniker range=">=vs-2022"

L Visual Studio editor semplifica l'ispezione della definizione di un tipo, di un metodo o di una variabile. Un modo è passare alla definizione, in qualsiasi file, scegliendo **Vai** a definizione o premendo **F12** ovunque si fa riferimento a un simbolo. Un modo ancora più rapido per non spostare lo stato attivo dal codice su cui si sta lavorando è usare [Visualizza definizione](../../ide/go-to-and-peek-definition.md#peek-definition).

Di seguito si procede a visualizzare la definizione del tipo `string`.

1. Fare clic con il pulsante destro del mouse su una qualsiasi ricorrenza di `string` e scegliere **Visualizza definizione** dal menu del contenuto. In caso contrario, **premere ALT** + **F12.**

   Viene visualizzata una finestra popup con la definizione della classe `String`. È possibile scorrere all'interno della finestra popup o anche esaminare la definizione di un altro tipo dal codice visualizzato.

   :::image type="content" source="media/vs-2022/tutorial-peek-definition.png" alt-text="Screenshot della finestra Visualizza definizione in Visual Studio 2022.":::

1. Chiudere la finestra di visualizzazione della definizione scegliendo la piccola casella con una "x" in alto a destra nella finestra popup.

::: moniker-end

## <a name="use-intellisense-to-complete-words"></a>Usare IntelliSense per il completamento di parole

::: moniker range="<=vs-2019"

[IntelliSense](../../ide/using-intellisense.md) è una risorsa di valore inestimabile durante la scrittura del codice. Consente di visualizzare informazioni sui membri disponibili di un tipo o sui dettagli parametro per diversi overload di un metodo. È anche possibile usare IntelliSense per completare una parola dopo aver digitato un numero di caratteri sufficiente a evitare ambiguità. Aggiungere una riga di codice per stampare le stringhe ordinate nella finestra della console, ovvero la posizione standard in cui finisce l'output del programma.

1. Sotto la variabile `query` iniziare a digitare il codice seguente:

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense visualizza **informazioni rapide** sul simbolo `query`.

   ![Screenshot di un popup di completamento delle parole intelliSense in Visual Studio.](../media/tutorial-intellisense-completion-list.png)

1. Per inserire il resto della parola `query` mediante la funzionalità di completamento della parola di IntelliSense premere **TAB**.

1. Completare il blocco di codice in modo che abbia un aspetto simile al codice seguente. È anche possibile esercitarsi ulteriormente nell'uso di frammenti di codice immettendo `cw` e quindi premendo **TAB** due volte per generare il codice `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

::: moniker-end

::: moniker range=">=vs-2022"

[IntelliSense](../../ide/using-intellisense.md) è una risorsa di valore inestimabile durante la scrittura del codice. Consente di visualizzare informazioni sui membri disponibili di un tipo o sui dettagli parametro per diversi overload di un metodo. È anche possibile usare IntelliSense per completare una parola dopo aver digitato un numero di caratteri sufficiente a evitare ambiguità.

Aggiungere una riga di codice per stampare le stringhe ordinate nella finestra della console, ovvero la posizione standard in cui finisce l'output del programma.

1. Sotto la variabile `query` iniziare a digitare il codice seguente:

   ```csharp
   foreach (string str in qu
   ```

   Verrà visualizzato un popup IntelliSense con informazioni sul `query` simbolo.

   :::image type="content" source="media/vs-2022/tutorial-intellisense-completion-list.png" alt-text="Screenshot di un popup di completamento delle parole IntelliSense in Visual Studio 2022.":::

1. Per inserire il resto della parola usando il completamento della parola `query` IntelliSense, premere **TAB.**

1. Completare il blocco di codice in modo che abbia un aspetto simile al codice seguente. È possibile esercitarsi ulteriormente con i frammenti di codice immettendo e quindi premendo `cw` **TAB** due volte per generare l'istruzione `Console.WriteLine` .

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

::: moniker-end

## <a name="refactor-a-name"></a>Effettuare il refactoring di un nome

::: moniker range="<=vs-2019"

Quando si inizia a creare codice è facile commettere errori e quindi dover modificare il nome di una variabile o di un metodo. Ora si userà la funzionalità [refactoring](../../ide/refactoring-in-visual-studio.md) di Visual Studio per rinominare la variabile `_words` come `words`.

1. Posizionare il cursore sulla definizione della variabile e scegliere Rinomina dal menu di scelta rapida o dal menu di scelta rapida `_words` oppure premere **CTRL**  + **R**, **CTRL** + **R**.

   Nella parte superiore destra dell'editor viene visualizzata la finestra di dialogo popup **Rinomina**.

1. Immettere le **parole** del nome desiderato. Si noti che anche il riferimento a `words` nella query viene rinominato automaticamente. Prima di premere **INVIO** selezionare la casella di controllo **Includi commenti** nella finestra popup **Rinomina**.

   ![Screenshot di una finestra di dialogo Rinomina in Visual Studio.](../media/tutorial-rename.png)

1. Premere **INVIO**.

   Entrambe le ricorrenze di `words` sono state rinominate, e così anche il riferimento a `words` nel commento del codice.

::: moniker-end

::: moniker range=">=vs-2022"

Quando si inizia a creare codice è facile commettere errori e quindi dover modificare il nome di una variabile o di un metodo. Ora si userà la funzionalità [refactoring](../../ide/refactoring-in-visual-studio.md) di Visual Studio per rinominare la variabile `someWords` come `unsortedWords`.

1. Posizionare il cursore sulla definizione della variabile e scegliere Rinomina dal menu di scelta rapida o dal menu di scelta rapida `someWords` oppure premere **F2.** 

   Viene **visualizzata una** finestra di dialogo Rinomina in alto a destra nell'editor.

   :::image type="content" source="media/vs-2022/tutorial-rename-start.png" alt-text="Screenshot della finestra popup Rinomina all'interno dell'editor di Visual Studio 2022.":::

1. Immettere il nome **desiderato unsortedWords**. Si noti che anche il riferimento a `unsortedWords` nell'istruzione di assegnazione `query` viene rinominato automaticamente. Prima di premere **INVIO** selezionare la casella di controllo **Includi commenti** nella finestra popup **Rinomina**.

   :::image type="content" source="media/vs-2022/tutorial-rename.png" alt-text="Screenshot della finestra popup Rinomina in Visual Studio 2022.":::

1. Premere **INVIO** o scegliere **Applica nella** finestra di **dialogo** Rinomina.

   Entrambe le `someWords` occorrenze di nel codice sono state rinominate, nonché il testo `someWords` nel commento del codice.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Informazioni su progetti e soluzioni](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedi anche

- [Frammenti di codice](../../ide/code-snippets.md)
- [Spostarsi all'interno del codice](../../ide/navigating-code.md)
- [struttura](../../ide/outlining.md)
- [Vai a definizione e Visualizza definizione](../../ide/go-to-and-peek-definition.md)
- [Refactoring](../../ide/refactoring-in-visual-studio.md)
- [Usare IntelliSense](../../ide/using-intellisense.md)
