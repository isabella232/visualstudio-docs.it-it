---
title: Modificare la formattazione del foglio di lavoro usando i controlli CheckBox
description: Informazioni su come usare gli Office di sviluppo in Visual Studio creare e aggiungere codice al progetto.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0f3a543d99b5b701256f1f738d4d79721f96cc5f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025498"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Procedura dettagliata: Modificare la formattazione del foglio di lavoro usando i controlli CheckBox
  Questa procedura dettagliata illustra le nozioni di base sull'uso delle caselle di controllo in un foglio Microsoft Office Excel foglio di lavoro per modificare la formattazione. Si useranno gli Office di sviluppo in Visual Studio per creare e aggiungere codice al progetto. Per visualizzare il risultato come esempio completo, vedere l'esempio Excel controlli di esempio in Office di sviluppo [e procedure dettagliate.](../vsto/office-development-samples-and-walkthroughs.md)

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante questa procedura dettagliata, si apprenderà come:

- Aggiungere testo e controlli a un foglio di lavoro.

- Formattare il testo quando viene selezionata un'opzione.

- Testare il progetto.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 In questo passaggio si creerà un progetto Excel cartella di lavoro usando Visual Studio.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Excel cartella di lavoro con il nome **My Excel Formatting**. Assicurarsi che **l'opzione Crea un nuovo documento** sia selezionata. Per altre informazioni, [vedere Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella Excel cartella di lavoro nella finestra di progettazione e aggiunge il progetto My **Excel Formatting** **a Esplora soluzioni**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Aggiungere testo e controlli al foglio di lavoro
 Per questa procedura dettagliata sono necessari tre <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controlli e del testo in un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> .

### <a name="to-add-three-check-boxes"></a>Per aggiungere tre caselle di controllo

1. Verificare che la cartella di lavoro sia aperta nella Visual Studio e `Sheet1` che sia aperta.

2. Dalla scheda **Controlli comuni** della casella **degli strumenti** trascinare un controllo nella cella B2 o accanto a in <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> **Sheet1.** 

3. Scegliere **Finestra** Proprietà **dal** menu Visualizza.

4. Assicurarsi che **Checkbox1** sia visibile nella casella di riepilogo Nome oggetto della **finestra** Proprietà e modificare le proprietà seguenti:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyBoldFont**|
    |**Text**|**Grassetto**|

5. Trascinare una seconda casella di controllo nella cella **B4** o accanto a questa e modificare le proprietà seguenti:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyItalicFont**|
    |**Text**|**Corsivo**|

6. Trascinare una terza casella di controllo nella cella **B6** o nelle vicinanze e modificare le proprietà seguenti:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyUnderlineFont**|
    |**Text**|**Sottolineato**|

7. Selezionare tutti e tre i controlli casella di controllo tenendo premuto **CTRL.**

8. Nel gruppo Disponi della scheda Formato in Excel fare clic **su** Allinea e quindi su **Allinea a sinistra.**

     I tre controlli casella di controllo sono allineati sul lato sinistro, in corrispondenza della posizione del primo controllo selezionato.

     Successivamente, si trascina un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nel foglio di lavoro.

    > [!NOTE]
    > È anche possibile aggiungere il <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo **digitando textFont** nella **casella** Nome.

#### <a name="to-add-text-to-a-namedrange-control"></a>Per aggiungere testo a un controllo NamedRange

1. Dalla scheda **Excel controlli della** casella degli strumenti trascinare un controllo nella cella <xref:Microsoft.Office.Tools.Excel.NamedRange> **B9.**

2. Verificare che **$B $ 9** venga visualizzato nella casella di testo modificabile e che la cella **B9** sia selezionata. In caso contrario, fare clic sulla **cella B9** per selezionarla.

3. Fare clic su **OK**.

4. La **cella B9** diventa un intervallo denominato `NamedRange1` .

    Non è presente alcuna indicazione visibile nel foglio di lavoro, ma viene visualizzata nella casella Nome (sopra il foglio di lavoro a sinistra) quando `NamedRange1` è selezionata la cella  **B9.**

5. Assicurarsi che **NamedRange1** sia visibile nella casella di riepilogo Nome oggetto della **finestra** Proprietà e modificare le proprietà seguenti:

   |Proprietà|Valore|
   |--------------|-----------|
   |**Nome**|**textFont**|
   |**Value2**|**Fare clic su una casella di controllo per modificare la formattazione del testo.**|

   Scrivere quindi il codice per formattare il testo quando viene selezionata un'opzione.

## <a name="format-the-text-when-an-option-is-selected"></a>Formattare il testo quando viene selezionata un'opzione
 In questa sezione si scriverà il codice in modo che quando l'utente seleziona un'opzione di formattazione, il formato del testo nel foglio di lavoro viene modificato.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Per modificare la formattazione quando è selezionata una casella di controllo

1. Fare clic con il **pulsante destro del mouse su Sheet1**, quindi scegliere **Visualizza** codice dal menu di scelta rapida.

2. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyBoldFont` controllo:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet7":::

3. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyItalicFont` controllo:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet8":::

4. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyUnderlineFont` controllo:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet9":::

5. In C# è necessario aggiungere gestori eventi per le caselle di controllo <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> all'evento , come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori eventi in Office progetti](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare la cartella di lavoro per assicurarsi che il testo sia formattato correttamente quando si seleziona o si deseleziona una casella di controllo.

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Selezionare o deselezionare una casella di controllo.

3. Verificare che il testo sia formattato correttamente.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'uso delle caselle di controllo e sulla formattazione del testo Excel fogli di lavoro. Ecco alcune possibili attività successive:

- Distribuzione del progetto. Per altre informazioni, vedere [Distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Usare un pulsante per popolare una casella di testo. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare il testo in una casella di testo in](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)un foglio di lavoro usando un pulsante .

## <a name="see-also"></a>Vedi anche
- [Procedure dettagliate che usano Excel](../vsto/walkthroughs-using-excel.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Limitazioni dei controlli Windows Form nei Office documenti](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
