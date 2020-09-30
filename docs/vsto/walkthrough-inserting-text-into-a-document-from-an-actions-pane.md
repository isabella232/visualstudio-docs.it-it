---
title: 'Procedura dettagliata: inserire testo in un documento da un riquadro azioni'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5c65027d7670c4d6789f32eb4d9080df061d904a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584963"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Procedura dettagliata: inserire testo in un documento da un riquadro azioni
  In questa procedura dettagliata viene illustrato come creare un riquadro azioni in un Microsoft Office documento di Word. Il riquadro azioni contiene due controlli che raccolgono l'input e quindi inviano il testo al documento.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Progettare un'interfaccia usando controlli Windows Forms in un controllo del riquadro azioni.

- Consente di visualizzare il riquadro azioni all'apertura dell'applicazione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di documento di Word con il nome **My Basic Actions pane**. Nella procedura guidata selezionare **Crea un nuovo documento**. Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il progetto **My Basic Actions pane** a **Esplora soluzioni**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Aggiungere testo e segnalibri al documento
 Il riquadro azioni invierà il testo ai segnalibri nel documento. Per progettare il documento, digitare un testo per creare un modulo di base.

### <a name="to-add-text-to-your-document"></a>Per aggiungere testo al documento

1. Digitare il testo seguente nel documento di Word:

    **21 marzo 2008**

    **Nome**

    **Indirizzo**

    **Questo è un esempio di un riquadro azioni di base in Word.**

   È possibile aggiungere un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento trascinandolo dalla **casella degli strumenti** in Visual Studio o usando la finestra di dialogo **segnalibro** in Word.

### <a name="to-add-a-bookmark-control-to-your-document"></a>Per aggiungere un controllo Bookmark al documento

1. Dalla scheda **controlli Word** della **casella degli strumenti**trascinare un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo nel documento.

     Verrà visualizzata la finestra di dialogo **Aggiungi controllo Bookmark** .

2. Selezionare il **nome**della parola, senza selezionare il segno di paragrafo, quindi fare clic su **OK**.

    > [!NOTE]
    > Il segno di paragrafo deve essere esterno al segnalibro. Se i segni di paragrafo non sono visibili nel documento, fare clic sul menu **strumenti** , scegliere **Microsoft Office strumenti di Word** , quindi fare clic su **Opzioni**. Fare clic sulla scheda **Visualizza** e selezionare la casella di controllo **segni di paragrafo** nella sezione **segni di formattazione** della finestra di dialogo **Opzioni** .

3. Nella finestra **Proprietà** modificare la proprietà **Name** di **segnalibro1** in **ShowName**.

4. Selezionare la parola **Indirizzo**senza selezionare il segno di paragrafo.

5. Nella scheda **Inserisci** della barra multifunzione fare clic su **segnalibro**nel gruppo **collegamenti** .

6. Nella finestra di dialogo **segnalibro** digitare **ShowAddress** nella casella **nome segnalibro** e fare clic su **Aggiungi**.

## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni
 Per progettare l'interfaccia del riquadro azioni, aggiungere un controllo riquadro azioni al progetto e quindi aggiungere Windows Forms controlli al controllo del riquadro azioni.

### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo del riquadro azioni

1. Selezionare il progetto **My Basic Actions pane** in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **controllo riquadro azioni**, denominare il controllo **InsertTextControl** e quindi fare clic su **Aggiungi**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Per aggiungere controlli Windows Form al controllo del riquadro azioni

1. Se il controllo riquadro azioni non è visibile nella finestra di progettazione, fare doppio clic su **InsertTextControl**.

2. Dalla scheda **controlli comuni** della **casella degli strumenti**trascinare un controllo **Label** nel controllo del riquadro azioni.

3. Modificare la proprietà **Text** del controllo Label in **Name**.

4. Aggiungere un controllo **TextBox** al controllo del riquadro azioni e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**getName**|
    |**Dimensione**|**130, 20**|

5. Aggiungere un secondo controllo **Label** al controllo del riquadro azioni e modificare la proprietà **Text** in **Address**.

6. Aggiungere un secondo controllo **TextBox** al controllo del riquadro azioni e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**getAddress**|
    |**Accetta la restituzione**|**True**|
    |**Multiline**|**True**|
    |**Dimensione**|**130, 40**|

7. Aggiungere un controllo **Button** al controllo del riquadro azioni e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**addText**|
    |**Text**|**Inserimento**|

## <a name="add-code-to-insert-text-into-the-document"></a>Aggiungere codice per inserire testo nel documento
 Nel riquadro azioni scrivere il codice che inserisce il testo dalle caselle di testo nei controlli appropriati del <xref:Microsoft.Office.Tools.Word.Bookmark> documento. È possibile utilizzare la `Globals` classe per accedere ai controlli del documento dai controlli del riquadro azioni. Per altre informazioni, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Per inserire testo dal riquadro azioni in un segnalibro nel documento

1. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi del pulsante **addText** .

     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]

2. In C# è necessario aggiungere un gestore eventi per il clic sul pulsante. È possibile inserire questo codice nel `InsertTextControl` Costruttore dopo la chiamata a `InitializeComponent` . Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]

## <a name="add-code-to-show-the-actions-pane"></a>Aggiungere codice per visualizzare il riquadro azioni
 Per visualizzare il riquadro azioni, aggiungere il controllo creato alla raccolta di controlli.

### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni

1. Creare una nuova istanza del controllo del riquadro azioni nella `ThisDocument` classe.

     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]

2. Aggiungere il codice seguente al <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore eventi di `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]

## <a name="test-the-application"></a>Test dell'applicazione
 Testare il documento per verificare che il riquadro azioni venga visualizzato quando il documento viene aperto e che il testo digitato nelle caselle di testo viene inserito nei segnalibri quando si fa clic sul pulsante.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Verificare che il riquadro azioni sia visibile.

3. Digitare il nome e l'indirizzo nelle caselle di testo nel riquadro azioni, quindi fare clic su **Inserisci**.

## <a name="next-steps"></a>Passaggi successivi
 Ecco alcune possibili attività successive:

- Creare un riquadro azioni in Excel. Per altre informazioni, vedere [procedura: aggiungere un riquadro azioni alle cartelle di lavoro di Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

- Associare dati a controlli in un riquadro azioni. Per ulteriori informazioni, vedere [procedura dettagliata: associare dati a controlli in un riquadro azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura: aggiungere un riquadro azioni alle cartelle di lavoro di Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Procedura: gestire il layout di controllo nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Segnalibro (controllo)](../vsto/bookmark-control.md)
