---
title: Modificare la formattazione del documento usando i controlli CheckBox
description: Informazioni su come usare i Windows Form in una personalizzazione a livello di documento per Microsoft Word modificare la formattazione del testo.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e9f280b2e8db25788e89bdb66d9ec5455c7a1efe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032056"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Procedura dettagliata: Modificare la formattazione dei documenti usando i controlli CheckBox
  Questa procedura dettagliata illustra come usare i Windows Form in una personalizzazione a livello di documento per Microsoft Office Word per modificare la formattazione del testo.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di testo e di un controllo al documento in un progetto a livello di documento in fase di progettazione.

- Formattazione del testo quando viene selezionata un'opzione.

  Per visualizzare il risultato come esempio completato, vedere l'esempio di controlli Word Office esempi di [sviluppo e procedure dettagliate](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="create-a-new-project"></a>Creare un nuovo progetto

1. Creare un progetto Documento di Word con il nome **My Word Formatting**. Nella procedura guidata selezionare **Crea un nuovo documento**.

     Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **progetto My Word Formatting** a **Esplora soluzioni**.

## <a name="add-text-and-controls-to-the-word-document"></a>Aggiungere testo e controlli al documento di Word
 Per questa procedura dettagliata, aggiungere tre caselle di controllo e del testo in <xref:Microsoft.Office.Tools.Word.Bookmark> un controllo al documento di Word. Le caselle di controllo presenteranno all'utente le opzioni per la formattazione del testo.

### <a name="add-three-check-boxes"></a>Aggiungere tre caselle di controllo

1. Verificare che il documento sia aperto nella finestra di progettazione di Visual Studio.

2. Dalla scheda **Controlli comuni** della Casella **degli strumenti** trascinare il primo controllo <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> nel documento.

3. Nella finestra **Proprietà** modificare le seguenti proprietà:

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyBoldFont**|
    |**Text**|**Grassetto**|

4. Premere **INVIO** per spostare il punto di inserimento sotto la prima casella di controllo.

5. Aggiungere una seconda casella di controllo al documento sotto la `ApplyBoldFont` casella di controllo e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyItalicFont**|
    |**Text**|**Corsivo**|

6. Premere **INVIO** per spostare il punto di inserimento sotto la seconda casella di controllo.

7. Aggiungere una terza casella di controllo al documento sotto la `ApplyItalicFont` casella di controllo e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**applyUnderlineFont**|
    |**Text**|**Sottolineato**|

### <a name="add-text-and-a-bookmark-control"></a>Aggiungere testo e un controllo Segnalibro

1. Spostare il punto di inserimento sotto i controlli casella di controllo e digitare il testo seguente:

    **Fare clic su una casella di controllo per modificare la formattazione del testo.**

2. Dalla scheda **Controlli word** della Casella **degli strumenti** trascinare un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento.

    Verrà **visualizzata la finestra di** dialogo Aggiungi controllo segnalibro .

3. Selezionare il testo aggiunto al documento e fare clic su **OK.**

    Un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo denominato **Bookmark1** viene aggiunto al testo selezionato nel documento.

4. Nella finestra **Proprietà** modificare il valore della proprietà **(Name)** in **fontText.**

   Scrivere quindi il codice per formattare il testo quando una casella di controllo è selezionata o deselezionata.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formattare il testo quando una casella di controllo è selezionata o deselezionata
 Quando l'utente seleziona un'opzione di formattazione, modificare il formato del testo nel documento.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Modificare la formattazione quando viene selezionata una casella di controllo

1. Fare clic con il pulsante destro del Esplora soluzioni e quindi scegliere `ThisDocument` **Visualizza** codice dal menu di scelta rapida. 

2. Solo per C#, aggiungere le costanti seguenti alla **classe ThisDocument.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet2":::

3. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyBoldFont` controllo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet3":::

4. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyItalicFont` controllo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet4":::

5. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi della casella di `applyUnderlineFont` controllo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet5":::

6. In C# è necessario aggiungere gestori eventi per le caselle di testo <xref:Microsoft.Office.Tools.Word.Document.Startup> all'evento . Per informazioni su come creare gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare il documento per verificare che il testo sia formattato correttamente quando si seleziona o si deseleziona una casella di controllo.

### <a name="test-your-document"></a>Testare il documento

1. Premere **F5** per eseguire il progetto.

2. Selezionare o deselezionare una casella di controllo.

3. Verificare che il testo sia formattato correttamente.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'uso delle caselle di controllo e sulla modifica a livello di codice della formattazione del testo nei documenti di Word. Ecco alcune possibili attività successive:

- Usare un pulsante per popolare una casella di testo. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare il testo in una casella di testo in un documento usando un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Uso di pulsanti di opzione per selezionare gli stili del grafico. Per altre informazioni, vedere [Procedura dettagliata: Aggiornare un grafico in un documento usando i pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Vedi anche
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Office esempi di sviluppo e procedure dettagliate](../vsto/office-development-samples-and-walkthroughs.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Limitazioni dei controlli Windows Form nei Office documenti](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
