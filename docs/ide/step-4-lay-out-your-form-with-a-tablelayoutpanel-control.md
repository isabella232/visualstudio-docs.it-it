---
title: 'Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7083a8874b699716d834ea69ba88c30225acec88
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926112"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel
In questo passaggio si aggiunge un controllo <xref:System.Windows.Forms.TableLayoutPanel> al form. TableLayoutPanel consente di allineare in modo corretto i controlli nel form che si aggiungerà successivamente.

 ![Collegamento a video](../data-tools/media/playvideo.gif)Per una versione video di questo argomento, vedere [Esercitazione 1: Creare un visualizzatore di immagini in Visual Basic - Video 2](http://go.microsoft.com/fwlink/?LinkId=205211) o [Esercitazione 1: Creare un visualizzatore immagini in C# - Video 2](http://go.microsoft.com/fwlink/?LinkId=205200). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.

## <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Per creare il layout del form con un controllo TableLayoutPanel

1.  Sul lato sinistro dell'IDE di Visual Studio individuare la scheda **Casella degli strumenti**. Scegliere la scheda **Casella degli strumenti**. Verrà visualizzata la **casella degli strumenti**. In alternativa, scegliere **Visualizza** > **Casella degli strumenti** sulla barra dei menu.

2.  Scegliere il piccolo simbolo del triangolo accanto al gruppo **Contenitori** per aprirlo, come mostrato nell'immagine seguente.

     ![Gruppo Contenitori](../ide/media/express_toolbox.png)
Gruppo **Contenitori**

3.  È possibile aggiungere al form controlli quali pulsanti, caselle di controllo ed etichette. Fare doppio clic sul controllo TableLayoutPanel nella **casella degli strumenti**. In alternativa, è possibile trascinare il controllo dalla casella degli strumenti al form. Quando si esegue questa operazione, l'IDE aggiunge un controllo TableLayoutPanel al modulo, come mostrato nell'immagine seguente.

     ![Controllo TableLayoutPanel](../ide/media/express_formtablelayout.png)
Controllo **TableLayoutPanel**

    > [!NOTE]
    >  Dopo aver aggiunto il controllo TableLayoutPanel, se nel form viene visualizzata una finestra con il titolo **Attività di TableLayoutPanel**, fare clic in qualsiasi punto all'interno del form per chiuderla. Verranno fornite ulteriori informazioni su questa finestra più avanti nell'esercitazione.

     Si noti che la **casella degli strumenti** si espande per coprire il modulo quando si fa clic sulla relativa scheda e si chiude quando si fa clic in un punto esterno. Si tratta della funzionalità Nascondi automaticamente dell'IDE. È possibile attivarla o disattivarla e bloccare in posizione qualsiasi finestra facendo clic sull'icona a forma di puntina da disegno nell'angolo superiore destro della finestra. L'icona a forma di puntina da disegno ha l'aspetto seguente.

     ![Icona della puntina da disegno](../ide/media/express_pushpintoolbox.png)
Icona della **puntina da disegno**

4.  Verificare che sia selezionato il controllo TableLayoutPanel facendo clic su di esso. È possibile verificare il controllo selezionato osservando l'elenco a discesa nella parte superiore della finestra **Proprietà**, come mostrato nell'immagine seguente.

     ![Finestra Proprietà con il controllo TableLayoutPanel](../ide/media/express_controlspropwin.png)
Finestra **Proprietà** con il controllo **TableLayoutPanel**

5.  Scegliere il pulsante **Alfabetico** nella barra degli strumenti nella finestra **Proprietà**. In questo modo, l'elenco delle proprietà nella finestra **Proprietà** viene visualizzato in ordine alfabetico per semplificare l'individuazione delle proprietà in questa esercitazione.

6.  Il selettore dei controlli è un elenco a discesa che si trova nella parte superiore della finestra **Proprietà**. In questo esempio è selezionato un controllo denominato `tableLayoutPanel1`. È possibile selezionare i controlli scegliendo un'area in **Progettazione Windows Form** o selezionandoli dal selettore dei controlli. Dopo aver selezionato TableLayoutPanel, individuare la relativa proprietà **Dock** e scegliere **Dock**, il cui valore dovrebbe essere impostato su **Nessuno**. Si noti che viene visualizzata una freccia a discesa accanto al valore. Fare clic sulla freccia, quindi selezionare il pulsante **Riempimento** (il pulsante grande al centro), come mostrato nell'immagine seguente.

     ![Finestra Proprietà con Riempimento selezionato](../ide/media/express_docktable.png)
Finestra **Proprietà** con **Riempimento** selezionato

     Il termine *ancoraggio* in Visual Studio indica l'associazione di una finestra un'altra finestra o area nell'IDE. Ad esempio, la finestra **Proprietà** può essere non ancorata, ovvero non collegata e mobile all'interno di Visual Studio, oppure può essere ancorata a **Esplora soluzioni**.

7.  Dopo aver impostato la proprietà **Dock** di TableLayoutPanel su **Fill**, il pannello riempie l'intero form. Se si ridimensiona nuovamente il form, TableLayoutPanel resta ancorato e viene ridimensionato correttamente.

    > [!NOTE]
    >  Un controllo TableLayoutPanel funziona come una tabella di Microsoft Office Word: dispone di righe e colonne e una singola cella può estendersi su più righe e colonne. Ogni cella può contenere un controllo (come un pulsante, una casella di controllo o un'etichetta). TableLayoutPanel avrà un controllo <xref:System.Windows.Forms.PictureBox> che si estende sull'intera riga superiore, un controllo <xref:System.Windows.Forms.CheckBox> nella cella inferiore sinistra e quattro controlli <xref:System.Windows.Forms.Button> nella cella inferiore destra.

8.  Attualmente, TableLayoutPanel dispone di due righe delle stesse dimensioni e di due colonne delle stesse dimensioni. È necessario ridimensionarle in modo che la riga superiore e la colonna a destra siano entrambe molto più grandi. In **Progettazione Windows Form** selezionare il controllo TableLayoutPanel. Nell'angolo superiore destro si trova un piccolo pulsante a forma di triangolo nero, illustrato di seguito.

     ![Pulsante triangolare](../ide/media/express_iconblacktriangle.gif)
Pulsante **triangolare**

     Questo pulsante indica che il controllo dispone di attività che consentono di impostare automaticamente le proprietà.

9. Scegliere il triangolo per visualizzare l'elenco attività del controllo, come mostrato nell'immagine seguente.

     ![Attività di TableLayoutPanel ](../ide/media/express_tablepanel.png)
Attività di **TableLayoutPanel**

10. Scegliere l'attività **Modifica righe e colonne** per visualizzare la finestra **Stili di riga e colonna**. Scegliere **Column1** e impostarne le dimensioni sul 15%, assicurandosi che il pulsante **Percentuale** sia selezionato e immettendo **15** nella casella **Percentuale**. Si tratta di un controllo <xref:System.Windows.Forms.NumericUpDown> che verrà usato in un'esercitazione successiva. Scegliere **Column2** e impostarla su 85%. Non scegliere ancora il pulsante **OK** per non chiudere la finestra. Se tuttavia si fa clic su OK, è possibile riaprire la finestra utilizzando l'elenco attività.

     ![Stili di riga e colonna di TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)
Stili di riga e colonna di **TableLayoutPanel**

11. Dall'elenco a discesa **Mostra** nella parte superiore della finestra scegliere **Righe**. Impostare **Row1** su 90% e **Row2** su 10%.

12. Fare clic sul pulsante **OK** . Il controllo TableLayoutPanel dispone ora di una riga grande nella parte superiore, una riga piccola nella parte inferiore, una colonna piccola a sinistra e una colonna grande a destra. È possibile ridimensionare righe e colonne in TableLayoutPanel scegliendo **tableLayoutPanel1** nel modulo e trascinando quindi i bordi di righe e colonne.

     ![Form1 con TableLayoutPanel ridimensionato](../ide/media/vs_formafterlayoutpanel.png)
**Form1** con **TableLayoutPanel** ridimensionato

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

-   Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 5: Aggiungere controlli al modulo](../ide/step-5-add-controls-to-your-form.md).

-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 3: Impostare le proprietà del modulo](../ide/step-3-set-your-form-properties.md).
