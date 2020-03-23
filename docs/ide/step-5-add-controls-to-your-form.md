---
title: 'Passaggio 5: Aggiungere controlli al modulo'
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631def96fc7e4b5d7858ea3474492b41c526da65
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579357"
---
# <a name="step-5-add-controls-to-your-form"></a>Passaggio 5: Aggiungere controlli al modulo

In questo passaggio si aggiungono controlli, ad esempio un controllo <xref:System.Windows.Forms.PictureBox> e un controllo <xref:System.Windows.Forms.CheckBox>, al form. Si aggiungono quindi controlli <xref:System.Windows.Forms.Button> al modulo.

## <a name="how-to-add-controls-to-your-form"></a>Come aggiungere controlli al modulo

1. Scegliere la scheda **Casella degli strumenti** sul lato sinistro dell'IDE di Visual Studio (o premere **Ctrl**+**CTRL Alt**+**X**), quindi espandere il gruppo **Controlli comuni.** Verranno visualizzati i controlli più comuni dei form.

1. Fare doppio clic sull'elemento **PictureBox** per aggiungere un controllo PictureBox al form. Poiché TableLayoutPanel è ancorato in modo da riempire il form, l'IDE aggiunge il controllo PictureBox alla prima cella vuota (angolo in alto a sinistra).

1. Scegliere il nuovo controllo **PictureBox** per selezionarlo, quindi scegliere il triangolo nero nel nuovo controllo PictureBox per visualizzare l'elenco attività, come illustrato nella schermata seguente.

    ![Attività di PictureBox](../ide/media/express_pictureboxtasks.png)<br/>PictureBox: *attività**

    > [!NOTE]
    > Se accidentalmente si aggiunge il tipo non corretto di controllo a TableLayoutPanel, è possibile eliminarlo. Fare clic con il pulsante destro del mouse sul controllo, quindi scegliere **Elimina** dal relativo menu di scelta rapida. È inoltre possibile rimuovere controlli dal form utilizzando la barra dei menu. Nella barra dei menu scegliere **Modifica** > **annullamento**o **Modifica** > **eliminazione**.

1. Nel menu **Attività PictureBox** dal controllo **PictureBox** scegliere il collegamento **Ancora nel contenitore padre.** La proprietà **Dock** di PictureBox verrà automaticamente impostata su **Fill**. A tale scopo, scegliere il **PictureBox** controllo per selezionarlo, passare alla **finestra proprietà** e assicurarsi che la proprietà **Dock** sia impostata su **Fill**.

1. Estendere il controllo PictureBox su entrambe le colonne modificandone la proprietà **ColumnSpan**. Nel **PictureBox**, scegliere il **PictureBox** controllo e impostare relativo **ColumnSpan** proprietà **2**. Inoltre, quando PictureBox è vuoto, si desidera visualizzare un frame vuoto. Impostare la proprietà **BorderStyle** su **Fixed3D**.

    > [!NOTE]
    > Se non viene visualizzata una proprietà **ColumnSpan** per PictureBox, è probabile che tale controllo sia stato aggiunto al form anziché a TableLayoutPanel. Per risolvere il problema, scegliere **PictureBox**, eliminarlo, scegliere **TableLayoutPanel**, quindi aggiungere un nuovo oggetto PictureBox.

1. Scegliere il **TableLayoutPanel** nel form e quindi aggiungere un CheckBox controllo al form. Fare doppio clic sull'elemento **CheckBox** nella **Casella degli strumenti** per aggiungere un nuovo controllo CheckBox alla cella libera successiva della tabella. Poiché un controllo PictureBox occupa le prime due celle, in TableLayoutPanel viene aggiunto un controllo CheckBox alla cella inferiore sinistra. Scegliere la proprietà **Text** e digitare la parola **Stretch**, come illustrato nell'immagine seguente.

    ![Controllo TextBox con la proprietà Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>***Controllo*** *TextBox con* ***proprietà*** *Stretch*

1. Scegliere il **TableLayoutPanel** nel form e quindi passare al **contenitori** gruppo nella **casella degli strumenti** (dove è stato ottenuto il TableLayoutPanel controllo) e fare doppio clic su **FlowLayoutPanel** elemento per aggiungere un nuovo controllo all'ultima cella (in basso a destra). Quindi, ancorare il FlowLayoutPanel nel TableLayoutPanel.Then, dock the FlowLayoutPanel in the TableLayoutPanel. A tale scopo, è possibile scegliere **Dock nel contenitore padre** nell'elenco attività Triangolo nero del FlowLayoutPanel oppure impostando la proprietà **Dock** di FlowLayoutPanel su **Fill**.

    > [!NOTE]
    > A <xref:System.Windows.Forms.FlowLayoutPanel> è un contenitore che dispone altri controlli in una riga, uno dopo l'altro. Quando si ridimensiona un FlowLayoutPanel, dispone tutti i relativi controlli in una singola riga, se ha spazio per eseguire questa operazione. In caso contrario, vengono disposti su più righe, uno sopra l'altro. <br/><br/>In questo caso, si userà un FlowLayoutPanel per contenere quattro pulsanti. Se i pulsanti dispongono uno sopra l'altro quando vengono aggiunti, assicurarsi di selezionare il FlowLayoutPanel prima di aggiungere i pulsanti. <br/><br/>In genere, ogni cella contiene un solo controllo. In questo esempio, la cella inferiore destra di TableLayoutPanel contiene quattro controlli pulsante. Perché?  Poiché il FlowLayoutPanel è un controllo contenitore, ovvero un controllo in una cella che contiene altri controlli.)

## <a name="to-add-buttons"></a>Per aggiungere pulsanti

1. Scegliere il nuovo controllo FlowLayoutPanel aggiunto. Passare a controlli comuni nella **casella degli strumenti** e fare doppio clic su Button elemento per aggiungere un controllo pulsante denominato button1 per il FlowLayoutPanel.Go to Common **Controls** in the Toolbox and double-click the **Button** item to add a button control called **button1** to your FlowLayoutPanel. Ripetere l'operazione per aggiungere un altro pulsante. L'IDE determina che un pulsante chiamato **button1** esiste già e denomina il successivo **button2**.

1. In genere, si aggiungono gli altri pulsanti utilizzando la **casella degli strumenti**. Questa volta, scegliere **button2**, quindi dalla barra dei menu scegliere **Modifica** > **copia** (o premere **Ctrl**+**C**). Quindi, scegli **Modifica** > **Incolla** dalla barra dei menu (o premi **Ctrl**+**V**) per incollare una copia del pulsante. Ora incollarlo nuovamente. Si noti che l'IDE aggiunge button3 e button4 per il FlowLayoutPanel.Notice that the IDE adds **button3** and **button4** to the FlowLayoutPanel.

    > [!NOTE]
    > È possibile copiare e incollare qualsiasi controllo. L'IDE denomina e posiziona i nuovi controlli in modo logico. Se si incolla un controllo in un contenitore, l'IDE sceglie lo spazio logico successivo per la posizione.

1. Scegliere il primo pulsante e impostarne la proprietà **Text** su **Visualizza immagine**. Impostare quindi le proprietà **Text** dei tre pulsanti successivi su **Cancella immagine**, **Imposta colore di sfondo** e **Chiudi**.

1. Ridimensionamo i pulsanti e disponiamoli in modo che si allineino al lato destro del pannello. Scegliere il **FlowLayoutPanel** ed esaminare il **relativo FlowDirection** proprietà. Modificarla in modo che venga impostata su **RightToLeft**.

   I pulsanti devono allinearsi al lato destro della cella e invertire l'ordine in modo che il pulsante **Mostra un'immagine** sia a destra.

    > [!NOTE]
    > Se i pulsanti sono ancora nell'ordine errato, è possibile trascinarli nel controllo FlowLayoutPanel per ridisporli in qualsiasi ordine. È possibile scegliere un pulsante e trascinarlo a sinistra o a destra.

1. Scegliere il pulsante **Chiudi** per selezionarlo. Quindi, per scegliere il resto dei pulsanti allo stesso tempo, premere e tenere premuto il **tasto Ctrl** e scegliere anche loro.

   Dopo aver selezionato tutti i pulsanti, passare alla finestra **Proprietà** e scorrere fino alla proprietà **AutoSize.** Questa proprietà consente di ridimensionare automaticamente il pulsante in modo che si adatti a tutto il testo. Impostarlo su **True**.

   I pulsanti sono ora ridimensionati correttamente e si trovano nell'ordine corretto. Se tutti e quattro i pulsanti sono selezionati, è possibile modificare tutte e quattro le proprietà **AutoSize** contemporaneamente. L'immagine seguente mostra i quattro pulsanti.

    ![Visualizzatore immagini con quattro pulsanti](../ide/media/express_autosize.png)<br/>***Visualizzatore di immagini*** *con quattro pulsanti*

1. Eseguire di nuovo il programma per visualizzare le modifiche.

   Si noti che i pulsanti e&mdash;la casella di controllo non fanno ancora nulla, ma lo faranno, presto.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 6: Assegnare un nome](../ide/step-6-name-your-button-controls.md)** ai controlli pulsante .

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 4: Disporre il form con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: Creare un quiz di matematica a tempoTutorial 2: Create a timed math quiz](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
