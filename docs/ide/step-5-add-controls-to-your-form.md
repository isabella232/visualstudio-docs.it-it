---
title: 'Passaggio 5: Aggiungere controlli al modulo'
description: Informazioni su come aggiungere controlli, ad esempio <xref:System.Windows.Forms.PictureBox> un controllo e un controllo , al <xref:System.Windows.Forms.CheckBox> form.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 638d7e32a522523cf53213fee1194c7a1a1bbc4e
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398416"
---
# <a name="step-5-add-controls-to-your-form"></a>Passaggio 5: Aggiungere controlli al modulo

In questo passaggio si aggiungono controlli, ad esempio un controllo <xref:System.Windows.Forms.PictureBox> e un controllo <xref:System.Windows.Forms.CheckBox>, al form. Si aggiungono quindi controlli <xref:System.Windows.Forms.Button> al modulo.

## <a name="how-to-add-controls-to-your-form"></a>Come aggiungere controlli al form

1. Scegliere la **scheda Casella** degli strumenti a sinistra dell'IDE Visual Studio (o premere **CTRL** + **ALT** + **X)** e quindi espandere il **gruppo Controlli** comuni. Verranno visualizzati i controlli più comuni dei form.

1. Fare doppio clic sull'elemento **PictureBox** per aggiungere un controllo PictureBox al form. Poiché TableLayoutPanel è ancorato in modo da riempire il form, l'IDE aggiunge il controllo PictureBox alla prima cella vuota (angolo in alto a sinistra).

1. Scegliere il **nuovo controllo PictureBox** per selezionarlo e quindi scegliere il triangolo nero nel nuovo controllo PictureBox per visualizzarne l'elenco attività, come illustrato nello screenshot seguente.

    ![Attività di PictureBox](../ide/media/express_pictureboxtasks.png)<br/>PictureBox **_ _tasks**

    > [!NOTE]
    > Se accidentalmente si aggiunge il tipo non corretto di controllo a TableLayoutPanel, è possibile eliminarlo. Fare clic con il pulsante destro del mouse sul controllo, quindi scegliere **Elimina** dal relativo menu di scelta rapida. È inoltre possibile rimuovere controlli dal form utilizzando la barra dei menu. Sulla barra dei menu scegliere **Modifica**  >  **Annulla** o **Modifica**  >  **elimina.**

1. Nel menu **Attività PictureBox** del **controllo PictureBox** scegliere il **collegamento Ancora nel contenitore** padre. La proprietà **Dock** di PictureBox verrà automaticamente impostata su **Fill**. Per visualizzare questa situazione, scegliere il **controllo PictureBox** per selezionarlo, passare alla finestra Proprietà e assicurarsi che la proprietà **Dock** sia impostata su **Fill.** 

1. Estendere il controllo PictureBox su entrambe le colonne modificandone la proprietà **ColumnSpan**. In **PictureBox** scegliere il **controllo PictureBox** e impostarne la **proprietà ColumnSpan** su **2.** Inoltre, quando PictureBox è vuoto, si desidera visualizzare un frame vuoto. Impostare la proprietà **BorderStyle** su **Fixed3D**.

    > [!NOTE]
    > Se non viene visualizzata una proprietà **ColumnSpan** per PictureBox, è probabile che tale controllo sia stato aggiunto al form anziché a TableLayoutPanel. Per risolvere il problema, scegliere **PictureBox,** eliminarlo, **scegliere TableLayoutPanel** e quindi aggiungere un nuovo oggetto PictureBox.

1. Scegliere **TableLayoutPanel** nel form e quindi aggiungere un controllo CheckBox al form. Fare doppio clic **sull'elemento CheckBox** nella **casella** degli strumenti per aggiungere un nuovo controllo CheckBox alla cella libera successiva della tabella. Poiché un controllo PictureBox occupa le prime due celle, in TableLayoutPanel viene aggiunto un controllo CheckBox alla cella inferiore sinistra. Scegliere la **proprietà Text** e digitare la parola **Stretch**, come illustrato nell'immagine seguente.

    ![Controllo TextBox con la proprietà Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>***TextBox** _ _control with* ***Stretch**_ _property*

1. Scegliere **TableLayoutPanel** nel form e quindi  passare al gruppo Contenitori nella casella degli strumenti **(in** cui è stato ottenuto il controllo TableLayoutPanel) e fare doppio clic sull'elemento **FlowLayoutPanel** per aggiungere un nuovo controllo all'ultima cella (in basso a destra). Ancorare quindi FlowLayoutPanel in TableLayoutPanel. A tale scopo, scegliere **Ancora** nel contenitore padre nell'elenco attività triangolo nero di FlowLayoutPanel o impostando la proprietà **Dock** di FlowLayoutPanel su **Fill**.

    > [!NOTE]
    > È <xref:System.Windows.Forms.FlowLayoutPanel> un contenitore che dispone altri controlli in una riga, uno dopo l'altro. Quando si ridimensiona flowLayoutPanel, tutti i relativi controlli vengono disloquisiti in una singola riga, se ha spazio a tale scopo. In caso contrario, vengono disposti su più righe, uno sopra l'altro. <br/><br/>In questo caso, si userà flowLayoutPanel per contenere quattro pulsanti. Se i pulsanti ne dispongono uno sopra l'altro quando vengono aggiunti, assicurarsi di selezionare FlowLayoutPanel prima di aggiungere i pulsanti. <br/><br/>In genere, ogni cella contiene un solo controllo. In questo esempio la cella in basso a destra di TableLayoutPanel contiene quattro controlli pulsante. Perché?  Poiché FlowLayoutPanel è un controllo contenitore, ovvero un controllo in una cella che contiene altri controlli.

## <a name="to-add-buttons"></a>Per aggiungere pulsanti

1. Scegliere il nuovo controllo FlowLayoutPanel aggiunto. Passare a **Controlli comuni nella** casella degli **strumenti** e fare doppio clic sull'elemento **Button** per aggiungere un controllo pulsante denominato **button1** a FlowLayoutPanel. Ripetere l'operazione per aggiungere un altro pulsante. L'IDE determina che un pulsante chiamato **button1** esiste già e denomina il successivo **button2**.

1. In genere, si aggiungono gli altri pulsanti usando la casella **degli strumenti**. Questa volta scegliere **button2** e quindi dalla barra dei menu scegliere **Modifica**  >  **copia** (o premere  + **CTRL+C).** Scegliere Quindi **Modifica**  >  **Incolla dalla** barra dei menu (o premere **CTRL** + **V)** per incollare una copia del pulsante. Ora incollarlo nuovamente. Si noti che l'IDE aggiunge **button3** **e button4** a FlowLayoutPanel.

    > [!NOTE]
    > È possibile copiare e incollare qualsiasi controllo. L'IDE denomina e posiziona i nuovi controlli in modo logico. Se si incolla un controllo in un contenitore, l'IDE sceglie lo spazio logico successivo per la posizione.

1. Scegliere il primo pulsante e impostarne la proprietà **Text** su **Visualizza immagine**. Impostare quindi le proprietà **Text** dei tre pulsanti successivi su **Cancella immagine**, **Imposta colore di sfondo** e **Chiudi**.

1. Ridimensionare i pulsanti e disporli in modo che siano allineati al lato destro del pannello. Scegliere **FlowLayoutPanel** e osservare la relativa **proprietà FlowDirection.** Modificarla in modo che venga impostata su **RightToLeft**.

   I pulsanti devono allinearsi al lato destro della cella e invertire l'ordine in modo che il pulsante **Mostra** un'immagine sia a destra.

    > [!NOTE]
    > Se i pulsanti sono ancora nell'ordine errato, è possibile trascinarli nel controllo FlowLayoutPanel per ridisporli in qualsiasi ordine. È possibile scegliere un pulsante e trascinarlo a sinistra o a destra.

1. Scegliere il pulsante **Chiudi** per selezionarlo. Quindi, per scegliere contemporaneamente gli altri pulsanti, tenere premuto **CTRL** e scegliere anche questi pulsanti.

   Dopo aver selezionato tutti i pulsanti, passare **alla** finestra Proprietà e scorrere fino alla **proprietà AutoSize.** Questa proprietà consente di ridimensionare automaticamente il pulsante in modo che si adatti a tutto il testo. Impostarlo su **True.**

   I pulsanti sono ora ridimensionati correttamente e si trovano nell'ordine corretto. Se tutti e quattro i pulsanti sono selezionati, è possibile modificare contemporaneamente tutte e quattro le proprietà **AutoSize.** L'immagine seguente mostra i quattro pulsanti.

    ![Visualizzatore immagini con quattro pulsanti](../ide/media/express_autosize.png)<br/>***Visualizzatore** immagini _ _with quattro pulsanti*

1. Eseguire di nuovo il programma per visualizzare le modifiche.

   Si noti che i pulsanti e la casella di controllo non fanno ancora &mdash; nulla, ma lo saranno a breve.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 6: Assegnare un nome ai controlli pulsante.](../ide/step-6-name-your-button-controls.md)**

* Per tornare al passaggio precedente dell'esercitazione, vedere Passaggio 4: Eseguire il layout [del form con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Vedi anche

* [Esercitazione 2: Creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
