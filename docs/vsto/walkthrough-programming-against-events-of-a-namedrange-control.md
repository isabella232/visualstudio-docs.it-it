---
title: 'Procedura dettagliata: programma per eventi di un controllo NamedRange'
description: Informazioni su come aggiungere un controllo NamedRange a un foglio di lavoro di Microsoft Excel e programmarlo in base agli eventi usando gli strumenti di sviluppo di Office in Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e311a567d32ee083bcc13f417c248f5f3d3ee5a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526123"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Procedura dettagliata: programma per eventi di un controllo NamedRange
  In questa procedura dettagliata viene illustrato come aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un foglio di lavoro di Excel Microsoft Office e programmarlo in base agli eventi utilizzando gli strumenti di sviluppo di Office in Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante questa procedura dettagliata, si apprenderà come:

- Aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un foglio di foglio.

- Programma per <xref:Microsoft.Office.Tools.Excel.NamedRange> gli eventi di controllo.

- Testare il progetto.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 In questo passaggio verrà creato un progetto di cartella di lavoro di Excel con Visual Studio.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di cartella di lavoro di Excel con il nome **eventi di intervallo denominato**. Assicurarsi che sia selezionata l'opzione **Crea un nuovo documento** . Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto **eventi di intervallo denominato** al **Esplora soluzioni**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Aggiungere testo e intervalli denominati al foglio di testo
 Poiché i controlli host sono oggetti estesi di Office, è possibile aggiungerli al documento nello stesso modo in cui si aggiunge l'oggetto nativo. Ad esempio, è possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo Excel a un foglio di lavoro aprendo il menu **Inserisci** , puntando a **nome** e scegliendo **Definisci**. È anche possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo trascinandoli dalla **casella degli strumenti** nel foglio di comando.

 In questo passaggio vengono aggiunti due controlli intervallo denominati al foglio di controllo utilizzando la **casella degli strumenti** e quindi viene aggiunto il testo al foglio di controllo.

### <a name="to-add-a-range-to-your-worksheet"></a>Per aggiungere un intervallo al foglio di lavoro

1. Verificare che la cartella di lavoro *Events.xlsxintervallo denominato* sia aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.

2. Dalla scheda **controlli Excel** della casella degli strumenti trascinare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella **a1** in `Sheet1` .

     Verrà visualizzata la finestra di dialogo **Aggiungi controllo NamedRange** .

3. Verificare che **$A $1** sia visualizzato nella casella di testo modificabile e che la cella **a1** sia selezionata. In caso contrario, fare clic sulla cella **a1** per selezionarla.

4. Fare clic su **OK**.

     La cella **a1** diventa un intervallo denominato `namedRange1` . Non è presente alcuna indicazione visibile sul foglio di lavori, ma `namedRange1` viene visualizzato nella casella **nome** (situata appena sopra il foglio di foglio a sinistra) quando si seleziona la cella **a1** .

5. Aggiungere un altro <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo alla cella **B3**.

6. Verificare che **$B $3** sia visualizzato nella casella di testo modificabile e che sia selezionata la cella **B3** . In caso contrario, fare clic sulla cella **B3** per selezionarla.

7. Fare clic su **OK**.

     La cella **B3** diventa un intervallo denominato `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Per aggiungere testo al foglio di lavoro

1. Nella cella **a1** Digitare il testo seguente:

    **Questo è un esempio di controllo NamedRange.**

2. Nella cella **a3** (a sinistra di `namedRange2` ) digitare il testo seguente:

    **Eventi**

   Nelle sezioni seguenti si scriverà codice che inserisce testo in `namedRange2` e modifica le proprietà del `namedRange2` controllo in risposta agli <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> eventi, e <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> di `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Aggiungere codice per rispondere all'evento BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Per inserire testo in NamedRange2 in base all'evento BeforeDoubleClick

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1. vb** o **Sheet1.cs** e selezionare **Visualizza codice**.

2. Aggiungere il codice `namedRange1_BeforeDoubleClick` in modo che il gestore dell'evento abbia un aspetto simile al seguente:

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. In C# è necessario aggiungere gestori eventi per l'intervallo denominato, come illustrato nell' <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento riportato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>Aggiungere codice per rispondere all'evento di modifica

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Per inserire il testo in namedRange2 in base all'evento di modifica

1. Aggiungere il codice `NamedRange1_Change` in modo che il gestore dell'evento abbia un aspetto simile al seguente:

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    > Poiché quando si fa doppio clic su una cella in un intervallo di Excel viene attivata la modalità di modifica, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> si verifica un evento quando la selezione viene spostata all'esterno dell'intervallo anche se non è stata apportata alcuna modifica al testo.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Aggiungere codice per rispondere all'evento SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Per inserire testo in namedRange2 in base all'evento SelectionChange

1. Aggiungere il codice in modo che il gestore dell'evento **NamedRange1_SelectionChange** abbia un aspetto simile al seguente:

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    > Poiché quando si fa doppio clic su una cella in un intervallo di Excel, la selezione viene spostata nell'intervallo, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> si verifica un evento prima che <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> si verifichi l'evento.

## <a name="test-the-application"></a>Test dell'applicazione
 A questo punto è possibile testare la cartella di lavoro per verificare che il testo che descrive gli eventi di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo venga inserito in un altro intervallo denominato quando vengono generati gli eventi.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Posizionare il cursore in `namedRange1` e verificare che il testo relativo all' <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> evento venga inserito e che nel foglio di lavoro venga inserito un commento.

3. Fare doppio clic all'interno di `namedRange1` e verificare che il testo relativo <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> agli eventi venga inserito con testo in corsivo in rosso `namedRange2` .

4. Fare clic all'esterno di `namedRange1` e notare che l'evento di modifica si verifica quando si esce dalla modalità di modifica anche se non è stata apportata alcuna modifica al testo.

5. Modificare il testo all'interno di `namedRange1` .

6. Fare clic all'esterno di `namedRange1` e verificare che il testo relativo all' <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> evento venga inserito con testo blu in `namedRange2` .

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base della programmazione rispetto agli eventi di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo. Ecco un'attività che può essere successiva:

- Distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Procedura: ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Procedura: aggiungere controlli NamedRange a fogli di foglio](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
