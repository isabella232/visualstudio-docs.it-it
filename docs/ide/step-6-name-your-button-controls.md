---
title: 'Passaggio 6: Assegnare un nome ai pulsanti'
description: Informazioni su come assegnare un nome ai controlli pulsante.
ms.custom: SEO-VS-2020
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
ms.topic: tutorial
dev_langs:
- CSharp
- VB
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e1214d5e640364e0a5cc256f3f78cbd17cc1acdb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094036"
---
# <a name="step-6-name-your-button-controls"></a>Passaggio 6: Assegnare un nome ai pulsanti

Nel modulo c'è un solo oggetto <xref:System.Windows.Forms.PictureBox>. Quando è stato aggiunto, l'IDE lo ha automaticamente denominato **pictureBox1**. C'è un solo oggetto <xref:System.Windows.Forms.CheckBox>, denominato **checkBox1**. A breve si scriverà codice che farà riferimento a CheckBox e PictureBox. Poiché è presente solo uno di questi controlli, si saprà cosa significa quando viene visualizzato **pictureBox1** o **checkBox1** nel codice.

> [!TIP]
> In Visual Basic, l'impostazione predefinita per la prima lettera di qualsiasi nome di controllo è la maiuscola, pertanto i nomi sono **PictureBox1**, **CheckBox1** e così via.

Vi sono quattro pulsanti nel form e l'IDE li ha denominati **button1**, **button2**, **button3** e **button4**. Da un semplice sguardo ai nomi correnti non è possibile capire quale pulsante corrisponda al pulsante **Chiudi** e quale corrisponda al pulsante **Visualizza immagine** . È questo il motivo per cui è utile assegnare nomi più descrittivi ai pulsanti.

## <a name="to-name-your-button-controls"></a>Per assegnare un nome ai pulsanti

1. Nel form scegliere il pulsante **Chiudi** . Se sono ancora selezionati tutti i pulsanti, premere **ESC** per annullare la selezione. Scorrere nella finestra **Proprietà** fino a visualizzare la **proprietà (Nome).** La **proprietà (Name)** si trova nella parte superiore quando le proprietà sono in ordine alfabetico. Modificare il nome in **closeButton**, come illustrato nello screenshot seguente.

    ![Finestra Proprietà con il nome closeButton](../ide/media/express_setnameproperty.png)<br>***Proprietà** _ _finestra con* ***closeButton**_ _name*

    > [!NOTE]
    > Provare a modificare il nome del pulsante per **chiudere Button**, con uno spazio tra le parole "close" e "Button". In questo caso, l'IDE visualizza un messaggio di errore: "Valore della proprietà non valido". Gli spazi (e alcuni altri caratteri) non sono consentiti nei nomi dei controlli.

1. Rinominare gli altri tre pulsanti **backgroundButton**, **clearButton** e **showButton**.
È possibile verificare i nomi facendo clic sull'elenco a discesa del selettore dei controlli nella finestra **Proprietà** . Vengono visualizzati i nuovi nomi dei pulsanti.

1. Fare doppio clic sul pulsante **Visualizza immagine** nel form. In alternativa, scegliere il **pulsante Mostra** immagine nel modulo e quindi premere **INVIO.** Quando si esegue questa operazione, l'IDE apre una scheda aggiuntiva nella finestra principale denominata **Form1.cs.** Se si usa Visual Basic, la scheda è denominata **Form1.vb**.

   Questa scheda visualizza il file di codice dietro il modulo, come illustrato nello screenshot seguente.

    ![Scheda Form1.cs con codice Visual C&#35;](../ide/media/express_showbuttoncode.png)<br>
***Form1.cs** _ _tab con codice C# *

    > [!NOTE]
    > La scheda Form1.cs o Form1.vb potrebbe invece visualizzare **showButton** **come ShowButton.**

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

   Si sta esaminando il codice denominato `showButton_Click()` (in alternativa, `ShowButton_Click()` ). È stato aggiunto dall'IDE nel codice del form quando si è aperto il file di codice per il pulsante **showButton** . In fase di progettazione, quando si apre il file di codice per un controllo in un form, il codice, se non esiste già, viene generato per il controllo. Questo codice, noto come *metodo*, viene eseguito quando si esegue l'app e si sceglie il controllo , in questo caso il pulsante **Mostra un'immagine.**

1. Scegliere di **nuovo** la scheda Progettazione form Windows (**Form1.cs [Progettazione]**) e quindi aprire il file di codice per il pulsante Cancella immagine per creare un metodo nel codice del form.  Ripetere questa operazione per i restanti due pulsanti. L'IDE aggiunge ogni volta un nuovo metodo al file del codice del form.

1. Per aggiungere un altro metodo, aprire il file di codice per il controllo **CheckBox** in Progettazione **Windows Form** per fare in modo che l'IDE apportare un `checkBox1_CheckedChanged()` metodo. Tale metodo viene chiamato ogni volta che l'utente seleziona o deseleziona la casella di controllo.

   > [!TIP]
   > Quando si lavora a un'app, spesso ci si sposta tra l'editor di codice e **Windows Progettazione Form.** L'IDE facilita lo spostamento nel progetto. Usare **Esplora soluzioni** per aprire progettazione form **Windows** facendo doppio clic su *Form1.cs* in C# o *Form1.vb* in Visual Basic oppure sulla barra dei menu scegliere Progettazione  >  viste.

    Di seguito viene mostrato il nuovo codice visualizzato nell'editor di codice.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs" id="Snippet2":::

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb" id="Snippet2":::

    > [!NOTE]
    > Il codice potrebbe non visualizzare i gestori eventi in lettere "camelCase".

    I cinque metodi aggiunti sono denominati gestori eventi *,* perché l'applicazione li chiama ogni volta che si verifica un evento, ad esempio la scelta di un pulsante o la selezione di una casella da parte dell'utente.

    Quando si visualizza il codice per un controllo nell'IDE in fase di progettazione, in Visual Studio viene aggiunto un metodo del gestore eventi per il controllo, se non è presente. Ad esempio, quando si fa doppio clic su un pulsante, l'IDE aggiunge un gestore dell'evento per il relativo evento <xref:System.Windows.Forms.Control.Click>, che viene chiamato ogni volta che l'utente fa clic sul pulsante. Quando si fa doppio clic su una casella di controllo, l'IDE aggiunge un gestore dell'evento per il relativo evento <xref:System.Windows.Forms.CheckBox.CheckedChanged>, che viene chiamato ogni volta che l'utente seleziona o deseleziona la casella.

    Dopo aver aggiunto un gestore dell'evento per un controllo, è possibile tornarvi in qualsiasi momento da **Progettazione Windows Form** facendo doppio clic sul controllo o scegliendo **Visualizza** > **Codice** sulla barra dei menu.

    I nomi sono importanti quando si compilano programmi e i metodi (inclusi i gestori di eventi) possono avere qualsiasi nome si desideri. Quando si aggiunge un gestore dell'evento con l'IDE, viene creato un nome basato sul nome del controllo e sull'evento gestito.

    Ad esempio, l'evento Click per un pulsante denominato **showButton** viene chiamato metodo del gestore eventi `showButton_Click()` (in alternativa, `ShowButton_Click()` ). Inoltre, vengono generalmente aggiunte parentesi di apertura e chiusura `()` dopo il nome del metodo, per indicare che si tratta di metodi.

    Se si decide di modificare il nome di una variabile di codice, fare clic con il pulsante destro del mouse sulla variabile nel codice e quindi scegliere **Refactoring**  >  **Rinomina**. Tutte le istanze della variabile nel codice vengono rinominate. Per altre informazioni, vedere [Refactoring di ridenominazione.](../ide/reference/rename.md)

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 7: Aggiungere componenti della finestra di dialogo al modulo.](../ide/step-7-add-dialog-components-to-your-form.md)**

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: Aggiungere controlli al modulo.](../ide/step-5-add-controls-to-your-form.md)

## <a name="see-also"></a>Vedi anche

* [Esercitazione 2: Creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
