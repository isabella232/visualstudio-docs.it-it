---
title: 'Procedura: Aggiungere controlli Windows form personalizzati a Office documenti'
description: Informazioni su come aggiungere controlli Form Windows a Microsoft Office Excel e Microsoft Office documenti di Word in fase di progettazione nei progetti a livello di documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 11d5efde772a85681f21fc8b08586f014d96978d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026278"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Procedura: Aggiungere controlli form Windows a Office documenti
  È possibile aggiungere controlli Windows Form a documenti di Microsoft Office Excel e Microsoft Office Word in fase di progettazione in progetti a livello di documento. In fase di esecuzione è possibile aggiungere controlli nelle personalizzazioni a livello di documento e VSTO componenti aggiuntivi. Ad esempio, è possibile aggiungere un controllo al foglio di lavoro <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> in modo che gli utenti possano eseguire la selezione da un elenco di opzioni.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Questo argomento descrive le attività seguenti:

- [Aggiungere controlli in fase di progettazione](#designtime)

- [Aggiungere controlli in fase di esecuzione nei progetti a livello di documento](#runtimedoclevel)

- [Aggiungere controlli in fase di VSTO componenti aggiuntivi](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Aggiungere controlli in fase di progettazione
 Sono disponibili varie modalità di aggiunta di controlli Windows Form al documento in un progetto a livello di documento in fase di progettazione.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Per trascinare un controllo Windows sul documento

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **Controlli comuni** della casella **degli strumenti** fare clic sul controllo da aggiungere e trascinarlo nel documento.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Per trascinare un controllo Windows Form sul documento

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **Controlli comuni** della casella **degli strumenti** fare clic sul controllo da aggiungere.

3. Nel documento fare clic sul punto in cui si vuole posizionare l'angolo superiore sinistro del controllo e trascinare fino al punto in cui si vuole posizionare l'angolo inferiore destro.

     Il controllo viene aggiunto al documento con la dimensione e la posizione specificate.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, nella barra della **formula** verrà visualizzato **=EMBED("WinForms.Control.Host","").** Questo testo è necessario e non deve essere eliminato.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Per aggiungere un controllo Windows al documento facendo un singolo clic sul controllo

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **Controlli comuni** della casella **degli strumenti** fare clic sul controllo da aggiungere

3. Nel documento fare clic nel punto in cui si vuole aggiungere il controllo.

     Il controllo viene aggiunto al documento con la dimensione predefinita.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Per aggiungere un controllo Windows al documento facendo un doppio clic sul controllo

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **Controlli comuni** della casella **degli strumenti** fare doppio clic sul controllo da aggiungere.

     Il controllo viene aggiunto al documento al centro del documento o del riquadro attivo.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Per aggiungere un Windows Form al documento premendo INVIO

1. Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione. Per informazioni sulla creazione di progetti, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nella scheda **Controlli comuni** della casella **degli strumenti** fare clic sul controllo da aggiungere e premere **INVIO.**

     Il controllo viene aggiunto al documento al centro del documento o del riquadro attivo.

    > [!NOTE]
    > Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Aggiungere controlli in fase di esecuzione nei progetti a livello di documento
 È possibile aggiungere controlli Windows Form a livello di codice a un documento in fase di esecuzione. In Word usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> della classe `ThisDocument`. In Excel usare i metodi della <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> proprietà di una classe `Sheet` *n.* Ogni metodo dispone di diversi overload per specificare in modi diversi il percorso del controllo.

 Quando si aggiunge un controllo Windows Form a un documento in fase di esecuzione, il controllo non viene reso persistente nel documento quando quest'ultimo viene chiuso. È possibile ricreare il controllo alla prossima apertura del documento. Per altre informazioni, vedere [Aggiungere controlli a Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Per aggiungere un controllo Windows Form in fase di esecuzione

1. Usare un metodo con il nome Add (dove control class è il nome della classe del controllo Windows Forms che si vuole \<*control class*> aggiungere, ad esempio  <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     Nell'esempio di codice seguente viene illustrato come aggiungere <xref:Microsoft.Office.Tools.Excel.Controls.Button> un oggetto alla cella **C5** di in un progetto a livello di `Sheet1` documento per Excel.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet4":::

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a>Aggiungere controlli in fase di VSTO componenti aggiuntivi
 È possibile aggiungere controlli Windows Form a livello di codice a qualsiasi documento aperto in fase di esecuzione. Generare innanzitutto un elemento host basato su un foglio di lavoro o un documento aperto. In Word usare quindi i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> del nuovo elemento host. In Excel usare i metodi della proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> del nuovo elemento host. Ogni metodo dispone di diversi overload per specificare in modi diversi il percorso del controllo.

 Quando si aggiunge un controllo Windows Form a un documento in fase di esecuzione, il controllo non viene reso persistente nel documento quando quest'ultimo viene chiuso. È possibile ricreare il controllo alla prossima apertura del documento. Per altre informazioni, vedere [Aggiungere controlli a Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Per altre informazioni sulla generazione di elementi host nei progetti di componente aggiuntivo VSTO, vedere Estendere documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di [esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Per aggiungere un controllo Windows Form in fase di esecuzione

1. Usare un metodo con il nome Add (dove control class è il nome della classe del controllo Windows Forms che si vuole \<*control class*> aggiungere, ad esempio  <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > In VSTO progetti di componente aggiuntivo che hanno come destinazione o versioni successive, è necessario aggiungere un riferimento all'assemblyMicrosoft.Office.Tools.Excel.v4.0.Utilities.dlloMicrosoft.Office.Tools.Word.v4.0.Utilities.dllprima di poter accedere ai [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] metodi   \<*control class*> Add.

     L'esempio di codice seguente illustra come aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> al primo paragrafo del documento attivo mediante un componente aggiuntivo VSTO per Word.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet7":::

## <a name="see-also"></a>Vedi anche
- [Windows Panoramica dei controlli form Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Procedura: Ridimensionare i controlli all'interno delle celle del foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
