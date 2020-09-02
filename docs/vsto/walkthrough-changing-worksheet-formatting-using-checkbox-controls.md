---
title: Modificare la formattazione del foglio di controllo tramite i controlli CheckBox
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 42d2c46f6fd61d74476933cfda3dea8c62b00c95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328694"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Procedura dettagliata: modificare la formattazione del foglio di controllo tramite i controlli CheckBox
  Questa procedura dettagliata illustra le nozioni di base sull'uso di caselle di controllo in un foglio di lavoro Microsoft Office Excel per modificare la formattazione. Per creare e aggiungere codice al progetto, si utilizzeranno gli strumenti di sviluppo di Office in Visual Studio. Per visualizzare il risultato come esempio completo, vedere l'esempio relativo ai controlli di Excel in [esempi e procedure dettagliate per lo sviluppo di Office](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante questa procedura dettagliata, si apprenderà come:

- Aggiungere testo e controlli a un foglio di foglio.

- Formattare il testo quando viene selezionata un'opzione.

- Testare il progetto.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 In questo passaggio verrà creato un progetto di cartella di lavoro di Excel usando Visual Studio.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di cartella di lavoro di Excel con il nome **formattazione di Excel**. Assicurarsi che sia selezionata l'opzione **Crea un nuovo documento** . Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto di **formattazione Excel** a **Esplora soluzioni**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Aggiungere testo e controlli al foglio di controllo
 Per questa procedura dettagliata sono necessari tre <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controlli e un testo in un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo.

### <a name="to-add-three-check-boxes"></a>Per aggiungere tre caselle di controllo

1. Verificare che la cartella di lavoro sia aperta nella finestra di progettazione di Visual Studio e che `Sheet1` sia aperta.

2. Dalla scheda **controlli comuni** della **casella degli strumenti**trascinare un <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controllo nella cella **B2** o vicino alla cella **Sheet1**B2.

3. Scegliere finestra **Proprietà** dal menu **Visualizza** .

4. Assicurarsi che **CheckBox1** sia visibile nella casella di riepilogo nome oggetto della finestra **Proprietà** e modificare le proprietà seguenti:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyBoldFont**|
    |**Text**|**Grassetto**|

5. Trascinare una seconda casella di controllo in prossimità della cella **B4** e modificare le proprietà seguenti:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyItalicFont**|
    |**Text**|**Corsivo**|

6. Trascinare una terza casella di controllo nella cella **B6** e modificare le proprietà seguenti:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyUnderlineFont**|
    |**Text**|**Sottolineare**|

7. Selezionare tutti e tre i controlli casella di controllo tenendo premuto il tasto **CTRL** .

8. Nel gruppo Disponi della scheda formato in Excel fare clic su **Allinea**, quindi fare clic su **Allinea a sinistra**.

     I tre controlli casella di controllo sono allineati sul lato sinistro, nella posizione del primo controllo selezionato.

     Successivamente, trascinare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nel foglio di controllo.

    > [!NOTE]
    > È anche possibile aggiungere il <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo digitando **FontTesto** nella casella **nome** .

#### <a name="to-add-text-to-a-namedrange-control"></a>Per aggiungere testo a un controllo NamedRange

1. Dalla scheda **controlli Excel** della casella degli strumenti trascinare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella **B9**.

2. Verificare che **$B $9** sia visualizzato nella casella di testo modificabile e che la cella **B9** sia selezionata. In caso contrario, fare clic su cella **B9** per selezionarlo.

3. Fare clic su **OK**.

4. La cella **B9** diventa un intervallo denominato `NamedRange1` .

    Non è presente alcuna indicazione visibile sul foglio di lavori, ma `NamedRange1` viene visualizzato nella **casella nome** (appena sopra il foglio di foglio a sinistra) quando si seleziona cella **B9** .

5. Assicurarsi che **NamedRange1** sia visibile nella casella di riepilogo nome oggetto della finestra **Proprietà** e modificare le proprietà seguenti:

   |Proprietà|Valore|
   |--------------|-----------|
   |**Nome**|**FontTesto**|
   |**Value2**|**Fare clic su una casella di controllo per modificare la formattazione del testo.**|

   Quindi, scrivere il codice per formattare il testo quando viene selezionata un'opzione.

## <a name="format-the-text-when-an-option-is-selected"></a>Formattare il testo quando viene selezionata un'opzione
 In questa sezione si scriverà il codice in modo che, quando l'utente seleziona un'opzione di formattazione, il formato del testo nel foglio di testo venga modificato.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Per modificare la formattazione quando si seleziona una casella di controllo

1. Fare clic con il pulsante destro del mouse su **Sheet1**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyBoldFont` controllo:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyItalicFont` controllo:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyUnderlineFont` controllo:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. In C# è necessario aggiungere i gestori eventi per le caselle di controllo all' <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Test dell'applicazione
 È ora possibile testare la cartella di lavoro per verificare che il testo sia formattato correttamente quando si seleziona o deseleziona una casella di controllo.

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Selezionare o deselezionare una casella di controllo.

3. Verificare che il testo sia formattato correttamente.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'uso di caselle di controllo e formattazione del testo nei fogli di lavoro di Excel. Ecco alcune possibili attività successive:

- Distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Usare un pulsante per popolare una casella di testo. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzare il testo in una casella di testo di un foglio di un foglio di testo utilizzando un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Vedere anche
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
