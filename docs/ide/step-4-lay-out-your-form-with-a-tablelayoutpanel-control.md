---
title: Creare il layout del modulo con un controllo TableLayoutPanel
description: Layout del modulo con un controllo TableLayoutPanel nell'esercitazione creare un visualizzatore di immagini.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: aa997d001fb2e6400516acea39e299ea39dc19ef
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397798"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel

In questo passaggio si aggiunge un controllo <xref:System.Windows.Forms.TableLayoutPanel> al form. TableLayoutPanel consente di allineare correttamente i controlli nel modulo che verrà aggiunto in seguito.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Come impostare il layout del form con un controllo TableLayoutPanel

1. Sul lato sinistro dell'IDE Visual Studio scegliere  la scheda Casella degli strumenti. In alternativa, scegliere Visualizza casella degli strumenti dalla barra dei menu o  >   premere **CTRL** + **ALT** + **X.**

1. Scegliere il piccolo simbolo del triangolo accanto **al gruppo Contenitori** per aprirlo, come illustrato nello screenshot seguente.

     ![Gruppo Contenitori](../ide/media/express_toolbox.png)<br>
***Contenitori** _ _group*

1. È possibile aggiungere al form controlli quali pulsanti, caselle di controllo ed etichette. Fare doppio clic sul controllo TableLayoutPanel nella **casella degli strumenti**. In caso contrario, è possibile trascinare il controllo dalla casella degli strumenti nel form. Quando si esegue questa operazione, l'IDE aggiunge un controllo TableLayoutPanel al form, come illustrato nello screenshot seguente.

     ![Controllo TableLayoutPanel](../ide/media/express_formtablelayout.png)<br>
***TableLayoutPanel** _ _control*

    > [!NOTE]
    > Dopo aver aggiunto il controllo TableLayoutPanel, se nel form viene visualizzata una finestra con il titolo **Attività di TableLayoutPanel**, fare clic in qualsiasi punto all'interno del form per chiuderla. Altre informazioni su questa finestra verranno apprese più avanti nell'esercitazione.

     Si noti che la **casella degli strumenti** si espande per coprire il modulo quando si fa clic sulla relativa scheda e si chiude quando si fa clic in un punto esterno. Questa è la funzionalità Nascondi automaticamente nell'IDE. È possibile attivarla o disattivarla per una delle finestre scegliendo l'icona della puntina da disegno nell'angolo superiore destro della finestra per attivare o disattivare Nascondi automaticamente e bloccarla sul posto. L'icona a forma di puntina da disegno ha l'aspetto seguente.

     ![Icona della puntina da disegno](../ide/media/express_pushpintoolbox.png)<br>
***Puntina** da disegno _ _icon*

1. Verificare che sia selezionato il controllo TableLayoutPanel facendo clic su di esso. È possibile verificare il controllo selezionato esaminando l'elenco a discesa nella parte superiore della finestra **Proprietà,** come illustrato nello screenshot seguente.

     ![Finestra Proprietà con il controllo TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
***Proprietà** _ _finestra che mostra* ***TableLayoutPanel**_ _control*

1. Scegliere il pulsante **Alfabetico** nella barra degli strumenti nella finestra **Proprietà**. In questo modo l'elenco delle proprietà nella finestra **Proprietà** viene ordinato in ordine alfabetico, semplificando l'individuazione delle proprietà in questa esercitazione.

1. Il selettore dei controlli è un elenco a discesa che si trova nella parte superiore della finestra **Proprietà**. In questo esempio è selezionato un controllo denominato `tableLayoutPanel1`. È possibile selezionare i controlli scegliendo un'area in **Progettazione Windows Form** o selezionandoli dal selettore dei controlli.

   Dopo aver selezionato TableLayoutPanel, individuare la relativa proprietà **Dock** e scegliere **Dock**, il cui valore dovrebbe essere impostato su **Nessuno**. Si noti che viene visualizzata una freccia a discesa accanto al valore. Scegliere la freccia e quindi selezionare il pulsante **Riempimento** (il pulsante grande al centro), come illustrato nello screenshot seguente.

     ![Finestra Proprietà con Riempimento selezionato](../ide/media/express_docktable.png)<br>
***Proprietà** _ _finestra con* ***Riempimento**_ _selected*

     Il termine *ancoraggio* in Visual Studio indica l'associazione di una finestra un'altra finestra o area nell'IDE. Ad esempio, **la** finestra Proprietà può essere disancosata, ad esempio, non ancorata e mobile all'interno di Visual Studio oppure può essere ancorata a &mdash; &mdash; **Esplora soluzioni**.

1. Dopo aver impostato la  proprietà Dock di TableLayoutPanel **su Fill,** si noti che il pannello riempie l'intero modulo. Se si ridimensiona nuovamente il form, TableLayoutPanel resta ancorato e viene ridimensionato correttamente.

    > [!NOTE]
    > Un controllo TableLayoutPanel funziona come una tabella di Microsoft Office Word: dispone di righe e colonne e una singola cella può estendersi su più righe e colonne. Ogni cella può contenere un controllo (come un pulsante, una casella di controllo o un'etichetta). TableLayoutPanel deve avere un controllo che si estende sull'intera riga superiore, un controllo nella cella inferiore sinistra e quattro controlli nella cella <xref:System.Windows.Forms.PictureBox> <xref:System.Windows.Forms.CheckBox> inferiore <xref:System.Windows.Forms.Button> destra.

1. Attualmente, TableLayoutPanel dispone di due righe delle stesse dimensioni e di due colonne delle stesse dimensioni. Verranno ridimensionati in modo che la riga superiore e la colonna di destra siano entrambe molto più grandi. In **Progettazione Windows Form** selezionare il controllo TableLayoutPanel. Nell'angolo superiore destro si trova un piccolo pulsante a forma di triangolo nero, illustrato di seguito.

     ![Pulsante triangolare](../ide/media/express_iconblacktriangle.gif)<br>
***Triangolo** _ _button*

     Questo pulsante indica che il controllo dispone di attività che consentono di impostare automaticamente le proprietà.

1. Scegliere il triangolo per visualizzare l'elenco attività del controllo, come illustrato nello screenshot seguente.

     ![Attività di TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***TableLayoutPanel** _ _tasks*

1. Scegliere l'attività **Modifica righe e colonne** per visualizzare la finestra **Stili di riga e colonna**. Scegliere **Column1** e impostarne le dimensioni sul 15%, assicurandosi che il pulsante **Percentuale** sia selezionato e immettendo **15** nella casella **Percentuale**. Si tratta di un <xref:System.Windows.Forms.NumericUpDown> controllo che verrà utilizzato in un'esercitazione successiva. Scegliere **Column2** e impostarlo su 85%. Non scegliere ancora il pulsante **OK** per non chiudere la finestra. In questo caso, tuttavia, è possibile riaprirlo usando l'elenco attività.

     ![Stili di riga e colonna di TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel** _ _column e stili di riga*

1. **Nell'elenco** a discesa Mostra nella parte superiore della finestra Stili di riga **e** colonna scegliere **Righe.** Impostare **Row1** su 90% e **Row2** su 10%.

1. Fare clic su **OK** . Il controllo TableLayoutPanel dispone ora di una riga grande nella parte superiore, una riga piccola nella parte inferiore, una colonna piccola a sinistra e una colonna grande a destra. È possibile ridimensionare le righe e le colonne in TableLayoutPanel scegliendo **tableLayoutPanel1** nel form e trascinandone i bordi di riga e colonna.

     ![Form1 con TableLayoutPanel ridimensionato](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1** _ (Visualizzatore immagini) con ridimensionato* ***TableLayoutPanel***

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 5: Aggiungere controlli al modulo.](../ide/step-5-add-controls-to-your-form.md)**

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 3: Impostare le proprietà del modulo](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Vedi anche

* [Esercitazione 2: Creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
