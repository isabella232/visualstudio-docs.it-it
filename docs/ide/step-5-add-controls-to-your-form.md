---
title: 'Passaggio 5: Aggiungere controlli al modulo'
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77b8fc1f1f9f34a5b19756b7cf1370522f74075e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589968"
---
# <a name="step-5-add-controls-to-your-form"></a>Passaggio 5: Aggiungere controlli al modulo

In questo passaggio si aggiungono controlli, ad esempio un controllo <xref:System.Windows.Forms.PictureBox> e un controllo <xref:System.Windows.Forms.CheckBox>, al form. Si aggiungono quindi controlli <xref:System.Windows.Forms.Button> al modulo.

## <a name="how-to-add-controls-to-your-form"></a>Come aggiungere controlli al form

1. Scegliere la **scheda casella degli strumenti** sul lato sinistro dell'IDE di Visual Studio (oppure premere **Ctrl**+**ALT**+**X**), quindi espandere il gruppo **controlli comuni** . Verranno visualizzati i controlli più comuni dei form.

1. Fare doppio clic sull'elemento **PictureBox** per aggiungere un controllo PictureBox al form. Poiché TableLayoutPanel è ancorato in modo da riempire il form, l'IDE aggiunge il controllo PictureBox alla prima cella vuota (angolo in alto a sinistra).

1. Scegliere il nuovo controllo **PictureBox** per selezionarlo, quindi scegliere il triangolo nero sul nuovo controllo PictureBox per visualizzare il relativo elenco attività, come illustrato nello screenshot seguente.

    ![Attività di PictureBox](../ide/media/express_pictureboxtasks.png)<br/>PictureBox * * * *attività**

    > [!NOTE]
    > Se accidentalmente si aggiunge il tipo non corretto di controllo a TableLayoutPanel, è possibile eliminarlo. Fare clic con il pulsante destro del mouse sul controllo, quindi scegliere **Elimina** dal relativo menu di scelta rapida. È inoltre possibile rimuovere controlli dal form utilizzando la barra dei menu. Sulla barra dei menu scegliere **Modifica** > **Annulla** o **Modifica** > **Elimina**.

1. Nel menu **attività PictureBox** del controllo **PictureBox** scegliere il collegamento **ancora nel contenitore padre** . La proprietà **Dock** di PictureBox verrà automaticamente impostata su **Fill**. Per verificarlo, scegliere il controllo **PictureBox** per selezionarlo, passare alla finestra **Proprietà** e verificare che la proprietà **Dock** sia impostata su **Riempi**.

1. Estendere il controllo PictureBox su entrambe le colonne modificandone la proprietà **ColumnSpan**. In **PictureBox**, scegliere il controllo **PictureBox** e impostarne la proprietà **ColumnSpan** su **2**. Inoltre, quando PictureBox è vuoto, si desidera visualizzare un frame vuoto. Impostare la proprietà **BorderStyle** su **Fixed3D**.

    > [!NOTE]
    > Se non viene visualizzata una proprietà **ColumnSpan** per PictureBox, è probabile che tale controllo sia stato aggiunto al form anziché a TableLayoutPanel. Per risolvere questo problema, scegliere il controllo **PictureBox**, eliminarlo, scegliere **TableLayoutPanel** e quindi aggiungere un nuovo controllo PictureBox.

1. Scegliere **TableLayoutPanel** nel modulo e quindi aggiungere un controllo CheckBox al modulo. Fare doppio clic sull'elemento **CheckBox** nella **casella degli strumenti** per aggiungere un nuovo controllo CheckBox alla cella libera successiva della tabella. Poiché un controllo PictureBox occupa le prime due celle, in TableLayoutPanel viene aggiunto un controllo CheckBox alla cella inferiore sinistra. Scegliere la proprietà **Text** e digitare la parola **Stretch**, come illustrato nella figura seguente.

    ![Controllo TextBox con la proprietà Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>Controllo ***TextBox*** *con la* *Proprietà* stretch

1. Scegliere **TableLayoutPanel** nel form, quindi passare al gruppo **contenitori** nella **casella degli strumenti** (dove si è ottenuto il controllo TableLayoutPanel) e fare doppio clic sull'elemento **FlowLayoutPanel** per aggiungere un nuovo controllo all'ultima cella (in basso a destra). Quindi, ancorare FlowLayoutPanel in TableLayoutPanel. Questa operazione può essere eseguita scegliendo **ancora nel contenitore padre** nell'elenco attività del triangolo nero di FlowLayoutPanel o impostando la proprietà **Dock** di FlowLayoutPanel su **Fill**.

    > [!NOTE]
    > Un <xref:System.Windows.Forms.FlowLayoutPanel> è un contenitore che dispone gli altri controlli in una riga, uno dopo l'altro. Quando si ridimensiona un controllo FlowLayoutPanel, tutti i controlli vengono posizionati in una singola riga, se è disponibile spazio a tale scopo. In caso contrario, vengono disposti su più righe, uno sopra l'altro. <br/><br/>Qui viene usato un controllo FlowLayoutPanel per mantenere quattro pulsanti. Se i pulsanti sono disposti uno sopra l'altro quando vengono aggiunti, assicurarsi di selezionare FlowLayoutPanel prima di aggiungere i pulsanti. <br/><br/>In genere, ogni cella contiene un solo controllo. In questo esempio, la cella inferiore destra di TableLayoutPanel contiene quattro controlli pulsante. Perché?  Poiché FlowLayoutPanel è un controllo contenitore, che è un controllo in una cella che contiene altri controlli.

## <a name="to-add-buttons"></a>Per aggiungere pulsanti

1. Scegliere il nuovo controllo FlowLayoutPanel aggiunto. Passare a **Controlli comuni** nella **casella degli strumenti** e fare doppio clic sull'elemento **Button** per aggiungere un pulsante denominato **button1** a FlowLayoutPanel. Ripetere l'operazione per aggiungere un altro pulsante. L'IDE determina che un pulsante chiamato **button1** esiste già e denomina il successivo **button2**.

1. In genere, si aggiungono gli altri pulsanti utilizzando la **casella degli strumenti**. Questa volta scegliere **Button2**, quindi dalla barra dei menu scegliere **modifica** > **copia** (o premere **CTRL**+**C**). Scegliere quindi **modifica** > **Incolla** dalla barra dei menu o premere **CTRL**+**V**per incollare una copia del pulsante. Ora incollarlo nuovamente. Si noti che l'IDE aggiunge **Button3** e **Button4** a FlowLayoutPanel.

    > [!NOTE]
    > È possibile copiare e incollare qualsiasi controllo. L'IDE denomina e posiziona i nuovi controlli in modo logico. Se si incolla un controllo in un contenitore, l'IDE sceglie lo spazio logico successivo per la posizione.

1. Scegliere il primo pulsante e impostarne la proprietà **Text** su **Visualizza immagine**. Impostare quindi le proprietà **Text** dei tre pulsanti successivi su **Cancella immagine**, **Imposta colore di sfondo** e **Chiudi**.

1. Ridimensionare i pulsanti e disporli in modo che siano allineati al lato destro del pannello. Scegliere il controllo **FlowLayoutPanel** e osservarne la proprietà **FlowDirection**. Modificarla in modo che venga impostata su **RightToLeft**.

   I pulsanti devono essere allineati al lato destro della cella e invertire l'ordine in modo che il pulsante **Visualizza immagine** si trovi sulla destra.

    > [!NOTE]
    > Se i pulsanti sono ancora nell'ordine errato, è possibile trascinarli nel controllo FlowLayoutPanel per ridisporli in qualsiasi ordine. È possibile scegliere un pulsante e trascinarlo a sinistra o a destra.

1. Scegliere il pulsante **Chiudi** per selezionarlo. Quindi, per scegliere il resto dei pulsanti contemporaneamente, tenere premuto il tasto **CTRL** e sceglierli.

   Dopo aver selezionato tutti i pulsanti, passare alla finestra **Proprietà** e scorrere verso l'alto fino alla proprietà **AutoSize** . Questa proprietà consente di ridimensionare automaticamente il pulsante in modo che si adatti a tutto il testo. Impostarla su **true**.

   I pulsanti sono ora ridimensionati correttamente e si trovano nell'ordine corretto. (Purché tutti i quattro pulsanti siano selezionati, è possibile modificare tutte e quattro le proprietà **AutoSize** contemporaneamente). Nella figura seguente sono illustrati i quattro pulsanti.

    ![Visualizzatore immagini con quattro pulsanti](../ide/media/express_autosize.png)<br/>***Visualizzatore immagini*** *con quattro pulsanti*

1. A questo punto, eseguire di nuovo il programma per visualizzare le modifiche.

   Si noti che i pulsanti e la casella di controllo non eseguono alcuna operazione ancora&mdash;ma saranno presto disponibili.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

* Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 6: assegnare un nome ai pulsanti](../ide/step-6-name-your-button-controls.md)** .

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
