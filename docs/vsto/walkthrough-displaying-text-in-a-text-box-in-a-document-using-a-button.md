---
title: Visualizza il testo nella casella di testo nel documento usando il pulsante
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f3c467abcee8fb4faafd2da06ba261e7f3039fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328748"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Procedura dettagliata: visualizzare il testo in una casella di testo in un documento utilizzando un pulsante
  Questa procedura dettagliata illustra come usare i pulsanti e le caselle di testo in una personalizzazione a livello di documento per Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di controlli al documento di Word in un progetto a livello di documento in fase di progettazione.

- Popolamento di una casella di testo quando si fa clic su un pulsante.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di documento di Word con il **pulsante nome My Word**. Nella procedura guidata selezionare **Crea un nuovo documento**.

     Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il progetto di **pulsante Word** **Esplora soluzioni**.

## <a name="add-controls-to-the-word-document"></a>Aggiungere controlli al documento di Word
 I controlli dell'interfaccia utente sono costituiti da un pulsante e da una casella di testo nel documento di Word.

### <a name="to-add-a-button-and-a-text-box"></a>Per aggiungere un pulsante e una casella di testo

1. Verificare che il documento sia aperto nella finestra di progettazione di Visual Studio.

2. Dalla scheda **controlli comuni** della **casella degli strumenti**trascinare un <xref:Microsoft.Office.Tools.Word.Controls.TextBox> controllo nel documento.

   > [!NOTE]
   > In Word i controlli vengono rilasciati in linea con il testo per impostazione predefinita. È possibile modificare la modalità di inserimento dei controlli e degli oggetti forma modificando il valore predefinito nella scheda **modifica** della finestra di dialogo **Opzioni** di Word.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

4. Trovare **textBox1** nella casella di riepilogo a discesa finestra **Proprietà** e modificare la proprietà **Name** della casella di testo in **DisplayText**.

5. Trascinare un controllo **Button** nel documento e modificare le proprietà seguenti.

   |Proprietà|Valore|
   |--------------|-----------|
   |**Nome**|**insertText**|
   |**Text**|**Inserisci testo**|

   È ora possibile scrivere il codice che verrà eseguito quando si fa clic sul pulsante.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Popola la casella di testo quando si fa clic sul pulsante
 Ogni volta che l'utente fa clic sul pulsante **Hello World!** viene aggiunto alla casella di testo.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Per scrivere nella casella di testo quando si fa clic sul pulsante

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ThisDocument**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Aggiungere il codice seguente al gestore eventi <xref:System.Windows.Forms.Control.Click> del pulsante.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. In C# è necessario aggiungere un gestore eventi per il pulsante all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Test dell'applicazione
 È ora possibile testare il documento per assicurarsi che il messaggio **Hello World!** viene visualizzato nella casella di testo quando si fa clic sul pulsante.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Fare clic sul pulsante.

3. Confermare che **Hello World!** viene visualizzato nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra i concetti di base relativi all'uso di pulsanti e caselle di testo nei documenti di Word. Ecco alcune possibili attività successive:

- Uso di una casella combinata per modificare la formattazione. Per altre informazioni, vedere [procedura dettagliata: modificare la formattazione dei documenti mediante i controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Uso di pulsanti di opzione per selezionare gli stili del grafico. Per altre informazioni, vedere [procedura dettagliata: aggiornare un grafico in un documento usando i pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sui controlli Windows Forms nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Procedure dettagliate e esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Procedura: aggiungere controlli Windows Forms ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
