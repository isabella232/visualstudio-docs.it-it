---
title: 'Procedura dettagliata: Inserire testo in un documento da un riquadro azioni'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c858cfbd2fb48aa850e395d74d7f03386ec8bc2f
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671859"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Procedura dettagliata: Inserire testo in un documento da un riquadro azioni
  Questa procedura dettagliata illustra come creare un riquadro azioni in un documento di Microsoft Office Word. Nel riquadro azioni contiene due controlli per la raccolta di input e quindi inviano il testo al documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Progettare un'interfaccia usando i controlli Windows Form in un controllo riquadro azioni.  
  
-   Visualizzare il riquadro azioni quando si apre l'applicazione.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Creare il progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto documento di Word con il nome **My Basic Actions Pane**. Nella procedura guidata, selezionare **creare un nuovo documento**. Per altre informazioni, vedere [procedura: progetti di Office di creare in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **My Basic Actions Pane** progetto al **Esplora soluzioni**.  
  
## <a name="add-text-and-bookmarks-to-the-document"></a>Aggiungere testo e i segnalibri nel documento  
 Nel riquadro azioni Invia testo ai segnalibri nel documento. Per progettare il documento, digitare un testo per creare un form di base.  
  
### <a name="to-add-text-to-your-document"></a>Per aggiungere testo al documento  
  
1. Digitare il testo seguente nel documento di Word:  
  
    **21 marzo 2008**  
  
    **Name**  
  
    **Indirizzo**  
  
    **Questo è un esempio di un riquadro azioni di base in Word.**  
  
   È possibile aggiungere un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento trascinandolo dal **della casella degli strumenti** in Visual Studio o utilizzando la **segnalibro** finestra di dialogo di Word.  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Per aggiungere un controllo Bookmark a un documento  
  
1.  Dal **controlli Word** scheda della finestra di **della casella degli strumenti**, trascinare un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento.  
  
     Il **Aggiungi controllo Bookmark** verrà visualizzata la finestra di dialogo.  
  
2.  Selezionare la parola **Name**senza selezionare il segno di paragrafo e fare clic su **OK**.  
  
    > [!NOTE]  
    >  Il segno di paragrafo deve essere di fuori del segnalibro. Se i segni di paragrafo non sono visibili nel documento, fare clic sui **degli strumenti** dal menu **strumenti di Microsoft Office Word** e quindi fare clic su **opzioni**. Fare clic sul **vista** scheda e selezionare il **segni di paragrafo** casella di controllo nel **segni di formattazione** sezione del **opzioni** nella finestra di dialogo.  
  
3.  Nel **delle proprietà** finestra Modifica il **nome** proprietà di **segnalibro1** a **showName**.  
  
4.  Selezionare la parola **indirizzo**, senza selezionare il segno di paragrafo.  
  
5.  Nel **inserire** della barra multifunzione, nella **collegamenti** fare clic su **segnalibro**.  
  
6.  Nel **segnalibro** finestra di dialogo, digitare **showAddress** nel **nome del segnalibro** casella e fare clic su **Aggiungi**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni  
 Per progettare l'interfaccia del riquadro azioni, aggiungere un controllo riquadro azioni per il progetto e quindi aggiungere i controlli Windows Form al controllo del riquadro azioni.  
  
### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni  
  
1.  Selezionare il **My Basic Actions Pane** del progetto **Esplora soluzioni**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo fare clic su **controllo del riquadro azioni**, denominare il controllo **InsertTextControl** e fare clic su **Aggiungi**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Per aggiungere controlli Windows Form al controllo del riquadro azioni  
  
1.  Se il controllo del riquadro azioni non è visibile nella finestra di progettazione, fare doppio clic su **InsertTextControl**.  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare un **etichetta** nel controllo del riquadro azioni.  
  
3.  Modifica il **testo** proprietà del controllo etichetta **nome**.  
  
4.  Aggiungere un **Textbox** al controllo del riquadro azioni e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**GetName**|  
    |**Dimensione**|**130, 20**|  
  
5.  Aggiungere un secondo **Label** al controllo del riquadro azioni e modificare le **testo** proprietà **indirizzo**.  
  
6.  Aggiungere una seconda **Textbox** al controllo del riquadro azioni e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**GetAddress**|  
    |**Accetta Return**|**True**|  
    |**Multiline**|**True**|  
    |**Dimensione**|**130, 40**|  
  
7.  Aggiungere un **pulsante** al controllo del riquadro azioni e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**addText**|  
    |**per**|**Inserisci**|  
  
## <a name="add-code-to-insert-text-into-the-document"></a>Aggiungere il codice per inserire il testo nel documento  
 Nel riquadro azioni, scrivere codice che inserisce il testo delle caselle di testo in appropriato <xref:Microsoft.Office.Tools.Word.Bookmark> controlli nel documento. È possibile usare il `Globals` classe per accedere ai controlli nel documento dai controlli del riquadro azioni. Per altre informazioni, vedere [globale accedere agli oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Per inserire il testo nel riquadro azioni in un segnalibro nel documento  
  
1.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del **addText** pulsante.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  In c#, è necessario aggiungere un gestore eventi per il clic del pulsante. È possibile inserire il codice nel `InsertTextControl` dopo la chiamata al costruttore `IntializeComponent`. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="add-code-to-show-the-actions-pane"></a>Aggiungere il codice per visualizzare il riquadro azioni  
 Per visualizzare il riquadro azioni, aggiungere il controllo che è stato creato all'insieme dei controlli.  
  
### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni  
  
1.  Creare una nuova istanza del controllo del riquadro azioni nel `ThisDocument` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Aggiungere il codice seguente per il <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore dell'evento di `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 Testare il documento per verificare che il riquadro azioni viene aperto quando il documento viene aperto e che il testo digitato in caselle di testo viene inserito nei segnalibri quando si fa clic sul pulsante.  
  
### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Verificare che il riquadro azioni sia visibile.  
  
3.  Digitare il nome e indirizzo nelle caselle di testo nel riquadro azioni e fare clic su **Inserisci**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Ecco alcune possibili attività successive:  
  
-   Creare un riquadro azioni in Excel. Per altre informazioni, vedere [procedura: aggiungere un riquadro azioni a cartelle di lavoro di Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).  
  
-   Associare dati a controlli in un riquadro azioni. Per altre informazioni, vedere [procedura dettagliata: associare dati a controlli in un riquadro azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Procedura: aggiungere un riquadro azioni ai documenti di Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: aggiungere un riquadro azioni a cartelle di lavoro di Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))   
 [Procedura: gestire il layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark (controllo)](../vsto/bookmark-control.md)  
  
  