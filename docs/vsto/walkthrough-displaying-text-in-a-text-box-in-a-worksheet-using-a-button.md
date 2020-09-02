---
title: Visualizza il testo in una casella di testo nel foglio di utilizzo con il pulsante
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b30eea0152b75cdd0869ececac674ee5aeee7933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328714"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Procedura dettagliata: visualizzare il testo in una casella di testo di un foglio di testo utilizzando un pulsante
  Questa procedura dettagliata illustra le nozioni di base sull'uso di pulsanti e caselle di testo in Microsoft Office fogli di lavoro di Excel e su come creare progetti Excel usando gli strumenti di sviluppo di Office in Visual Studio. Per visualizzare il risultato come esempio completo, vedere l'esempio relativo ai controlli di Excel in [esempi e procedure dettagliate per lo sviluppo di Office](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante questa procedura dettagliata, si apprenderà come:

- Aggiungere controlli a un foglio di foglio.

- Inserire una casella di testo quando si fa clic su un pulsante.

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

1. Creare un progetto di cartella di lavoro di Excel con il **pulsante nome My Excel**. Assicurarsi che sia selezionata l'opzione **Crea un nuovo documento** . Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto di **pulsante Excel** a **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di controllo
 Per questa procedura dettagliata sono necessari un pulsante e una casella di testo nel primo foglio di foglio.

### <a name="to-add-a-button-and-a-text-box"></a>Per aggiungere un pulsante e una casella di testo

1. Verificare che la cartella di lavoro di **Excel Button.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.

2. Dalla scheda **controlli comuni** della casella degli strumenti trascinare un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> in `Sheet1` .

3. Scegliere **finestra Proprietà**dal menu **Visualizza** .

4. Assicurarsi che **textBox1** sia visibile nella casella di riepilogo a discesa finestra **Proprietà** e modificare la proprietà **Name** della casella di testo in **DisplayText**.

5. Trascinare un controllo **Button** su `Sheet1` e modificare le proprietà seguenti:

   |Proprietà|Valore|
   |--------------|-----------|
   |**Nome**|**insertText**|
   |**Text**|**Inserisci testo**|

   A questo punto, scrivere il codice da eseguire quando si fa clic sul pulsante.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Popola la casella di testo quando si fa clic sul pulsante
 Ogni volta che l'utente fa clic sul pulsante **Hello World!** viene accodato alla casella di testo.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Per scrivere nella casella di testo quando si fa clic sul pulsante

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **Sheet1**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi del pulsante:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. In C# è necessario aggiungere un gestore eventi all'evento, <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>Test dell'applicazione
 È ora possibile testare la cartella di lavoro per verificare che il messaggio **Hello World!** viene visualizzato nella casella di testo quando si fa clic sul pulsante.

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Fare clic sul pulsante.

3. Confermare che **Hello World!** viene visualizzato nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'uso di pulsanti e caselle di testo in fogli di lavoro di Excel. Ecco alcune possibili attività successive:

- Distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).

- Utilizzare le caselle di controllo per modificare la formattazione. Per altre informazioni, vedere [procedura dettagliata: modificare la formattazione del foglio di controllo tramite i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: aggiungere controlli Windows Forms ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
- [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
