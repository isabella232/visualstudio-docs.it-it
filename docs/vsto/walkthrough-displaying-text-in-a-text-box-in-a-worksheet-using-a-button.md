---
title: Visualizzare il testo nella casella di testo nel foglio di lavoro usando il pulsante
description: Informazioni di base sull'uso di pulsanti e caselle di testo Microsoft Excel fogli di lavoro. Creare anche Excel progetti usando Office di sviluppo in Visual Studio.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d909db152521749a21ff418c004756d2b77e0b43
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031913"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Procedura dettagliata: Visualizzare il testo in una casella di testo in un foglio di lavoro usando un pulsante
  Questa procedura dettagliata illustra le nozioni di base sull'uso di pulsanti e caselle di testo Microsoft Office Excel fogli di lavoro e come creare progetti Excel usando Office di sviluppo in Visual Studio. Per visualizzare il risultato come un esempio completato, vedere l'esempio Excel Controls all'indirizzo Office esempi di sviluppo [e procedure dettagliate.](../vsto/office-development-samples-and-walkthroughs.md)

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
 In questo passaggio si creerà un progetto Excel workbook usando Visual Studio.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un Excel cartella di lavoro con il nome **My Excel Button**. Assicurarsi che **l'opzione Crea un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella Excel cartella di lavoro nella finestra di progettazione e aggiunge il progetto **My Excel Button** a **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro
 Per questa procedura dettagliata sono necessari un pulsante e una casella di testo nel primo foglio di lavoro.

### <a name="to-add-a-button-and-a-text-box"></a>Per aggiungere un pulsante e una casella di testo

1. Verificare che la **cartella di lavoro My Excel Button.xlsx** sia aperta nella finestra Visual Studio designer, con `Sheet1` visualizzata.

2. Dalla scheda **Controlli comuni** della Casella degli strumenti trascinare un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> in `Sheet1` .

3. Scegliere **Finestra** Proprietà **dal** menu Visualizza .

4. Assicurarsi che **TextBox1** sia visibile nella casella **di** riepilogo a discesa della finestra Proprietà e modificare la proprietà **Name** della casella di testo **in displayText**.

5. Trascinare **un controllo** Button in e modificare le proprietà `Sheet1` seguenti:

   |Proprietà|Valore|
   |--------------|-----------|
   |**Nome**|**insertText**|
   |**Text**|**Inserisci testo**|

   Scrivere ora il codice da eseguire quando si fa clic sul pulsante.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Popolare la casella di testo quando si fa clic sul pulsante
 Ogni volta che l'utente fa clic sul pulsante, **Hello World!** viene aggiunto alla casella di testo.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Per scrivere nella casella di testo quando si fa clic sul pulsante

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su Sheet1** e quindi scegliere **Visualizza** codice dal menu di scelta rapida.

2. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi del pulsante:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet11":::

3. In C# è necessario aggiungere un gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> all'evento come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet12":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare la cartella di lavoro per assicurarsi che il messaggio **Hello World.** viene visualizzato nella casella di testo quando si fa clic sul pulsante .

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Fare clic sul pulsante.

3. Verificare che **Hello World!** viene visualizzato nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'uso di pulsanti e caselle di testo Excel fogli di lavoro. Ecco alcune possibili attività successive:

- Distribuzione del progetto. Per altre informazioni, vedere [Deploy an Office solution](../vsto/deploying-an-office-solution.md).

- Uso delle caselle di controllo per modificare la formattazione. Per altre informazioni, vedere Procedura [dettagliata: Modificare la formattazione del foglio di lavoro usando i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere controlli Windows Form per Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
- [Limitazioni dei controlli Windows Form nei Office documenti](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
