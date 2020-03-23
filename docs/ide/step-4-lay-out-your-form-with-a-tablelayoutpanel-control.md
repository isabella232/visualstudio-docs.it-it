---
title: 'Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d827077266adbe0a1ba8cabd1f19ae6d815df833
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579386"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel

In questo passaggio si aggiunge un controllo <xref:System.Windows.Forms.TableLayoutPanel> al form. Il TableLayoutPanel consente di allineare correttamente i controlli nel form che verrà aggiunto in un secondo momento.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Come definire il layout del form con un controllo TableLayoutPanel

1. Sul lato sinistro dell'IDE di Visual Studio, scegliere **View** > **Toolbox** la scheda Casella degli **Ctrl**+**Alt**+**X** **strumenti** .

1. Scegliere il piccolo simbolo del triangolo accanto al gruppo **Contenitori** per aprirlo, come illustrato nella schermata seguente.

     ![Gruppo Contenitori](../ide/media/express_toolbox.png)<br>
***Gruppo Contenitori*** *group*

1. È possibile aggiungere al form controlli quali pulsanti, caselle di controllo ed etichette. Fare doppio clic sul controllo TableLayoutPanel nella **casella degli strumenti**. In alternativa, è possibile trascinare il controllo dalla casella degli strumenti nel form. In questo caso, l'IDE aggiunge un TableLayoutPanel controllo al form, come illustrato nella schermata seguente.

     ![Controllo TableLayoutPanel](../ide/media/express_formtablelayout.png)<br>
***TableLayoutPanel*** *(controllo)*

    > [!NOTE]
    > Dopo aver aggiunto il controllo TableLayoutPanel, se nel form viene visualizzata una finestra con il titolo **Attività di TableLayoutPanel**, fare clic in qualsiasi punto all'interno del form per chiuderla. Si apprenderà di più su questa finestra più avanti nell'esercitazione.

     Si noti che la **casella degli strumenti** si espande per coprire il modulo quando si fa clic sulla relativa scheda e si chiude quando si fa clic in un punto esterno. Questa è la funzionalità Nascondi automaticamente nell'IDE. È possibile attivarlo o disattivarlo per una qualsiasi delle finestre scegliendo l'icona a forma di puntina da disegno nell'angolo superiore destro della finestra per attivare o disattivare Nascondi automaticamente e bloccarlo sul posto. L'icona a forma di puntina da disegno ha l'aspetto seguente.

     ![Icona della puntina da disegno](../ide/media/express_pushpintoolbox.png)<br>
***Icona della puntina da spinta*** *icon*

1. Verificare che sia selezionato il controllo TableLayoutPanel facendo clic su di esso. È possibile verificare quale controllo è selezionato esaminando l'elenco a discesa nella parte superiore della finestra **Proprietà,** come illustrato nella schermata seguente.

     ![Finestra Proprietà con il controllo TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
***Finestra Proprietà*** *con il* *controllo* ***TableLayoutPanel***

1. Scegliere il pulsante **Alfabetico** nella barra degli strumenti nella finestra **Proprietà**. In questo modo l'elenco delle proprietà nella finestra **Proprietà** viene ordinato in ordine alfabetico, in modo da semplificare l'individuazione delle proprietà in questa esercitazione.

1. Il selettore dei controlli è un elenco a discesa che si trova nella parte superiore della finestra **Proprietà**. In questo esempio è selezionato un controllo denominato `tableLayoutPanel1`. È possibile selezionare i controlli scegliendo un'area in **Progettazione Windows Form** o selezionandoli dal selettore dei controlli.

   Dopo aver selezionato TableLayoutPanel, individuare la relativa proprietà **Dock** e scegliere **Dock**, il cui valore dovrebbe essere impostato su **Nessuno**. Si noti che viene visualizzata una freccia a discesa accanto al valore. Scegliere la freccia e quindi selezionare il pulsante **Riempi** (il pulsante grande al centro), come illustrato nella schermata seguente.

     ![Finestra Proprietà con Riempimento selezionato](../ide/media/express_docktable.png)<br>
***Finestra Proprietà*** *con* ***l'opzione Riempimento*** *selezionata*

     Il termine *ancoraggio* in Visual Studio indica l'associazione di una finestra un'altra finestra o area nell'IDE. Ad esempio, la finestra **Proprietà** &mdash;può essere disancorata, ovvero&mdash;non collegata e mobile all'interno di Visual Studio oppure può essere ancorata a **Esplora soluzioni.**

1. Dopo aver impostato la proprietà TableLayoutPanel **Dock** su **Fill**, si noti che il pannello riempie l'intero form. Se si ridimensiona nuovamente il form, TableLayoutPanel resta ancorato e viene ridimensionato correttamente.

    > [!NOTE]
    > Un controllo TableLayoutPanel funziona come una tabella di Microsoft Office Word: dispone di righe e colonne e una singola cella può estendersi su più righe e colonne. Ogni cella può contenere un controllo (come un pulsante, una casella di controllo o un'etichetta). Il TableLayoutPanel deve <xref:System.Windows.Forms.PictureBox> avere un controllo che <xref:System.Windows.Forms.CheckBox> si estende su tutta la <xref:System.Windows.Forms.Button> riga superiore, un controllo nella cella inferiore sinistra e quattro controlli nella cella inferiore a destra.

1. Attualmente, TableLayoutPanel dispone di due righe delle stesse dimensioni e di due colonne delle stesse dimensioni. Rimpiccioliamo in modo che la riga superiore e la colonna destra siano entrambe molto più grandi. In **Progettazione Windows Form** selezionare il controllo TableLayoutPanel. Nell'angolo superiore destro si trova un piccolo pulsante a forma di triangolo nero, illustrato di seguito.

     ![Pulsante triangolare](../ide/media/express_iconblacktriangle.gif)<br>
***Pulsante Triangolo*** *button*

     Questo pulsante indica che il controllo dispone di attività che consentono di impostare automaticamente le proprietà.

1. Scegliere il triangolo per visualizzare l'elenco attività del controllo, come illustrato nella schermata seguente.

     ![Attività di TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***Attività TableLayoutPanelTableLayoutPanel*** *tasks*

1. Scegliere l'attività **Modifica righe e colonne** per visualizzare la finestra **Stili di riga e colonna**. Scegliere **Column1** e impostarne le dimensioni sul 15%, assicurandosi che il pulsante **Percentuale** sia selezionato e immettendo **15** nella casella **Percentuale**. (Questo è <xref:System.Windows.Forms.NumericUpDown> un controllo, che si userà in un'esercitazione successiva.) Scegliere **Colonna2** e impostarlo su 85 percento. Non scegliere ancora il pulsante **OK** per non chiudere la finestra. In tal caso, è possibile riaprirlo utilizzando l'elenco attività.

     ![Stili di riga e colonna di TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel*** *stili di riga e colonna*

1. Dall'elenco a discesa **Mostra** nella parte superiore della finestra **Stili colonna e riga** scegliere **Righe.** Impostare **Row1** su 90% e **Row2** su 10%.

1. Fare clic su **OK** . Il controllo TableLayoutPanel dispone ora di una riga grande nella parte superiore, una riga piccola nella parte inferiore, una colonna piccola a sinistra e una colonna grande a destra. È possibile ridimensionare le righe e le colonne in TableLayoutPanel scegliendo **tableLayoutPanel1** nel form e trascinandone i bordi di righe e colonne.

     ![Form1 con TableLayoutPanel ridimensionato](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1*** *(Visualizzatore immagini) con* ***TableLayoutPanel*** ridimensionato

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 5: Aggiungere controlli al form.](../ide/step-5-add-controls-to-your-form.md)**

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 3: Impostare le proprietà del modulo](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: Creare un quiz di matematica a tempoTutorial 2: Create a timed math quiz](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
