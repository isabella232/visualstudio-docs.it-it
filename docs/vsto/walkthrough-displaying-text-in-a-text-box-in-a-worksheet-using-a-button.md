---
title: Visualizzare il testo nella casella di testo nel foglio di lavoro usando il pulsante
description: Informazioni di base sull'uso di pulsanti e caselle di testo nei fogli di lavoro di Microsoft Excel. Creare anche progetti Excel usando gli strumenti di sviluppo di Office in Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1209bf903f5a5b9c0005d9ba4ba6a891752aedd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827786"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Procedura dettagliata: Visualizzare il testo in una casella di testo in un foglio di lavoro usando un pulsante
  Questa procedura dettagliata illustra le nozioni di base sull'uso di pulsanti e caselle di testo Microsoft Office fogli di lavoro di Excel e come creare progetti di Excel usando gli strumenti di sviluppo di Office in Visual Studio. Per visualizzare il risultato come esempio completato, vedere l'esempio di controlli Excel in Esempi e procedure dettagliate per lo sviluppo [di Office.](../vsto/office-development-samples-and-walkthroughs.md)

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante questa procedura dettagliata, si apprenderà come:

- Aggiungere controlli a un foglio di lavoro.

- Popolare una casella di testo quando si fa clic su un pulsante.

- Testare il progetto.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 In questo passaggio si creerà un progetto Cartella di lavoro di Excel usando Visual Studio.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Cartella di lavoro di Excel con il **nome My Excel Button**. Assicurarsi che **l'opzione Crea un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto **My Excel Button** a **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro
 Per questa procedura dettagliata sono necessari un pulsante e una casella di testo nel primo foglio di lavoro.

### <a name="to-add-a-button-and-a-text-box"></a>Per aggiungere un pulsante e una casella di testo

1. Verificare che la **cartella di lavoro My Excel Button.xlsx** sia aperta nella finestra Visual Studio designer, con `Sheet1` visualizzata.

2. Dalla scheda **Controlli comuni** della Casella degli strumenti trascinare un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> in `Sheet1` .

3. Scegliere **Finestra** Proprietà **dal** menu Visualizza .

4. Assicurarsi che **TextBox1 sia**  visibile nella casella di riepilogo a discesa della finestra Proprietà e modificare la proprietà **Name** della casella di testo in **displayText**.

5. Trascinare **un controllo** Pulsante in e modificare le proprietà `Sheet1` seguenti:

   |Proprietà|Valore|
   |--------------|-----------|
   |**Nome**|**insertText**|
   |**Text**|**Inserisci testo**|

   Scrivere ora il codice da eseguire quando si fa clic sul pulsante.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Popolare la casella di testo quando si fa clic sul pulsante
 Ogni volta che l'utente fa clic sul **pulsante, Hello World!** viene aggiunto alla casella di testo.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Per scrivere nella casella di testo quando si fa clic sul pulsante

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **su Sheet1**, quindi scegliere **Visualizza** codice dal menu di scelta rapida.

2. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi del pulsante:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet11":::

3. In C# è necessario aggiungere un gestore eventi all'evento , <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, [vedere Procedura: Creare gestori eventi nei progetti di Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet12":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare la cartella di lavoro per assicurarsi che il messaggio **Hello World.** viene visualizzato nella casella di testo quando si fa clic sul pulsante.

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Fare clic sul pulsante.

3. Verificare che **sia Hello World.** viene visualizzato nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'uso di pulsanti e caselle di testo nei fogli di lavoro di Excel. Ecco alcune possibili attività successive:

- Distribuzione del progetto. Per altre informazioni, vedere [Distribuire una soluzione Office.](../vsto/deploying-an-office-solution.md)

- Uso delle caselle di controllo per modificare la formattazione. Per altre informazioni, vedere Procedura [dettagliata: Modificare la formattazione del foglio di lavoro usando i controlli CheckBox.](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere controlli Windows Forms ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
- [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
