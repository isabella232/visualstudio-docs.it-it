---
title: Introduzione alla modifica
ms.date: 11/30/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 9e2f451ecfb73e0c1ac69da4e48f3d2c8033aa51
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027802"
---
# <a name="learn-to-use-the-code-editor"></a>Informazioni su come usare l'editor del codice

In questa introduzione all'editor di codice di Visual Studio della durata di 10 minuti si aggiunge codice a un file per vedere in che modo Visual Studio semplifica la scrittura, la navigazione e la comprensione del codice.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

Questa articolo presuppone una certa familiarità con un linguaggio di programmazione. In caso contrario, è consigliabile leggere prima di tutto una delle guide introduttive alla programmazione, ad esempio su come creare un'app Web con [Python](../ide/quickstart-python.md) o [C#](../ide/tutorial-csharp-aspnet-core.md) oppure come creare un'app console con [Visual Basic](../ide/quickstart-visual-basic-console.md) o [C++](../ide/getting-started-with-cpp-in-visual-studio.md).

## <a name="create-a-new-code-file"></a>Creare un nuovo file di codice

Per iniziare si crea un nuovo file e si aggiunge codice al file.

1. Aprire Visual Studio, quindi nel menu **File** sulla barra dei menu scegliere **Nuovo** > **File**.

1. Nella finestra di dialogo **Nuovo file**, nella categoria **Generale**, scegliere **Classe di Visual C#** e quindi scegliere **Apri**.

   Nell'editor viene aperto un nuovo file con lo scheletro di una classe C#. Si noti che non è necessario creare un progetto di Visual Studio completo per ottenere alcuni dei vantaggi che offre l'editor di codice. È sufficiente un file di codice.

   ![File di codice C# in Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Usare frammenti di codice

Visual Studio offre *frammenti di codice* utili che è possibile usare per generare in modo semplice e rapido blocchi di codice di uso comune. [I frammenti di codice](../ide/code-snippets.md) sono disponibili per vari linguaggi di programmazione, tra cui C#, Visual Basic e C++. Ora si aggiunge il frammento C# `void Main` al file.

1. Posizionare il cursore appena sopra l'ultima parentesi graffa di chiusura **}** del file e digitare i caratteri `svm`, un acronimo per `static void Main`&mdash;non importa se non se ne capisce il significato.

   Verrà visualizzata una finestra di dialogo a comparsa con le informazioni sul frammento di codice `svm`.

   ![IntelliSense per il frammento di codice in Visual Studio](media/tutorial-intellisense-snippet.png)

1. Premere due volte **TAB** per inserire il frammento di codice.

   La firma del metodo `static void Main()` viene aggiunta al file. Il metodo [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) è il punto di ingresso per le applicazioni C#.

I frammenti di codice disponibili variano a seconda del linguaggio di programmazione. Per vedere i frammenti di codice disponibili per il proprio linguaggio scegliere **Modifica** > **IntelliSense** > **Inserisci frammento** e quindi scegliere la cartella del linguaggio. Per C# l'elenco ha l'aspetto seguente:

![Elenco di frammenti di codice per C#](media/tutorial-code-snippet-list.png)

L'elenco include frammenti per la creazione di una [classe](/dotnet/csharp/programming-guide/classes-and-structs/classes), un [costruttore](/dotnet/csharp/programming-guide/classes-and-structs/constructors), un ciclo [for](/dotnet/csharp/language-reference/keywords/for), un'istruzione [if](/dotnet/csharp/language-reference/keywords/if-else) o [switch](/dotnet/csharp/language-reference/keywords/switch) e altro ancora.

## <a name="comment-out-code"></a>Codice di impostazione come commento

La barra degli strumenti, ovvero la riga di pulsanti sotto la barra dei menu di Visual Studio, contribuisce ad aumentare la produttività in fase di creazione del codice. Ad esempio, è possibile attivare o disattivare la modalità di completamento IntelliSense ([IntelliSense](../ide/using-intellisense.md) è un ausilio per la scrittura del codice che visualizza un elenco di metodi corrispondenti, tra le altre cose), aumentare o ridurre un rientro di riga o impostare come commento il codice che non si vuole compilare. In questa sezione, una porzione del codice verrà impostata come commento.

![Barra degli strumenti editor](media/tutorial-editor-toolbar.png)

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

1. In questa fase non si usa la variabile `morewords` ma, poiché potrebbe risultare utile in seguito, non la si elimina. Invece si impostano le linee corrispondenti come commento. Selezionare l'intera definizione di `morewords` fino al punto e virgola finale, quindi scegliere il pulsante **Imposta le righe selezionate come commento** sulla barra degli strumenti. Se si preferisce usare la tastiera, premere **Ctrl**+**K**, **Ctrl**+**C**.

   ![Pulsante di impostazione come commento](media/tutorial-comment-out.png)

   I caratteri del commento di C# `//` vengono aggiunti all'inizio di ogni linea selezionata per impostare la linea come codice.

## <a name="collapse-code-blocks"></a>Comprimere i blocchi di codice

Non è necessario visualizzare il [costruttore](/dotnet/csharp/programming-guide/classes-and-structs/constructors) vuoto per `Class1` che è stato generato, pertanto per semplificare la visualizzazione del codice si procederà a comprimere il costruttore. Scegliere la piccola casella grigia contenente il segno meno sul margine della prima riga del costruttore. Oppure, con la tastiera posizionare il cursore in qualsiasi punto del codice del costruttore e premere **CTRL**+**M**, **CTRL**+**M**.

![Pulsante di compressione evidenziato](media/tutorial-collapse.png)

Il blocco di codice viene compresso e visualizza solo la prima riga seguita dai puntini di sospensione (`...`). Per espandere di nuovo il blocco di codice fare clic sulla stessa casella grigia, che ora contiene un segno più, oppure premere di nuovo **CTRL**+**M**, **CTRL**+**M**. Questa funzionalità è detta [Gestione della struttura](../ide/outlining.md) ed è particolarmente utile per comprimere metodi con molto codice o intere classi.

## <a name="view-symbol-definitions"></a>Visualizzare le definizioni dei simboli

L'editor di Visual Studio semplifica l'ispezione della definizione di un tipo, un metodo e così via. Ad esempio è possibile navigare al file contenente la definizione scegliendo **Vai alla definizione** in qualsiasi punto in cui esiste un riferimento al simbolo. Un metodo ancora più veloce che non sposta lo stato attivo dal file in uso è rappresentato da [Visualizza definizione](../ide/go-to-and-peek-definition.md#peek-definition). Di seguito si procede a visualizzare la definizione del tipo `string`.

1. Fare clic con il pulsante destro del mouse su una qualsiasi ricorrenza di `string` e scegliere **Visualizza definizione** dal menu del contenuto. In alternativa, premere **Alt**+**F12**.

   Viene visualizzata una finestra popup con la definizione della classe `String`. È possibile scorrere all'interno della finestra popup o anche esaminare la definizione di un altro tipo dal codice visualizzato.

   ![Finestra Visualizza definizione](media/tutorial-peek-definition.png)

1. Chiudere la finestra di visualizzazione della definizione scegliendo la piccola casella contenente una "x" nell'angolo in alto a destra della finestra popup.

## <a name="use-intellisense-to-complete-words"></a>Usare IntelliSense per il completamento di parole

[IntelliSense](../ide/using-intellisense.md) è una risorsa molto importante per la creazione di codice. Consente di visualizzare informazioni sui membri disponibili di un tipo o sui dettagli parametro per diversi overload di un metodo. È anche possibile usare IntelliSense per completare una parola dopo aver digitato un numero di caratteri sufficiente a evitare ambiguità. Aggiungere una riga di codice per stampare le stringhe ordinate nella finestra della console, ovvero la posizione standard in cui finisce l'output del programma.

1. Sotto la variabile `query` iniziare a digitare il codice seguente:

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense visualizza **informazioni rapide** sul simbolo `query`.

   ![Completamento delle parole IntelliSense in Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Per inserire il resto della parola `query` mediante la funzionalità di completamento della parola di IntelliSense premere **TAB**.

1. Completare il blocco di codice in modo che abbia un aspetto simile al codice seguente. È anche possibile esercitarsi ulteriormente nell'uso di frammenti di codice immettendo `cw` e quindi premendo **TAB** due volte per generare il codice `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Effettuare il refactoring di un nome

Quando si inizia a creare codice è facile commettere errori e quindi dover modificare il nome di una variabile o di un metodo. Ora si userà la funzionalità [refactoring](../ide/refactoring-in-visual-studio.md) di Visual Studio per rinominare la variabile `_words` come `words`.

1. Posizionare il cursore sulla definizione della variabile `_words`, quindi scegliere **Rinomina** dal menu di scelta rapida o dal menu a comparsa oppure premere **CTRL**+**R**, **CTRL**+**R**.

   Nella parte superiore destra dell'editor viene visualizzata la finestra di dialogo popup **Rinomina**.

1. Immettere le **parole** del nome desiderato. Si noti che anche il riferimento a `words` nella query viene rinominato automaticamente. Prima di premere **INVIO** selezionare la casella di controllo **Includi commenti** nella finestra popup **Rinomina**.

   ![Rinomina (finestra di dialogo)](media/tutorial-rename.png)

1. Premere **INVIO**.

   Entrambe le ricorrenze di `words` sono state rinominate, e così anche il riferimento a `words` nel commento del codice.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Guida introduttiva: progetti e soluzioni](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedere anche

- [Frammenti di codice](../ide/code-snippets.md)
- [Spostarsi all'interno del codice](../ide/navigating-code.md)
- [Struttura](../ide/outlining.md)
- [Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Usare IntelliSense](../ide/using-intellisense.md)
