---
title: Introduzione alla modifica del codice per gli sviluppatori Visual Basic
description: In questa introduzione all'editor del codice di Visual Studio della durata di 10 minuti viene illustrato in che modo Visual Studio semplifica la scrittura, la navigazione e la comprensione del codice Visual Basic.
ms.custom:
- vs-acquisition
- seodec18
- get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2a66cf69615640b8750f53dfd3d150708dbacb90f7c09ba43d78110ecd9e4a50
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121259708"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Informazioni sull'uso dell'editor di codice con Visual Basic

In questa introduzione di 10 minuti all'editor di codice in Visual Studio verrà aggiunto codice a un file per esaminare alcuni dei modi in cui Visual Studio semplifica la scrittura, lo spostamento e la comprensione del codice Visual Basic.

::: moniker range="vs-2017"

> [!TIP]
> Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Se non è già stato installato Visual Studio Preview, passare alla pagina di download di [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) per installarla gratuitamente.

::: moniker-end

Questa articolo presuppone una certa familiarità con Visual Basic. Se non si possiede questa familiarità, è consigliabile seguire prima un'esercitazione, ad esempio [Introduzione a Visual Basic in Visual Studio](../../get-started/visual-basic/tutorial-console.md).

> [!TIP]
> Per poter seguire questo articolo, assicurarsi che per Visual Studio siano selezionate le impostazioni di Visual Basic. Per informazioni sulla selezione delle impostazioni per l'ambiente di sviluppo integrato (IDE), vedere [Select environment settings](visual-studio-ide.md#select-environment-settings) (Selezionare le impostazioni di ambiente).

## <a name="create-a-new-code-file"></a>Creare un nuovo file di codice

Per iniziare si crea un nuovo file e si aggiunge codice al file.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio. Premere **ESC o** fare clic su Continua senza **codice** nella finestra iniziale per aprire l'ambiente di sviluppo.

::: moniker-end

2. Nel menu **File** sulla barra dei menu scegliere **Nuovo file**.

3. Nella finestra di dialogo **Nuovo file**, all'interno della categoria **Generale**, scegliere **Classe di Visual Basic** e quindi scegliere **Apri**.

   Nell'editor viene aperto un nuovo file con lo scheletro di una classe di Visual Basic. È già possibile notare che non è necessario creare un progetto di Visual Studio completo per ottenere alcuni dei vantaggi che offre l'editor di codice, come l'evidenziazione della sintassi. È sufficiente un file di codice.

   ![File di codice Visual Basic in Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Usare frammenti di codice

Visual Studio offre *frammenti di codice* utili che è possibile usare per generare in modo semplice e rapido blocchi di codice di uso comune. [I frammenti di codice](../../ide/code-snippets.md) sono disponibili per vari linguaggi di programmazione, tra cui Visual Basic, C# e C++. Ora si aggiungerà il frammento di codice **Sub** di Visual Basic al file.

1. Posizionare il cursore sopra la riga con la dicitura `End Class` e digitare **sub**.

   Verrà visualizzata una finestra di dialogo a comparsa con le informazioni sulla parola chiave `Sub` e come inserire il frammento di codice **Sub**.

   ![IntelliSense per il frammento di codice in Visual Studio](media/tutorial-intellisense-snippet.png)

1. Premere due volte **TAB** per inserire il frammento di codice.

   La struttura della routine Sub `MySub()` viene aggiunta al file.

I frammenti di codice disponibili variano a seconda del linguaggio di programmazione. È possibile esaminare i frammenti di codice disponibili per Visual Basic scegliendo Modifica frammento di codice IntelliSense Insert (Modifica frammento di codice  >  **IntelliSense)** o premendo  >   **CTRL** + **K**, **CTRL** + **X**). Per Visual Basic sono disponibili frammenti di codice per le categorie seguenti:

![Elenco dei frammenti di codice di Visual Basic](media/tutorial-code-snippet-list.png)

Sono disponibili frammenti di codice per determinare se esiste un file nel computer, per scrivere in un file di testo, per leggere un valore del Registro di sistema, per eseguire una query SQL, per creare un'[istruzione For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) e molto altro ancora.

## <a name="comment-out-code"></a>Codice di impostazione come commento

La barra degli strumenti, ovvero la riga di pulsanti sotto la barra dei menu di Visual Studio, contribuisce ad aumentare la produttività in fase di creazione del codice. È possibile, ad esempio, attivare o disattivare la modalità di terminazione IntelliSense, aumentare o ridurre un rientro riga o impostare come commento una parte del codice che non si desidera compilare. ([IntelliSense](../../ide/using-intellisense.md) è un supporto per la codifica che visualizza un elenco di metodi corrispondenti, tra le altre cose). In questa sezione verrà commentato il codice.

![Pulsanti della barra degli strumenti editor](media/tutorial-editor-toolbar.png)

1. Incollare il codice seguente nel corpo della procedura `MySub()`.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. In questa fase non si usa la matrice `morewords` ma, poiché potrebbe risultare utile in seguito, non la si elimina. Invece si impostano le linee corrispondenti come commento. Selezionare l'intera definizione di `morewords` fino alla parentesi graffa di chiusura, quindi scegliere il pulsante **Imposta le righe selezionate come commento** sulla barra degli strumenti. Se si preferisce usare la tastiera, premere **CTRL** + **K**, **CTRL** + **C**.

   ![Pulsante di impostazione come commento](media/tutorial-comment-out.png)

   Il carattere del commento di Visual Basic `'` viene aggiunto all'inizio di ogni riga selezionata per impostare la riga come commento.

## <a name="collapse-code-blocks"></a>Comprimere i blocchi di codice

È possibile comprimere sezioni di codice per concentrarsi solo sulle parti di particolare interesse per l'utente. Per fare pratica, si procederà a comprimere la matrice `_words` in una sola riga di codice. Scegliere la casellina grigia contenente il segno meno sul margine della riga con la dicitura `Dim _words = New String() {`. In caso contrario, se si è un utente della tastiera, posizionare il cursore in un punto qualsiasi della definizione della matrice e premere **CTRL** + **M**, **CTRL** + **M**.

![Pulsante di compressione evidenziato](media/tutorial-collapse.png)

Il blocco di codice viene compresso e visualizza solo la prima riga seguita dai puntini di sospensione (`...`). Per espandere di nuovo il blocco di codice, fare clic sulla stessa casella grigia in cui è ora presente un segno più oppure premere **di** nuovo CTRL + **M**, **CTRL** + **M.** Questa funzionalità è [denominata Struttura ed](../../ide/outlining.md) è particolarmente utile quando si comproendo metodi lunghi o intere classi.

## <a name="view-symbol-definitions"></a>Visualizzare le definizioni dei simboli

L Visual Studio editor semplifica l'ispezione della definizione di un tipo, di un metodo e così via. Un modo è passare al file che contiene la definizione, ad esempio scegliendo **Vai** a definizione in qualsiasi punto in cui viene fatto riferimento al simbolo. Un metodo ancora più veloce che non sposta lo stato attivo dal file in uso è rappresentato da [Visualizza definizione](../../ide/go-to-and-peek-definition.md#peek-definition). Di seguito si procede a visualizzare la definizione del tipo `String`.

1. Fare clic con il pulsante destro del mouse sulla parola `String` e scegliere **Visualizza definizione** dal menu del contenuto. In caso contrario, **premere ALT** + **F12.**

   Viene visualizzata una finestra popup con la definizione della classe `String`. È possibile scorrere all'interno della finestra popup o anche esaminare la definizione di un altro tipo dal codice visualizzato.

   ![Finestra Visualizza definizione](media/tutorial-peek-definition.png)

1. Chiudere la finestra di visualizzazione della definizione scegliendo la piccola casella contenente una "x" nell'angolo in alto a destra della finestra popup.

## <a name="use-intellisense-to-complete-words"></a>Usare IntelliSense per il completamento di parole

[IntelliSense](../../ide/using-intellisense.md) è una risorsa di valore inestimabile durante la scrittura del codice. Consente di visualizzare informazioni sui membri disponibili di un tipo o sui dettagli parametro per diversi overload di un metodo. È anche possibile usare IntelliSense per completare una parola dopo aver digitato un numero di caratteri sufficiente a evitare ambiguità. Aggiungere una riga di codice per stampare le stringhe ordinate nella finestra della console, ovvero la posizione standard in cui finisce l'output del programma.

1. Sotto la variabile `query` iniziare a digitare il codice seguente:

   ```vb
   For Each str In qu
   ```

   IntelliSense visualizza **informazioni rapide** sul simbolo `query`.

   ![Completamento delle parole IntelliSense in Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Per inserire il resto della parola `query` mediante la funzionalità di completamento della parola di IntelliSense premere **TAB**.

1. Completare il blocco di codice in modo che abbia un aspetto simile al codice seguente.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Effettuare il refactoring di un nome

Quando si inizia a creare codice è facile commettere errori e quindi dover modificare il nome di una variabile o di un metodo. Ora si userà la funzionalità [refactoring](../../ide/refactoring-in-visual-studio.md) di Visual Studio per rinominare la variabile `_words` come `words`.

1. Posizionare il cursore sulla definizione della variabile `_words`, quindi scegliere **Rinomina** dal menu di scelta rapida.

   Nella parte superiore destra dell'editor viene visualizzata la finestra di dialogo popup **Rinomina**.

1. Con la variabile `_words` ancora selezionata, digitare il nome desiderato di **words**. Si noti che anche il riferimento a `words` nella query viene rinominato automaticamente. Prima di premere **INVIO** o di fare clic su **Applica**, selezionare la casella di controllo **Includi commenti** nella finestra popup **Rinomina**.

   ![Rinomina (finestra di dialogo)](media/tutorial-rename.png)

1. Premere **INVIO** o fare clic su **Applica**.

   Entrambe le occorrenze di `words` sono rinominate e lo stesso vale per il riferimento a `words` nel commento del codice.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Informazioni su progetti e soluzioni](tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedi anche

- [Frammenti di codice](../../ide/code-snippets.md)
- [Spostarsi all'interno del codice](../../ide/navigating-code.md)
- [struttura](../../ide/outlining.md)
- [Vai a definizione e Visualizza definizione](../../ide/go-to-and-peek-definition.md)
- [Refactoring](../../ide/refactoring-in-visual-studio.md)
- [Usare IntelliSense](../../ide/using-intellisense.md)
