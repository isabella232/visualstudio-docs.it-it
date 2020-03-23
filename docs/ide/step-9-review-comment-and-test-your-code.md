---
title: 'Passaggio 9: Esaminare, commentare e testare il codice'
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
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
ms.openlocfilehash: 1b31532bf6c26512e471ee787dc7219620e6db62
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579752"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Passaggio 9: Esaminare, commentare e testare il codice

Successivamente si aggiunge un commento al codice. Un commento è una nota che non cambia il modo in cui l'app si comporta. Facilita la comprensione del codice da parte di altri utenti. L'aggiunta di commenti al codice è un'operazione consigliabile.

Nel linguaggio C, due barre (//) contrassegnano una riga come commento. In Visual Basic viene utilizzata una virgoletta singola (') per contrassegnare una riga come commento. Dopo aver aggiunto un commento, è necessario testare l'applicazione. È consigliabile eseguire frequentemente e testare il codice mentre si lavora sui progetti, in modo che sia possibile intercettare e correggere eventuali problemi, prima che il codice diventi più complesso. Si tratta di un *test iterativo*.

Si è appena compilato un programma che funziona e sebbene non sia ancora finito, è già in grado di caricare un'immagine. Prima di aggiungere un commento al codice e di testarlo, prendere tempo per rivedere i concetti di codifica, poiché tali concetti si utilizzeranno frequentemente:

- Dopo aver fatto doppio clic sul pulsante **Mostra immagine** in **Progettazione Windows Form**, l'IDE ha aggiunto automaticamente un *metodo* al codice del programma.

- I metodi rappresentano la modalità di organizzazione del codice, vale a dire il modo in cui viene raggruppato il codice.

- Nella maggior parte dei casi, un metodo esegue un numero `showButton_Click()` limitato `ShowButton_Click()`di operazioni in un ordine specifico, ad esempio il modo in cui il metodo (o ) visualizza una finestra di dialogo e quindi carica un'immagine.

- Un metodo è costituito da *istruzioni* o righe di codice. Un metodo può essere considerato un modo per raggruppare istruzioni d codice.

- Quando un metodo viene eseguito, o *chiamato*, le istruzioni nel metodo vengono eseguite in ordine, una dopo l'altra, a cominciare dalla prima.

   Di seguito è riportato un esempio di istruzione.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Le istruzioni consentono ai programmi di eseguire azioni. Un'istruzione termina sempre con un punto e virgola. In Visual Basic la fine di una riga è la fine di un'istruzione. Non è necessario alcun punto e virgola in Visual Basic. L'istruzione precedente <xref:System.Windows.Forms.PictureBox> indica al controllo di caricare il file selezionato dall'utente con il componente **OpenFileDialog.**

## <a name="to-add-comments"></a>Per aggiungere commenti

1. Aggiungere il seguente commento al codice.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    Il gestore dell'evento <xref:System.Windows.Forms.Control.Click> del pulsante **showButton** è ora completato e funziona. Si è iniziato a scrivere codice, iniziando con l'istruzione `if`. Un'istruzione `if` è il modo in cui comunichi alla tua app: "Controlla questa cosa e, se è vera, esegui queste azioni". In questo caso, si indica all'app di aprire la finestra di dialogo **Apri file** e, se l'utente seleziona un file e sceglie il pulsante **OK,** caricare il file nella **finestra Immagine.**

    > [!TIP]
    > L'IDE è compilato in modo da semplificare la scrittura del codice anche tramite i *frammenti di codice*. Un frammento è un collegamento che viene espanso in un piccolo blocco di codice.
    >
    >  È possibile visualizzare tutti i frammenti disponibili. Nella barra dei menu scegliere Gestione**frammenti di codice** **degli strumenti** > . Nel linguaggio `if` C, il frammento di codice si trova in **Visual C.** Per Visual Basic, `if` i frammenti sono in modelli di **codice** > **condizionali e cicli**. È possibile utilizzare questo strumento di gestione per esplorare frammenti esistenti o aggiungere frammenti personalizzati.
    >
    >  Per attivare un frammento quando si digita il codice, digitarlo e premere **TAB**. Molti frammenti di codice vengono visualizzati nella finestra di **IntelliSense** ed è per questo motivo che è necessario premere **TAB** due volte: prima per selezionare il frammento di codice nella finestra di **IntelliSense** e poi per indicare all'IDE di usare il frammento di codice. Si noti che IntelliSense supporta il frammento `if`, ma non il frammento `ifelse`.

1. Prima di eseguire l'applicazione, salvare l'app scegliendo il pulsante **salva tutto** della barra degli strumenti, che dovrebbe essere simile alla schermata seguente.

     ![Pulsante della barra degli strumenti Salva tutto](../ide/media/express_iconsaveall.png)<br>
***Pulsante Salva tutto*** *button*

     In alternativa, per salvare l'app, scegli **Salva** > **tutto** dalla barra dei menu (oppure premi **Ctrl**+**Maiusc**+**S**). Una procedura consigliata consiste nel salvare presto e spesso.

     Quando è in esecuzione, il programma dovrebbe essere simile all'immagine seguente.

     ![Visualizzatore di immagini](../ide/media/express_pictureviewerdonerun.png)<br>***Visualizzatore di immagini***

## <a name="to-test-your-app"></a>Per testare l'app

1. Scegliere il **tasto F5** o il pulsante **Avvia debug** della barra degli strumenti.

1. Scegliere il pulsante **Visualizza immagine** per eseguire il codice appena scritto. Innanzitutto, l'app apre una finestra di dialogo **Apri file.** Verificare che i filtri vengano visualizzati nell'elenco a discesa **Tipo file** nella parte inferiore della finestra di dialogo. Passare quindi a un'immagine e aprirla. In genere è possibile trovare immagini di esempio incluse nel sistema operativo Windows nella cartella *Documenti*, che si trova all'interno della cartella *Immagini\Immagini campione*.

    > [!TIP]
    > Se nella finestra di dialogo relativa alla **selezione di un file immagine** non sono presenti immagini, assicurarsi che il filtro **Tutti i file (*.\*)** sia selezionato nell'elenco a discesa nella parte inferiore destra della finestra di dialogo.

1. Caricare un'immagine. L'immagine viene visualizzata in PictureBox. Provare quindi a ridimensionare il form trascinandone i bordi. Poiché PictureBox è ancorato all'interno di TableLayoutPanel, il quale è a sua volta ancorato all'interno del form, l'area dell'immagine verrà ridimensionata in modo da eguagliare la larghezza del form e da riempire il 90% del form nella parte superiore. È per questo motivo che sono stati usati i contenitori <xref:System.Windows.Forms.TableLayoutPanel> e <xref:System.Windows.Forms.FlowLayoutPanel>, che mantengono le dimensioni corrette del modulo quando l'utente lo ridimensiona.

     A questo punto le immagini più grandi superano i bordi del visualizzatore immagini. Nel prossimo passaggio verrà aggiunto il codice per adattare le immagini alla finestra.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 10: Scrivere codice per pulsanti aggiuntivi e una casella di controllo](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 8: Scrivere codice per il gestore dell'evento del pulsante Mostra immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: Creare un quiz di matematica a tempoTutorial 2: Create a timed math quiz](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
