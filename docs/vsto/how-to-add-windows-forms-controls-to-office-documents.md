---
title: 'Procedura: aggiungere controlli Windows Form a documenti di Office'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b12d51ffe3a2e647a067b95d320e8beb70cac384
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547537"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Procedura: aggiungere controlli Windows Forms ai documenti di Office
  È possibile aggiungere controlli Windows Form a documenti di Microsoft Office Excel e Microsoft Office Word in fase di progettazione in progetti a livello di documento. In fase di esecuzione è possibile aggiungere controlli nelle personalizzazioni a livello di documento e nei componenti aggiuntivi VSTO. Ad esempio, è possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> controllo al foglio di lavoro in modo che gli utenti possano selezionare da un elenco di opzioni.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Questo argomento descrive le attività seguenti:

- [Aggiungere controlli in fase di progettazione](#designtime)

- [Aggiungere controlli in fase di esecuzione nei progetti a livello di documento](#runtimedoclevel)

- [Aggiungere controlli in fase di esecuzione nei componenti aggiuntivi VSTO](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Aggiungere controlli in fase di progettazione
 Sono disponibili varie modalità di aggiunta di controlli Windows Form al documento in un progetto a livello di documento in fase di progettazione.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Per trascinare un controllo Windows sul documento

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **controlli comuni** della **casella degli strumenti**fare clic sul controllo che si desidera aggiungere e trascinarlo nel documento.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Per trascinare un controllo Windows Form sul documento

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **controlli comuni** della **casella degli strumenti**fare clic sul controllo che si desidera aggiungere.

3. Nel documento fare clic sul punto in cui si vuole posizionare l'angolo superiore sinistro del controllo e trascinare fino al punto in cui si vuole posizionare l'angolo inferiore destro.

     Il controllo viene aggiunto al documento con la dimensione e la posizione specificate.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **= Embed ("WinForms. Control. host", "")**  nella barra della **Formula**. Questo testo è necessario e non deve essere eliminato.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Per aggiungere un controllo Windows al documento facendo un singolo clic sul controllo

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **controlli comuni** della **casella degli strumenti**fare clic sul controllo che si desidera aggiungere.

3. Nel documento fare clic nel punto in cui si vuole aggiungere il controllo.

     Il controllo viene aggiunto al documento con la dimensione predefinita.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Per aggiungere un controllo Windows al documento facendo un doppio clic sul controllo

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **controlli comuni** della **casella degli strumenti**fare doppio clic sul controllo che si desidera aggiungere.

     Il controllo viene aggiunto al documento al centro del documento o del riquadro attivo.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Per aggiungere un controllo Windows Forms al documento premendo il tasto invio

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **controlli comuni** della **casella degli strumenti**fare clic sul controllo che si desidera aggiungere e premere il tasto **invio** .

     Il controllo viene aggiunto al documento al centro del documento o del riquadro attivo.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Aggiungere controlli in fase di esecuzione nei progetti a livello di documento
 È possibile aggiungere controlli Windows Form a livello di codice a un documento in fase di esecuzione. In Word usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> della classe `ThisDocument`. In Excel usare i metodi della <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> proprietà di una classe `Sheet` *n* . Ogni metodo dispone di diversi overload per specificare in modi diversi il percorso del controllo.

 Quando si aggiunge un controllo Windows Form a un documento in fase di esecuzione, il controllo non viene reso persistente nel documento quando quest'ultimo viene chiuso. È possibile ricreare il controllo alla prossima apertura del documento. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Per aggiungere un controllo Windows Form in fase di esecuzione

1. Usare un metodo con il nome Add \<*control class*> (dove *classe del controllo* è il nome della classe del controllo Windows Forms che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     Nell'esempio di codice seguente viene illustrato come aggiungere un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.Button> alla cella **C5** di `Sheet1` in un progetto a livello di documento per Excel.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> Aggiungere controlli in fase di esecuzione nei componenti aggiuntivi VSTO
 È possibile aggiungere controlli Windows Form a livello di codice a qualsiasi documento aperto in fase di esecuzione. Generare innanzitutto un elemento host basato su un foglio di lavoro o un documento aperto. In Word usare quindi i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> del nuovo elemento host. In Excel usare i metodi della proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> del nuovo elemento host. Ogni metodo dispone di diversi overload per specificare in modi diversi il percorso del controllo.

 Quando si aggiunge un controllo Windows Form a un documento in fase di esecuzione, il controllo non viene reso persistente nel documento quando quest'ultimo viene chiuso. È possibile ricreare il controllo alla prossima apertura del documento. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Per altre informazioni sulla generazione di elementi host nei progetti di componente aggiuntivo VSTO, vedere [estendere i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Per aggiungere un controllo Windows Form in fase di esecuzione

1. Usare un metodo con il nome Add \<*control class*> (dove *classe del controllo* è il nome della classe del controllo Windows Forms che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > Nei progetti di componente aggiuntivo VSTO destinati [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a o versione successiva è necessario aggiungere un riferimento all'assembly *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* o *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* prima di poter accedere ai \<*control class*> metodi Add.

     L'esempio di codice seguente illustra come aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> al primo paragrafo del documento attivo mediante un componente aggiuntivo VSTO per Word.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sui controlli Windows Forms nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Procedura: ridimensionare i controlli all'interno di celle del foglio di comando](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
