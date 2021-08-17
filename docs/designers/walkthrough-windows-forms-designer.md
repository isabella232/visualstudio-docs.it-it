---
title: Esercitazione di Progettazione Windows Form
description: Informazioni su come compilare un'app usando i vari strumenti forniti Windows Progettazione Form. L'app è un controllo personalizzato che usa molte funzionalità di layout disponibili.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: tutorial
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.openlocfilehash: 95c8d746e39fdf4c5536dd69028c5f246280ba5c76a51f69ee4c92eea21f52c3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452899"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>Esercitazione: Introduzione a Progettazione Windows Forms

Progettazione Windows Form fornisce molti strumenti per la creazione di applicazioni Windows Forms. Questo articolo illustra come creare un'app usando i vari strumenti forniti dalla finestra di progettazione, incluse le attività seguenti:

- Disporre i controlli usando le guide di allineamento.
- Eseguire le attività della finestra di progettazione usando gli smart tag.
- Impostare i margini e la spaziatura interna per i controlli.
- Disporre i controlli usando un controllo <xref:System.Windows.Forms.TableLayoutPanel>.
- Partizionare il layout del controllo usando un controllo <xref:System.Windows.Forms.SplitContainer>.
- Esplorare il layout con la finestra Struttura documento.
- Posizionare i controlli con la visualizzazione delle informazioni sulle dimensioni e sulla posizione.
- Impostare i valori delle proprietà usando la finestra Proprietà.

Al termine, si avrà un controllo personalizzato assemblato usando molte delle funzionalità di layout disponibili in Progettazione Windows Form. Questo controllo implementa l'interfaccia utente per una semplice calcolatrice. L'immagine seguente illustra il layout generale del controllo della calcolatrice:

![Presentazione guidata dell'interfaccia utente della calcolatrice](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Creare il progetto di controllo personalizzato

Il primo passaggio consiste nel creare il progetto di controllo DemoCalculator.

1. Aprire Visual Studio e creare un nuovo progetto **Libreria di controlli Windows Form**. Denominare il progetto **DemoCalculatorLib**.

   ::: moniker range=">=vs-2019"

   ![Modello della libreria di controlli Windows Forms in Visual Studio 2019](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Per rinominare il file, in **Esplora soluzioni** fare clic con il pulsante destro del mouse su **UserControl1.vb** o **UserControl1.cs,** scegliere **Rinomina** e modificare il nome del file in DemoCalculator.vb o DemoCalculator.cs. Selezionare il pulsante **Sì** quando richiesto per rinominare tutti i riferimenti all'elemento di codice "UserControl1".

Progettazione Windows Form mostra l'area di progettazione per il controllo DemoCalculator. In questa visualizzazione è possibile progettare graficamente l'aspetto del controllo selezionando i controlli e i componenti dalla casella degli strumenti e inserendoli nell'area di progettazione. Per altre informazioni sui controlli personalizzati, vedere [Tipi di controlli personalizzati](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Progettare il layout del controllo

Il controllo DemoCalculator contiene diversi controlli Windows Forms. In questa procedura si disporranno i controlli usando Progettazione Windows Form.

1. In Progettazione Windows Form ridimensionare il controllo DemoCalculator impostando dimensioni maggiori. A tale scopo, selezionare il quadratino di ridimensionamento nell'angolo in basso a destra e trascinarlo verso il basso e verso destra. Nell'angolo in basso a destra di Visual Studio sono disponibili le informazioni sulle dimensioni e sulla posizione per i controlli. Impostare la dimensione del controllo su larghezza 500 e altezza 400 osservando le informazioni sulle dimensioni durante il ridimensionamento del controllo.

2. Nella **casella degli strumenti** selezionare il nodo **Contenitori** per aprirlo. Selezionare il controllo **SplitContainer** e trascinarlo nell'area di progettazione.

   Il controllo `SplitContainer` viene inserito nell'area di progettazione del controllo DemoCalculator.

    > [!TIP]
    > Il controllo `SplitContainer` viene ridimensionato in modo da adattarsi alle dimensioni del controllo DemoCalculator. Osservare la finestra **Proprietà** per vedere le impostazioni delle proprietà per il controllo `SplitContainer`. Trovare la proprietà <xref:System.Windows.Forms.SplitContainer.Dock%2A>. Il valore è [DockStyle.Fill](xref:System.Windows.Forms.DockStyle.Fill), il che significa che il controllo `SplitContainer` verrà sempre ridimensionato in base ai limiti del controllo DemoCalculator. Ridimensionare il controllo DemoCalculator per verificare questo comportamento.

3. Nella finestra **Proprietà** impostare il valore della proprietà <xref:System.Windows.Forms.SplitContainer.Dock%2A> su `None`.

    Il controllo `SplitContainer` viene ridotto fino alle dimensioni predefinite e non segue più le dimensioni del controllo DemoCalculator.

4. Selezionare il glifo dello smart tag (![Glifo smart tag](media/smart-tag-glyph.gif)) nell'angolo superiore destro del controllo `SplitContainer`. Selezionare **Ancora nel contenitore padre** per impostare la proprietà `Dock` su `Fill`.

    Il controllo `SplitContainer` viene ancorato ai limiti del controllo DemoCalculator.

    > [!NOTE]
    > Diversi controlli offrono smart tag per facilitare la progettazione. Per altre informazioni, vedere [Procedura dettagliata: Eseguire attività comuni usando gli smart tag nei Windows Form.](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls)

5. Selezionare il bordo verticale tra i pannelli e trascinarlo a destra, in modo che la maggior parte dello spazio sia preso dal pannello sinistro.

    Il controllo `SplitContainer` divide il controllo DemoCalculator in due pannelli con un bordo mobile che li separa. Il pannello sinistro conterrà i pulsanti e la visualizzazione della calcolatrice e il pannello destro mostrerà un record delle operazioni aritmetiche eseguite dall'utente.

6. Nella finestra **Proprietà** impostare il valore della proprietà `BorderStyle` su `Fixed3D`.

7. Nella **casella degli strumenti** selezionare il nodo **Controlli comuni** per aprirlo. Selezionare il controllo `ListView` e trascinarlo nel pannello destro del controllo `SplitContainer`.

8. Selezionare il glifo smart tag del controllo `ListView`. Nel pannello smart tag modificare l'impostazione `View` in `Details`.

9. Nel pannello smart tag selezionare **Modifica colonne.**

   Verrà visualizzata la finestra di dialogo **Editor della raccolta ColumnHeader**.

10. Nella finestra di dialogo **Editor della raccolta ColumnHeader** selezionare **Aggiungi** per aggiungere una colonna al controllo `ListView`. Impostare il valore della proprietà `Text` della colonna su **Cronologia**. Selezionare **OK** per creare la colonna.

11. Nel pannello smart tag selezionare **Ancora nel contenitore padre** e quindi selezionare il glifo smart tag per chiudere il pannello smart tag.

12. Dalla **casella degli strumenti** del nodo **Contenitori** trascinare un controllo `TableLayoutPanel` nel pannello sinistro del controllo `SplitContainer`.

    Il controllo `TableLayoutPanel` viene visualizzato nell'area di progettazione con il relativo pannello smart tag aperto. Il controllo `TableLayoutPanel` dispone i relativi controlli figlio in una griglia. Il controllo `TableLayoutPanel` conterrà i pulsanti e la visualizzazione del controllo DemoCalculator. Per altre informazioni, vedere [Procedura dettagliata: Disporre i controlli usando tableLayoutPanel.](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel)

13. Selezionare **Modifica righe e colonne** nel pannello smart tag.

    Verrà visualizzata la finestra di dialogo **Stili di riga e colonna**.

14. Selezionare il pulsante **Aggiungi** finché non vengono visualizzate cinque colonne. Selezionare tutte e cinque le colonne e quindi selezionare **Percentuale** nella casella **Tipo dimensione**. Impostare il valore **Percentuale** su **20**. In questo modo, ogni colonna viene impostata sulla stessa larghezza.

15. In **Mostra** selezionare **Righe**.

16. Selezionare **Aggiungi** finché non vengono visualizzate cinque righe. Selezionare tutte e cinque le righe e quindi selezionare **Percentuale** nella casella **Tipo dimensione**. Impostare il valore **Percentuale** su **20**. In questo modo, ogni riga viene impostata sulla stessa altezza.

17. Selezionare **OK** per accettare le modifiche e quindi selezionare il glifo smart tag per chiudere il pannello smart tag.

18. Nella finestra **Proprietà** impostare il valore della proprietà `Dock` su `Fill`.

## <a name="populate-the-control"></a>Popolare il controllo

Ora che il layout del controllo è configurato, è possibile popolare il controllo DemoCalculator con i pulsanti e una visualizzazione.

1. Nella **Casella degli** strumenti selezionare l'icona del `TextBox` controllo.

   Un controllo `TextBox` viene inserito nella prima cella del controllo `TableLayoutPanel`.

2. Nella finestra **Proprietà** impostare il valore della proprietà ColumnSpan del controllo `TextBox` su **5**.

   Il controllo `TextBox` viene spostato in una posizione centrata nella relativa riga.

3. Impostare il valore della proprietà `Anchor` del controllo `TextBox` su `Left`, `Right`.

   Il controllo `TextBox` si espande orizzontalmente fino a coprire tutte e cinque colonne.

4. Modificare il valore della proprietà del controllo `TextBox` , `TextAlign` , su `Right`.

5. Nella finestra **Proprietà** espandere il nodo della proprietà `Font`. Impostare `Size` su **14** e impostare `Bold` su **true** per il controllo `TextBox`.

6. Selezionare il controllo `TableLayoutPanel`.

7. Nella **casella degli** strumenti selezionare l'icona `Button` .

   Un controllo `Button` viene inserito nella successiva cella aperta del controllo `TableLayoutPanel`.

8. Nella **Casella degli** strumenti selezionare `Button` l'icona altre quattro volte per popolare la seconda riga del `TableLayoutPanel` controllo.

9. Selezionare tutti e cinque i controlli `Button` selezionandoli tenendo premuto il tasto **MAIUSC**. Premere **CTRL** + **C** per copiare `Button` i controlli negli Appunti.

10. Premere **CTRL** + **V** tre volte per incollare copie `Button` dei controlli nelle righe rimanenti del `TableLayoutPanel` controllo.

11. Selezionare tutti e 20 i controlli `Button` selezionandoli tenendo premuto il tasto **MAIUSC**.

12. Nella finestra **Proprietà** impostare il valore della proprietà `Dock` su `Fill`.

    Tutti i controlli `Button` vengono ancorati per riempire le celle che li contengono.

13. Nella finestra **Proprietà** espandere il nodo della proprietà `Margin`. Impostare il valore di `All` su **5**.

    Le dimensioni di tutti i controlli `Button` vengono ridotte per creare un margine maggiore tra loro.

14. Selezionare **button10** e **button20** e quindi premere **Elimina** per rimuoverli dal layout.

15. Selezionare **button5** e **button15** e quindi impostare il valore della proprietà `RowSpan` su **2**. Questi saranno i pulsanti **Cancella** e **=** per il controllo DemoCalculator.

## <a name="use-the-document-outline-window"></a>Usare la finestra Struttura documento

Quando il controllo o il form viene popolato con diversi controlli, può risultare più semplice spostarsi nel layout con la finestra Struttura documento.

1. Sulla barra dei menu scegliere **Visualizza**  >  **altro Windows** struttura  >  **documento**.

   La finestra Struttura documento mostra una visualizzazione albero del controllo DemoCalculator e dei relativi controlli costitutivi. I controlli contenitore come `SplitContainer` visualizzano i relativi controlli figlio come sottonodi dell'albero. È anche possibile rinominare i controlli sul posto usando la finestra Struttura documento.

2. Nella finestra **Struttura documento fare** clic con il pulsante destro del mouse su **button1** e quindi scegliere **Rinomina**. Impostare il nome su sevenButton.

3. Usando la finestra **Struttura documento**, rinominare i controlli `Button` dal nome generato dalla finestra di progettazione al nome di produzione in base all'elenco seguente:

   - button1 in **sevenButton**

   - button2 in **eightButton**

   - button3 in **nineButton**

   - button4 in **divisionButton**

   - button5 in **clearButton**

   - button6 in **fourButton**

   - button7 in **fiveButton**

   - button8 in **sixButton**

   - button9 in **multiplicationButton**

   - button11 in **oneButton**

   - button12 in **twoButton**

   - button13 in **threeButton**

   - button14 in **subtractionButton**

   - button15 in **equalsButton**

   - button16 in **zeroButton**

   - button17 in **changeSignButton**

   - button18 in **decimalButton**

   - button19 in **additionButton**

4. Usando le finestre **Struttura documento** e **Proprietà**, modificare il valore della proprietà `Text` per ogni nome di controllo `Button` in base all'elenco seguente:

   - Impostare la proprietà Text del controllo sevenButton su **7**

   - Impostare la proprietà Text del controllo eightButton su **8**

   - Impostare la proprietà Text del controllo nineButton su **9**

   - Modificare la proprietà di testo del controllo divisionButton in **/** (barra)

   - Impostare la proprietà Text del controllo clearButton su **Cancella**

   - Impostare la proprietà Text del controllo fourButton su **4**

   - Impostare la proprietà Text del controllo fiveButton su **5**

   - Impostare la proprietà Text del controllo sixButton su **6**

   - Modificare la proprietà di testo del controllo multiplicationButton in **\*** (asterisco)

   - Impostare la proprietà Text del controllo oneButton su **1**

   - Impostare la proprietà Text del controllo twoButton su **2**

   - Impostare la proprietà Text del controllo threeButton su **3**

   - Modificare la proprietà di testo del controllo subtractionButton in **-** (trattino)

   - Modificare la proprietà text del controllo equalsButton in **=** (segno di uguale)

   - Impostare la proprietà Text del controllo zeroButton su **0**

   - Modificare la proprietà di testo del controllo changeSignButton in **+/-**

   - Impostare la proprietà Text del controllo decimalButton su **.** (punto)

   - Modificare la proprietà text del controllo additionButton in **+** (segno più)

5. Nell'area di progettazione selezionare tutti i controlli `Button` selezionandoli tenendo premuto il tasto **MAIUSC**.

6. Nella finestra **Proprietà** espandere il nodo della proprietà `Font`. Impostare `Size` su **14** e impostare `Bold` su **true** per tutti i controlli `Button`.

Questa operazione completa la progettazione del controllo DemoCalculator. Tutto ciò che rimane è fornire la logica della calcolatrice.

## <a name="implement-event-handlers"></a>Implementare i gestori eventi

I pulsanti del controllo DemoCalculator hanno gestori eventi che possono essere usati per implementare gran parte della logica della calcolatrice. La Windows Progettazione form consente di implementare gli stub di tutti i gestori eventi per tutti i pulsanti con una selezione.

1. Nell'area di progettazione selezionare tutti i controlli `Button` selezionandoli tenendo premuto il tasto **MAIUSC**.

2. Selezionare uno dei `Button` controlli.

   Viene aperto l'editor del codice per i gestori eventi generati dalla finestra di progettazione.

## <a name="test-the-control"></a>Testare il controllo

Poiché il controllo DemoCalculator eredita dalla classe <xref:System.Windows.Forms.UserControl>, è possibile testarne il comportamento con **UserControl Test Container**. Per altre informazioni, vedere Procedura: Testare il comportamento in fase di [esecuzione di un oggetto UserControl.](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol)

1. Premere **F5** per compilare ed eseguire il controllo DemoCalculator in **UserControl Test Container**.

2. Selezionare il bordo tra i pannelli `SplitContainer` e trascinarlo verso sinistra e verso destra. Il controllo `TableLayoutPanel` e tutti i relativi controlli figlio vengono ridimensionati per adattarsi allo spazio disponibile.

3. Al termine del test del controllo, selezionare **Chiudi**.

## <a name="use-the-control-on-a-form"></a>Usare il controllo in un form

Il controllo DemoCalculator può essere usato in altri controlli compositi o in un form. La procedura seguente descrive come usarlo.

### <a name="create-the-project"></a>Creare il progetto

Il primo passaggio consiste nel creare il progetto dell'applicazione. Questo progetto verrà usato per compilare l'applicazione che mostra il controllo personalizzato.

1. Creare un nuovo progetto di **Windows Forms Application** e denominarlo **DemoCalculatorTest**.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **DemoCalculatorTest** e quindi scegliere **Aggiungi riferimento** per aprire la finestra di dialogo **Aggiungi riferimento**.

3. Passare alla **scheda Progetti** e quindi selezionare il progetto DemoCalculatorLib per aggiungere il riferimento al progetto di test.

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **DemoCalculatorTest** e quindi scegliere **Imposta come progetto di avvio**.

5. In Progettazione Windows Form aumentare le dimensioni del form a circa **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Usare il controllo nel layout del form

Per usare il controllo DemoCalculator in un'applicazione, è necessario inserirlo in un form.

1. Nella **casella degli strumenti** espandere il nodo **Componenti DemoCalculatorLib**.

2. Trascinare il controllo **DemoCalculator** dalla **casella degli strumenti** nel form. Spostare il controllo nell'angolo superiore sinistro del form. Quando il controllo è vicino ai bordi del form, verranno visualizzate le *guide di allineamento*. Le guide di allineamento indicano la distanza della proprietà `Padding` del form e della proprietà `Margin` del controllo. Posizionare il controllo nella posizione indicata dalle guide di allineamento.

   Per altre informazioni, vedere [Procedura dettagliata: Disporre i controlli tramite guide di allineamento.](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines)

3. Trascinare un controllo `Button` dalla **casella degli strumenti** e rilasciarlo nel form.

4. Spostare il controllo `Button` vicino al controllo DemoCalculator e osservare dove vengono visualizzate le guide di allineamento. È possibile allineare i controlli in modo semplice e preciso usando questa funzionalità. Al termine, eliminare il controllo `Button`.

5. Fare clic con il pulsante destro del mouse sul controllo DemoCalculator e quindi **scegliere Proprietà**.

6. Impostare il valore della proprietà `Dock` su `Fill`.

7. Selezionare il form e quindi espandere il nodo della proprietà `Padding`. Impostare il valore di **Tutto** su **20**.

   Le dimensioni del controllo DemoCalculator vengono ridotte per contenere il nuovo valore `Padding` del form.

8. Ridimensionare il form trascinando i vari quadratini di ridimensionamento in posizioni diverse. Osservare come il controllo DemoCalculator viene ridimensionato per adattarsi alla posizione.

## <a name="next-steps"></a>Passaggi successivi

Questo articolo ha illustrato come costruire l'interfaccia utente per una semplice calcolatrice. Per continuare, è possibile estenderne la funzionalità implementando la logica della calcolatrice e quindi [pubblicare l'app usando ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). In alternativa, continuare con un'altra esercitazione in cui [si crea un visualizzatore di immagini con Windows Forms](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Vedi anche

- [Controlli Windows Form](/dotnet/framework/winforms/controls/)
- [Accessibilità per i controlli Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Pubblicare con ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
