---
title: 'Procedura dettagliata: Modificare la formattazione dei documenti mediante controlli CheckBox'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a4ab82b47a69509ee151675d483ae5cff859d12d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871039"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Procedura dettagliata: Modificare la formattazione dei documenti mediante controlli CheckBox
  Questa procedura dettagliata illustra come usare i controlli Windows Form in una personalizzazione a livello di documento per Microsoft Office Word per modificare la formattazione del testo.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
- Aggiunta di testo e un controllo al documento in un progetto a livello di documento in fase di progettazione.  
  
- Quando si seleziona un'opzione di formattazione del testo.  
  
  Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli Word all'indirizzo [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Creare il progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
### <a name="create-a-new-project"></a>Creare un nuovo progetto  
  
1.  Creare un progetto documento di Word con il nome **formattazione in Word**. Nella procedura guidata, selezionare **creare un nuovo documento**.  
  
     Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **My Word Formatting** progetto al **Esplora soluzioni**.  
  
## <a name="add-text-and-controls-to-the-word-document"></a>Aggiungere testo e controlli al documento di Word  
 Per questa procedura dettagliata, aggiungere tre caselle di controllo e il testo in un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento di Word. Le caselle di controllo verranno visualizzate le opzioni per l'utente per la formattazione del testo.  
  
### <a name="add-three-check-boxes"></a>Aggiungere tre caselle di controllo  
  
1.  Verificare che il documento sia aperto nella finestra di progettazione di Visual Studio.  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare il primo <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> controllo al documento.  
  
3.  Nella finestra **Proprietà** modificare le seguenti proprietà:  
  
    |Proprietà|Value|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**per**|**Grassetto**|  
  
4.  Premere **invio** per posizionare il cursore sotto la prima casella di controllo.  
  
5.  Aggiungere una seconda casella di controllo al documento riportato di seguito il `ApplyBoldFont` casella di controllo e modificare le proprietà seguenti.  
  
    |Proprietà|Value|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**per**|**Corsivo**|  
  
6.  Premere **invio** per spostare il punto di inserimento seguente la seconda casella di controllo.  
  
7.  Aggiungere una terza casella di controllo al documento riportato di seguito il `ApplyItalicFont` casella di controllo e modificare le proprietà seguenti.  
  
    |Proprietà|Value|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**per**|**Carattere di sottolineatura**|  
  
### <a name="add-text-and-a-bookmark-control"></a>Aggiungere testo e un controllo Bookmark  
  
1. Spostare il punto di inserimento sotto i controlli casella di controllo e digitare il testo seguente:  
  
    **Fare clic su una casella di controllo per modificare la formattazione del testo.**  
  
2. Dal **controlli Word** scheda della finestra di **della casella degli strumenti**, trascinare un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento.  
  
    Il **Aggiungi controllo Bookmark** verrà visualizzata la finestra di dialogo.  
  
3. Selezionare il testo è stato aggiunto al documento e fare clic su **OK**.  
  
    Oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> controllo denominato **segnalibro1** viene aggiunto al testo selezionato nel documento.  
  
4. Nel **le proprietà** finestra, modificare il valore della **(nome)** proprietà **fontText.**  
  
   Successivamente, scrivere il codice per formattare il testo quando una casella di controllo è selezionata o deselezionata.  
  
## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formattare il testo quando viene selezionata o deselezionata una casella di controllo  
 Quando l'utente seleziona un'opzione di formattazione, modificare il formato del testo nel documento.  
  
### <a name="change-formatting-when-a-check-box-is-selected"></a>Modificare la formattazione quando è selezionata una casella di controllo  
  
1.  Fare doppio clic su `ThisDocument` nelle **Esplora soluzioni**, quindi fare clic su **Visualizza codice** menu di scelta rapida.  
  
2.  Per C# , aggiungere le seguenti costanti per il **ThisDocument** classe.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyBoldFont` casella di controllo.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyItalicFont` casella di controllo.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyUnderlineFont` casella di controllo.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  In C#, è necessario aggiungere i gestori eventi per le caselle di testo per il <xref:Microsoft.Office.Tools.Word.Document.Startup> evento. Per informazioni su come creare gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 È ora possibile testare il documento per verificare che il testo è formattato correttamente quando si seleziona o deseleziona una casella di controllo.  
  
### <a name="test-your-document"></a>Testare il documento  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Selezionare o deselezionare una casella di controllo.  
  
3.  Verificare che il testo è formattato correttamente.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base usando le caselle di controllo e a livello di programmazione cambiando il testo, formattazione nei documenti di Word. Ecco alcune possibili attività successive:  
  
-   Usare un pulsante per popolare una casella di testo. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare il testo in una casella di testo in un documento tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Uso di pulsanti di opzione per selezionare gli stili del grafico. Per altre informazioni, vedere [Procedura dettagliata: Aggiornare un grafico in un documento mediante pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  

## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
