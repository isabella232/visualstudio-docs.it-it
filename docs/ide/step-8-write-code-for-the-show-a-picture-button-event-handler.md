---
title: "Passaggio 8: Scrivere codice per il gestore dell'evento del pulsante Mostra immagine"
ms.date: 08/30/2019
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d74c9ecda0e3ab23c1f2ab1cb2180a60701c069a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579802"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Passaggio 8: Scrivere codice per il gestore dell'evento del pulsante Mostra immagine

In questo passaggio si fa in modo che il pulsante **Mostra immagine** funzioni come segue:

- Quando un utente sceglie tale pulsante, l'app apre una <xref:System.Windows.Forms.OpenFileDialog> casella.

- Se un utente apre un file di immagine, l'app mostra tale immagine in <xref:System.Windows.Forms.PictureBox> .

Nell'IDE è disponibile uno strumento potente denominato IntelliSense che agevola la scrittura del codice. Durante la digitazione del codice, l'IDE apre una casella con i completamenti suggeriti per le parole parziali immesse.

IntelliSense tenta di determinare cosa si desidera eseguire successivamente e passa automaticamente all'ultimo elemento scelto dall'elenco. È possibile utilizzare le frecce su o giù per spostarsi nell'elenco oppure continuare a digitare lettere per limitare le scelte. Quando viene visualizzata la scelta desiderata, premere **TAB** per selezionarla. In alternativa, è possibile ignorare i suggerimenti, se non si ritengono necessari.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Per scrivere il codice per il gestore dell'evento del pulsante Mostra immagine

1. Passare a **Progettazione Windows Form** e fare doppio clic sul pulsante **Mostra immagine**. L'IDE passa immediatamente alla finestra di progettazione del codice e sposta il cursore in modo che si trovi all'interno del `showButton_Click()` Metodo (in alternativa, `ShowButton_Click()` ) aggiunto in precedenza.

1. Digitare `i` nella riga vuota tra le due parentesi graffe `{ }`. (In Visual Basic, digitare sulla riga vuota tra `Private Sub...` e `End Sub` .) Viene visualizzata una finestra di **IntelliSense** , come illustrato nella figura seguente.

    ![IntelliSense con codice Visual C&#35;](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Il codice potrebbe non visualizzare i gestori eventi in lettere "camelCase".

1. La finestra di **IntelliSense** deve evidenziare la parola `if` . In caso contrario, immettere un valore minuscolo `f` e sarà. Si noti che viene visualizzata una casella *Descrizione comando* accanto alla finestra di **IntelliSense** con la descrizione **frammento di codice per l'istruzione If**. (In Visual Basic, la descrizione comando indica anche che si tratta di un frammento, ma con una formulazione leggermente diversa). Si vuole usare il frammento di codice, quindi scegliere il tasto **Tab** da inserire `if` nel codice. Premere quindi di nuovo **TAB** per usare il frammento di codice `if`. Se si è fatto clic in un altro punto e la finestra di **IntelliSense** non è più visualizzata, tornare con il tasto BACKSPACE su `i` e digitare di nuovo. La finestra di **IntelliSense** verrà riaperta.

    ![Codice Visual C&#35;](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Usare IntelliSense per immettere altro codice

Viene quindi usato IntelliSense per immettere altro codice per aprire una finestra **Apri file**. Se l'utente ha fatto clic sul pulsante **OK**, il controllo PictureBox carica il file selezionato dall'utente. I passaggi seguenti illustrano come immettere il codice e, sebbene ci siano molti passaggi, si tratta solo di poche sequenze di tasti:

 1. Iniziare con il testo **true** selezionato nel frammento. Digitare `op` per sovrascriverlo. In Visual Basic l'iniziale è maiuscola, pertanto digitare `Op`.

 1. Viene visualizzata la finestra di **IntelliSense** con **openFileDialog1**. Premere **TAB** per selezionarlo. In Visual Basic l'iniziale è maiuscola, pertanto viene visualizzato **OpenFileDialog1**. Assicurarsi che **OpenFileDialog1** sia selezionato.

     Per altre informazioni su `OpenFileDialog`, vedere [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Digitare un punto ( `.` ) (molti programmatori chiamano questo punto). Poiché è stato digitato un punto subito dopo **OpenFileDialog1**, viene visualizzata una finestra di **IntelliSense** , compilata con tutte le proprietà e i metodi del componente **OpenFileDialog** . Si tratta delle stesse proprietà visualizzate nel finestra **Proprietà** quando si sceglie l'oggetto in **Progettazione Windows Form**. È inoltre possibile scegliere metodi che indicano al componente di eseguire operazioni (ad esempio, aprire una finestra di dialogo).

    > [!NOTE]
    > Nella finestra di **IntelliSense** possono essere visualizzati sia proprietà che metodi. Per determinare gli elementi visualizzati, osservare l'icona a sinistra di ogni elemento nella finestra **IntelliSense**. Viene visualizzata un'immagine di un blocco accanto a ogni metodo e un'immagine di una chiave (o di una chiave fissa) accanto a ogni proprietà. È anche visualizzata un'icona a forma di saetta accanto a ogni evento. <br><br>Ecco le icone visualizzate:<br><br>![Icona del metodo](../ide/media/express_iconmethod.png)<br>![Icona della proprietà](../ide/media/express_iconproperty.png)<br>![Icona dell'evento](../ide/media/express_iconevent.png)

 1. Iniziare a digitare `ShowDialog` (l'uso di maiuscole non viene considerato in IntelliSense). Il metodo `ShowDialog()` visualizzerà la finestra di dialogo **Apri file**. Dopo che nella finestra viene evidenziato **ShowDialog**, premere **TAB**. È anche possibile evidenziare "ShowDialog" e premere **F1** per ottenere informazioni.

    Per altre informazioni sul metodo `ShowDialog()`, vedere [Metodo ShowDialog](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. Quando si usa un metodo in un controllo o un componente, ovvero si effettua una *chiamata a un metodo*, è necessario aggiungere le parentesi. Immettere quindi le parentesi di apertura e chiusura immediatamente dopo la "g" di `ShowDialog`: `()` Viene visualizzato "openFileDialog1.ShowDialog()".

    > [!NOTE]
    > I metodi sono una parte importante di qualsiasi app e in questa esercitazione sono stati illustrati diversi modi per usare i metodi. È possibile chiamare un metodo di un componente per indicare l'esecuzione di un'operazione, come è stato fatto quando si è chiamato il metodo `ShowDialog()` del componente **OpenFileDialog**. È possibile creare metodi personalizzati per fare in modo che l'app esegua operazioni, come quella che si sta compilando adesso, denominata `showButton_Click()` metodo, che apre una finestra di dialogo e un'immagine quando un utente sceglie un pulsante.

 1. Per C#, aggiungere uno spazio, quindi aggiungere due segni di uguale ( `==` ). Per Visual Basic, aggiungere uno spazio e quindi usare un solo segno di uguale (`=`). C# e Visual Basic utilizzano operatori di uguaglianza diversi.

 1. Aggiungere un altro spazio. Viene immediatamente visualizzata un'altra finestra di **IntelliSense**. Iniziare a digitare `DialogResult` e premere **TAB** per aggiungerlo.

    > [!NOTE]
    > Quando si scrive codice per chiamare un metodo, a volte viene restituito un valore. In questo caso il metodo <xref:System.Windows.Forms.CommonDialog.ShowDialog> del componente **OpenFileDialog** restituisce un valore <xref:System.Windows.Forms.DialogResult>. DialogResult è un valore speciale che fornisce informazioni sulle operazioni eseguite in una finestra di dialogo. Un componente **OpenFileDialog** può far sì che l'utente scelga **OK** o **Annulla**, quindi il relativo metodo `ShowDialog()` restituisce `DialogResult.OK` o `DialogResult.Cancel`.

 1. Digitare un punto per aprire la finestra di **IntelliSense** del valore DialogResult. Immettere la lettera `O` e premere **TAB** per inserire **OK**.

    Per altre informazioni su DialogResult, vedere [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > La prima riga di codice è stata completata. Per C#, il codice dovrebbe essere simile al seguente.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Per Visual Basic, il codice è analogo al seguente.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Aggiungere ora l'ultima riga di codice. È possibile digitarlo (o copiarlo e incollarlo), ma è consigliabile utilizzare IntelliSense per aggiungerlo. Più si ha dimestichezza con IntelliSense, più rapidamente si scriverà il codice. Il `showButton_Click()` metodo finale dovrebbe essere simile al codice seguente.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 9: esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md)**.

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
