---
title: Introduzione alla modifica del codice per sviluppatori JavaScript
description: In questa introduzione all'editor di codice di Visual Studio viene illustrato in che modo Visual Studio semplifica la scrittura, la navigazione e la comprensione del codice JavaScript.
ms.date: 03/25/2021
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f84c9483da176a67d4636dd22a6cadee062e826eb82f06d561b6384aa17ad794
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231899"
---
# <a name="learn-to-use-the-code-editor-for-javascript"></a>Informazioni sull'uso dell'editor di codice per JavaScript

In questa breve introduzione all'editor di codice di Visual Studio viene illustrato in che modo Visual Studio semplifica la scrittura, la navigazione e la comprensione del codice.

> [!TIP]
> Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente. A seconda del tipo di sviluppo di app che si sta eseguendo, può essere necessario installare il **carico di lavoro Sviluppo Node.js** con Visual Studio. Per altre informazioni su come ottenere il servizio di linguaggio per TypeScript, vedere [Supporto di TypeScript](../javascript/javascript-in-vs-2019.md#typescript-support).

Questo articolo presuppone una certa familiarità con lo sviluppo di JavaScript. Se non è questo il caso, è consigliabile vedere prima l'esercitazione [Creare un progetto Node.js e un'app Express in Visual Studio](../javascript/tutorial-nodejs.md).

## <a name="add-a-new-project-file"></a>Aggiungere un nuovo file di progetto

È possibile usare l'IDE per aggiungere nuovi file al progetto.

1. Con il progetto aperto in Visual Studio, fare clic con il pulsante destro del mouse su una cartella o sul nodo del progetto in Esplora soluzioni (riquadro destro) e scegliere **Aggiungi**  >  **nuovo elemento**.

1. Nella finestra di dialogo **Nuovo file** nella categoria **Generale** scegliere il tipo di file che si vuole aggiungere, ad esempio **File JavaScript**, e scegliere **Apri**.

    Il nuovo file viene aggiunto al progetto e viene aperto nell'editor.

## <a name="use-intellisense-to-complete-words"></a>Usare IntelliSense per il completamento di parole

IntelliSense è una risorsa molto importante per la creazione di codice. Consente di visualizzare informazioni sui membri disponibili di un tipo o sui dettagli parametro per diversi overload di un metodo. Nel codice seguente quando si digita `Router()`, vengono visualizzati i tipi di argomento che si possono passare. Questo si chiama firma di chiamata.

![Screenshot di una finestra Visual Studio codice con codice JavaScript immesso. Le informazioni di IntelliSense vengono visualizzate per la funzione Router().](../javascript/media/write-code-signature-checking.png)

È anche possibile usare IntelliSense per completare una parola dopo aver digitato un numero di caratteri sufficiente a evitare ambiguità. Se si posiziona il cursore dopo la stringa `data` nel codice seguente e si digita `get`, IntelliSense visualizza le funzioni definite in precedenza nel codice o definite in una libreria di terze parti che è stata aggiunta al progetto.

![Screenshot di una Visual Studio codice con la parola "get" immessa. Le informazioni di IntelliSense vengono visualizzate per tutte le funzioni che iniziano con 'get'.](../javascript/media/write-code-intellisense.png)

IntelliSense può visualizzare anche informazioni sui tipi quando si passa il mouse sugli elementi di programmazione.

Per specificare informazioni di IntelliSense, il servizio di linguaggio può usare i file TypeScript *d.ts* e i commenti JSDoc. Per le librerie JavaScript più comuni, i file *d.ts* vengono acquisiti automaticamente. Per altre informazioni sull'acquisizione delle informazioni intelliSense, vedere [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json). Se si è interessati alla programmazione AngularJS in Visual Studio, è possibile usare l'estensione del servizio di linguaggio [AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) per Visual Studio per ottenere IntelliSense.

## <a name="check-syntax"></a>Controllare la sintassi

Il servizio di linguaggio usa ESLint per il controllo e il rilevamento di errori della sintassi. Se è necessario impostare le opzioni per il controllo della sintassi nell'editor, **selezionare** Opzioni  >    >  **strumenti JavaScript/TypeScript**  >  **Linting**. Le opzioni di rilevamento degli errori puntano al file di configurazione globale ESLint.

Nel codice seguente parte della sintassi viene evidenziata con una linea verde a zig zag all'interno dell'espressione. Spostare il puntatore del mouse sull'evidenziazione della sintassi.

![Visualizzazione di un errore di sintassi](../javascript/media/write-code-syntax-checking.png)

L'ultima riga di questo messaggio indica che il servizio di linguaggio prevedeva una virgola (`,`). La sottolineatura di colore verde indica un avviso. Le sottolineature rosse indicano un errore.

Nel riquadro inferiore è possibile fare clic sulla scheda **Elenco errori** per visualizzare l'avviso e la descrizione relativa nonché il nome file e il numero di riga.

![Visualizzazione dell'elenco errori](../javascript/media/write-code-error-list.png)

È possibile correggere il codice aggiungendo la virgola (`,`) prima di `"data"`.

Per altre informazioni sulla linting, vedere [Linting](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md).

## <a name="comment-out-code"></a>Codice di impostazione come commento

La barra degli strumenti, ovvero la riga di pulsanti sotto la barra dei menu di Visual Studio, contribuisce ad aumentare la produttività in fase di creazione del codice. Ad esempio, è possibile attivare o disattivare la modalità di completamento IntelliSense ([IntelliSense](../ide/using-intellisense.md) è un ausilio per la scrittura del codice che visualizza un elenco di metodi corrispondenti, tra le altre cose), aumentare o ridurre un rientro di riga o impostare come commento il codice che non si vuole compilare. In questa sezione, una porzione del codice verrà impostata come commento.

Selezionare una o più righe di codice nell'editor e quindi scegliere il pulsante **Imposta le righe selezionate come commento**![Pulsante impostazione commento ](../javascript/media/write-code-comment-out.png) sulla barra degli strumenti. Se si preferisce usare la tastiera, premere **CTRL** + **K**, **CTRL** + **C**.

I caratteri del commento di JavaScript `//` vengono aggiunti all'inizio di ogni riga selezionata per essere impostata come commento del codice.

## <a name="collapse-code-blocks"></a>Comprimere i blocchi di codice

Se è necessario semplificare la visualizzazione di alcune aree del codice, è possibile comprimerlo. Scegliere la piccola casella grigia contenente il segno meno sul margine della prima riga di una funzione. In caso contrario, se si è un utente della tastiera, posizionare il cursore in un punto qualsiasi del codice del costruttore e premere **CTRL** + **M**, **CTRL** + **M**.

![Pulsante di compressione evidenziato](../javascript/media/write-code-collapse-code.png)

Il blocco di codice viene compresso e visualizza solo la prima riga seguita dai puntini di sospensione (`...`). Per espandere di nuovo il blocco di codice, fare clic sulla stessa casella grigia in cui è ora presente un segno più oppure premere **di** nuovo CTRL + **M**, **CTRL** + **M.** Questa funzionalità è detta [Struttura](../ide/outlining.md) ed è particolarmente utile per comprimere funzioni molto lunghe o intere classi.

## <a name="view-definitions"></a>Visualizzare le definizioni

L Visual Studio editor semplifica l'ispezione della definizione di un tipo, di una funzione e così via. Un modo è passare al file che contiene la definizione, ad esempio scegliendo **Vai** a definizione in qualsiasi punto in cui viene fatto riferimento all'elemento di programmazione. Un metodo ancora più veloce che non sposta lo stato attivo dal file in uso è rappresentato da [Visualizza definizione](../ide/go-to-and-peek-definition.md#peek-definition). Prendiamo ad esempio la definizione del metodo `render` nell'esempio seguente.

Fare clic con il pulsante destro del mouse su `render` e scegliere **Visualizza definizione** dal menu del contenuto. In caso contrario, **premere ALT** + **F12.**

   Viene visualizzata una finestra popup con la definizione del metodo `render`. È possibile scorrere all'interno della finestra popup o anche esaminare la definizione di un altro tipo dal codice visualizzato.

   ![Finestra Visualizza definizione](../javascript/media/write-code-peek-definition.png)

Chiudere la finestra di visualizzazione della definizione scegliendo la piccola casella contenente una "x" nell'angolo in alto a destra della finestra popup.

## <a name="use-code-snippets"></a>Usare frammenti di codice

Visual Studio offre *frammenti di codice* utili che è possibile usare per generare in modo semplice e rapido blocchi di codice di uso comune. I [frammenti di codice](../ide/code-snippets.md) sono disponibili per vari linguaggi di programmazione, tra cui JavaScript. Ora verrà aggiunto un ciclo `for` al file di codice.

Posizionare il cursore nel punto in cui si vuole inserire il frammento di codice, fare clic con il pulsante destro del mouse e scegliere **Inserisci**  >  **frammento di codice**.

![Frammenti di codice in Visual Studio](../javascript/media/write-code-insert-snippet.png)

Nell'editor viene visualizzata la casella **Inserisci frammento**. Scegliere **Generale** e fare doppio clic sull'elemento **for** nell'elenco.

![Frammento di codice per un ciclo for in Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

In questo modo il frammento di codice del ciclo `for` viene aggiunto al codice:

```javascript
for (var i = 0; i < length; i++) {

}
```

È possibile esaminare i frammenti di codice disponibili per il linguaggio scegliendo Modifica frammento di codice  >  **IntelliSense** e quindi  >  scegliendo la cartella del linguaggio.

## <a name="see-also"></a>Vedi anche

- [Frammenti di codice](../ide/code-snippets.md)
- [Spostarsi all'interno del codice](../ide/navigating-code.md)
- [struttura](../ide/outlining.md)
- [Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Usare IntelliSense](../ide/using-intellisense.md)
