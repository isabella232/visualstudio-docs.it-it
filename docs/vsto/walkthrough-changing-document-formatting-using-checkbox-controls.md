---
title: Modificare la formattazione del documento utilizzando i controlli CheckBox
description: Informazioni su come usare i controlli Windows Form in una personalizzazione a livello di documento per Microsoft Word per modificare la formattazione del testo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4d83fb8fad6de0c932d371f7f874cea0ff9a8f80
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958661"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Procedura dettagliata: modificare la formattazione del documento utilizzando i controlli CheckBox
  Questa procedura dettagliata illustra come usare i controlli Windows Form in una personalizzazione a livello di documento per Microsoft Office Word per modificare la formattazione del testo.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di testo e di un controllo al documento in un progetto a livello di documento in fase di progettazione.

- Formattazione del testo quando viene selezionata un'opzione.

  Per visualizzare il risultato come esempio completo, vedere l'esempio relativo ai controlli di Word in [esempi e procedure dettagliate per lo sviluppo di Office](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="create-a-new-project"></a>Creare un nuovo progetto

1. Creare un progetto di documento di Word con il nome **formattazione di Word**. Nella procedura guidata selezionare **Crea un nuovo documento**.

     Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il progetto **My Word Formatting** a **Esplora soluzioni**.

## <a name="add-text-and-controls-to-the-word-document"></a>Aggiungere testo e controlli al documento di Word
 Per questa procedura dettagliata, aggiungere tre caselle di controllo e un testo in un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento di Word. Le caselle di controllo presenteranno opzioni all'utente per la formattazione del testo.

### <a name="add-three-check-boxes"></a>Aggiungi tre caselle di controllo

1. Verificare che il documento sia aperto nella finestra di progettazione di Visual Studio.

2. Dalla scheda **controlli comuni** della **casella degli strumenti** trascinare il primo <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> controllo nel documento.

3. Nella finestra **Proprietà** modificare le seguenti proprietà:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyBoldFont**|
    |**Text**|**Grassetto**|

4. Premere **invio** per spostare il punto di inserimento sotto la prima casella di controllo.

5. Aggiungere una seconda casella di controllo al documento sotto la `ApplyBoldFont` casella di controllo e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyItalicFont**|
    |**Text**|**Corsivo**|

6. Premere **invio** per spostare il punto di inserimento sotto la seconda casella di controllo.

7. Aggiungere una terza casella di controllo al documento sotto la `ApplyItalicFont` casella di controllo e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyUnderlineFont**|
    |**Text**|**Sottolineato**|

### <a name="add-text-and-a-bookmark-control"></a>Aggiungere testo e un controllo segnalibro

1. Spostare il punto di inserimento sotto i controlli casella di controllo e digitare il testo seguente:

    **Fare clic su una casella di controllo per modificare la formattazione del testo.**

2. Dalla scheda **controlli Word** della **casella degli strumenti** trascinare un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo nel documento.

    Verrà visualizzata la finestra di dialogo **Aggiungi controllo Bookmark** .

3. Selezionare il testo aggiunto al documento e fare clic su **OK**.

    Un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo denominato **segnalibro1** viene aggiunto al testo selezionato nel documento.

4. Nella finestra **Proprietà** modificare il valore della proprietà **(Name)** in **fontText.**

   Scrivere quindi il codice per formattare il testo quando una casella di controllo viene selezionata o deselezionata.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formattare il testo quando una casella di controllo è selezionata o deselezionata
 Quando l'utente seleziona un'opzione di formattazione, modificare il formato del testo nel documento.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Modificare la formattazione quando si seleziona una casella di controllo

1. Fare clic con il pulsante destro del mouse su `ThisDocument` **Esplora soluzioni**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Solo per C#, aggiungere le costanti seguenti alla classe **ThisDocument** .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyBoldFont` controllo.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyItalicFont` controllo.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyUnderlineFont` controllo.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. In C# è necessario aggiungere i gestori eventi per le caselle di testo all' <xref:Microsoft.Office.Tools.Word.Document.Startup> evento. Per informazioni su come creare i gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare il documento per verificare che il testo sia formattato correttamente quando si seleziona o deseleziona una casella di controllo.

### <a name="test-your-document"></a>Testare il documento

1. Premere **F5** per eseguire il progetto.

2. Selezionare o deselezionare una casella di controllo.

3. Verificare che il testo sia formattato correttamente.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'uso delle caselle di controllo e la modifica a livello di codice dei documenti di Word. Ecco alcune possibili attività successive:

- Utilizzare un pulsante per popolare una casella di testo. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzare il testo in una casella di testo in un documento utilizzando un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Uso di pulsanti di opzione per selezionare gli stili del grafico. Per altre informazioni, vedere [procedura dettagliata: aggiornare un grafico in un documento usando i pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Vedi anche
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Procedure dettagliate e esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
