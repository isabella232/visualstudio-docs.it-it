---
title: 'Passaggio 6: Assegnare un nome ai pulsanti'
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
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
ms.openlocfilehash: a5c23f48e803665e00155d1b546ace4e4ec7bc54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579788"
---
# <a name="step-6-name-your-button-controls"></a>Passaggio 6: Assegnare un nome ai pulsanti

Nel modulo c'è un solo oggetto <xref:System.Windows.Forms.PictureBox>. Quando è stato aggiunto, l'IDE lo ha automaticamente denominato **pictureBox1**. C'è un solo oggetto <xref:System.Windows.Forms.CheckBox>, denominato **checkBox1**. Presto, si scriverà del codice, e che il codice farà riferimento al CheckBox e PictureBox. Poiché è presente solo uno di questi controlli, si saprà cosa significa quando viene visualizzato **pictureBox1** o **checkBox1** nel codice.

> [!TIP]
> In Visual Basic, l'impostazione predefinita per la prima lettera di qualsiasi nome di controllo è la maiuscola, pertanto i nomi sono **PictureBox1**, **CheckBox1**e così via.

Vi sono quattro pulsanti nel form e l'IDE li ha denominati **button1**, **button2**, **button3**e **button4**. Da un semplice sguardo ai nomi correnti non è possibile capire quale pulsante corrisponda al pulsante **Chiudi** e quale corrisponda al pulsante **Visualizza immagine** . È questo il motivo per cui è utile assegnare nomi più descrittivi ai pulsanti.

## <a name="to-name-your-button-controls"></a>Per assegnare un nome ai pulsanti

1. Nel form scegliere il pulsante **Chiudi** . Se sono ancora selezionati tutti i pulsanti, scegliere **ESC** per annullare la selezione. Scorrere nella finestra **Proprietà** fino a visualizzare la proprietà **(Nome).** (La proprietà **(Nome)** si trova nella parte superiore quando le proprietà sono alfabetiche.) Modificare il nome in **closeButton**, come illustrato nella schermata seguente.

    ![Finestra Proprietà con il nome closeButton](../ide/media/express_setnameproperty.png)<br>***Finestra Proprietà*** *con* *il nome* ***closeButton***

    > [!NOTE]
    > Provare a cambiare il nome del pulsante per **chiudere Button**, con uno spazio tra le parole "close" e "Button". In questo caso, l'IDE viene visualizzato un messaggio di errore: "Valore della proprietà non è valido". Gli spazi (e alcuni altri caratteri) non sono consentiti nei nomi dei controlli.

1. Rinominare gli altri tre pulsanti **backgroundButton**, **clearButton**e **showButton**.
È possibile verificare i nomi facendo clic sull'elenco a discesa del selettore dei controlli nella finestra **Proprietà** . Vengono visualizzati i nuovi nomi dei pulsanti.

1. Fare doppio clic sul pulsante **Visualizza immagine** nel form. In alternativa, scegliere il pulsante **Mostra immagine** nel modulo e quindi premere **INVIO.** In questo caso, l'IDE apre una scheda aggiuntiva nella finestra principale denominata **Form1.cs**. Se si utilizza Visual Basic, la scheda è denominata **Form1.vb**.

   Questa scheda visualizza il file di codice dietro il form, come illustrato nella schermata seguente.

    ![Scheda Form1.cs con codice Visual C&#35;](../ide/media/express_showbuttoncode.png)<br>
***Form1.cs*** *scheda con il codice C*

    > [!NOTE]
    > La scheda Form1.cs o Form1.vb potrebbe invece visualizzare **showButton** come **ShowButton.**

1. Concentrare l'attenzione su questa parte del codice.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click

    End Sub
    ```

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   Si sta esaminando il `showButton_Click()` codice chiamato `ShowButton_Click()`(in alternativa, ). È stato aggiunto dall'IDE nel codice del form quando si è aperto il file di codice per il pulsante **showButton** . In fase di progettazione, quando si apre il file di codice per un controllo in un form, il codice, se non esiste già, viene generato per il controllo. Questo codice, noto come *metodo*, viene eseguito quando si esegue l'app e si sceglie il controllo, in questo caso il pulsante **Mostra immagine.**

1. Scegliere nuovamente la scheda **Progettazione Windows Form** (**Form1.cs [Progettazione]**), quindi aprire il file di codice per il pulsante **Cancella l'immagine** per creare un metodo nel codice del form. Ripetere questa operazione per i restanti due pulsanti. L'IDE aggiunge ogni volta un nuovo metodo al file del codice del form.

1. Per aggiungere un altro metodo, aprire il file di codice per il **controllo CheckBox** in **Progettazione Windows Form** per fare in modo che l'IDE aggiurrà un `checkBox1_CheckedChanged()` metodo. Tale metodo viene chiamato ogni volta che l'utente seleziona o deseleziona la casella di controllo.

   > [!TIP]
   > Quando si lavora su un'app, spesso ci si sposta tra l'editor di codice e **Progettazione Windows Form**. L'IDE facilita lo spostamento nel progetto. Utilizzare **Esplora soluzioni** per aprire **Progettazione Windows Form** facendo doppio clic su *Form1.cs* in Visual Basic o in *Visual* Basic oppure sulla barra dei menu scegliere**Progettazione** **viste** > .

    Di seguito viene mostrato il nuovo codice visualizzato nell'editor di codice.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Il codice potrebbe non visualizzare i gestori eventi in lettere "camelCase".

    I cinque metodi aggiunti vengono chiamati *gestori eventi*, poiché l'applicazione li chiama ogni volta che si verifica un evento, ad esempio un utente che sceglie un pulsante o seleziona una casella.

    Quando si visualizza il codice per un controllo nell'IDE in fase di progettazione, in Visual Studio viene aggiunto un metodo del gestore eventi per il controllo, se non è presente. Ad esempio, quando si fa doppio clic su un pulsante, l'IDE aggiunge un gestore dell'evento per il relativo evento <xref:System.Windows.Forms.Control.Click>, che viene chiamato ogni volta che l'utente fa clic sul pulsante. Quando si fa doppio clic su una casella di controllo, l'IDE aggiunge un gestore dell'evento per il relativo evento <xref:System.Windows.Forms.CheckBox.CheckedChanged>, che viene chiamato ogni volta che l'utente seleziona o deseleziona la casella.

    Dopo aver aggiunto un gestore dell'evento per un controllo, è possibile tornarvi in qualsiasi momento da **Progettazione Windows Form** facendo doppio clic sul controllo o scegliendo **Visualizza** > **Codice** sulla barra dei menu.

    I nomi sono importanti quando si compilano programmi e i metodi (inclusi i gestori di eventi) possono avere qualsiasi nome si desideri. Quando si aggiunge un gestore dell'evento con l'IDE, viene creato un nome basato sul nome del controllo e sull'evento gestito.

    Ad esempio, il Click evento per un `showButton_Click()` pulsante denominato `ShowButton_Click()` **showButton** viene chiamato il (in alternativa, ) metodo del gestore eventi. Inoltre, vengono generalmente aggiunte parentesi di apertura e chiusura `()` dopo il nome del metodo, per indicare che si tratta di metodi.

    Se si decide di modificare il nome di una variabile di codice, fare clic con il pulsante destro del mouse sulla variabile nel codice e quindi scegliere > **Refactorrename**. **Refactor** Tutte le istanze della variabile nel codice vengono rinominate. Per ulteriori informazioni, vedere [Rinominare il refactoring](../ide/reference/rename.md).

## <a name="next-steps"></a>Passaggi successivi

* Per passare al passaggio successivo dell'esercitazione, vedere **[Passaggio 7: Aggiungere componenti della finestra di dialogo al form.](../ide/step-7-add-dialog-components-to-your-form.md)**

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: Aggiungere controlli al form.](../ide/step-5-add-controls-to-your-form.md)

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: Creare un quiz di matematica a tempoTutorial 2: Create a timed math quiz](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
