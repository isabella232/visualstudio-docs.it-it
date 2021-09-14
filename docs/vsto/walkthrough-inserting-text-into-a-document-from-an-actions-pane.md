---
title: 'Procedura dettagliata: Inserire testo in un documento da un riquadro azioni'
description: Creare un riquadro azioni in un Microsoft Word documento. Informazioni sul fatto che il riquadro azioni contiene due controlli che raccolgono l'input e quindi inviano il testo al documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 071f447e8f32d53feef912b6c804af27fe69aa1e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710040"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Procedura dettagliata: Inserire testo in un documento da un riquadro azioni
  Questa procedura dettagliata illustra come creare un riquadro azioni in un documento Microsoft Office Word. Il riquadro azioni contiene due controlli che raccolgono l'input e quindi inviano il testo al documento.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Progettare un'interfaccia usando Windows form personalizzati in un controllo riquadro azioni.

- Visualizzare il riquadro azioni all'apertura dell'applicazione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Documento di Word con il nome **My Basic Actions Pane**. Nella procedura guidata selezionare **Crea un nuovo documento.** Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il progetto **Riquadro** azioni di base a **Esplora soluzioni**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Aggiungere testo e segnalibri al documento
 Il riquadro azioni invierà testo ai segnalibri nel documento. Per progettare il documento, digitare del testo per creare un modulo di base.

### <a name="to-add-text-to-your-document"></a>Per aggiungere testo al documento

1. Digitare il testo seguente nel documento di Word:

    **21 marzo 2008**

    **Nome**

    **Indirizzo**

    **Questo è un esempio di riquadro azioni di base in Word.**

   È possibile aggiungere un controllo al documento trascinandolo dalla Casella degli strumenti in Visual Studio o usando la finestra di dialogo <xref:Microsoft.Office.Tools.Word.Bookmark> Segnalibro in  Word. 

### <a name="to-add-a-bookmark-control-to-your-document"></a>Per aggiungere un controllo Bookmark al documento

1. Dalla scheda **Controlli word** della casella **degli strumenti** trascinare un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento.

     Verrà **visualizzata la finestra di dialogo** Aggiungi controllo Segnalibro .

2. Selezionare la parola **Nome** senza selezionare il segno di paragrafo e fare clic su **OK.**

    > [!NOTE]
    > Il segno di paragrafo deve essere esterno al segnalibro. Se i segni di paragrafo non sono visibili nel documento, fare clic sul **menu** Strumenti , scegliere Microsoft Office **Word Tools** e quindi fare clic su **Opzioni**. Fare clic **sulla scheda** Visualizza e selezionare la casella **di controllo** Segni di paragrafo nella **sezione Contrassegni** di formattazione della **finestra di dialogo** Opzioni.

3. Nella finestra **Proprietà** modificare la proprietà **Name** di **Bookmark1** in **showName.**

4. Selezionare la parola **Indirizzo** senza selezionare il segno di paragrafo.

5. Nel gruppo **Collegamenti** della scheda Inserisci della barra multifunzione **fare** clic su **Segnalibro.**

6. Nella finestra **di dialogo** Segnalibro digitare **showAddress** nella casella **Nome** segnalibro e fare clic su **Aggiungi**.

## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni
 Per progettare l'interfaccia del riquadro azioni, aggiungere un controllo riquadro azioni al progetto e quindi aggiungere Windows form al controllo riquadro azioni.

### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni

1. Selezionare il **progetto Riquadro azioni di** base in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo elemento** fare clic su Controllo riquadro **azioni**, assegnare al controllo il nome **InsertTextControl e** fare clic su **Aggiungi**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Per aggiungere Windows form al controllo riquadro azioni

1. Se il controllo riquadro azioni non è visibile nella finestra di progettazione, fare doppio clic **su InsertTextControl**.

2. Dalla scheda **Controlli comuni** della casella degli **strumenti** trascinare un **controllo Etichetta** nel controllo riquadro azioni.

3. Modificare la **proprietà Text** del controllo Etichetta in **Name**.

4. Aggiungere un **controllo Textbox** al controllo riquadro azioni e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**Getname**|
    |**Size**|**130, 20**|

5. Aggiungere un secondo **controllo Etichetta** al controllo riquadro azioni e modificare la **proprietà Text** in **Address**.

6. Aggiungere un secondo **controllo Textbox** al controllo riquadro azioni e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**getAddress**|
    |**Accetta valori restituiti**|**True**|
    |**Multiline**|**True**|
    |**Size**|**130, 40**|

7. Aggiungere un **controllo** Pulsante al controllo riquadro azioni e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**addText**|
    |**Text**|**Inserimento**|

## <a name="add-code-to-insert-text-into-the-document"></a>Aggiungere il codice per inserire testo nel documento
 Nel riquadro azioni scrivere il codice che inserisce il testo dalle caselle di testo nei controlli <xref:Microsoft.Office.Tools.Word.Bookmark> appropriati nel documento. È possibile usare la `Globals` classe per accedere ai controlli nel documento dai controlli nel riquadro azioni. Per altre informazioni, vedere [Accesso globale agli oggetti in Office progetti](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Per inserire testo dal riquadro azioni in un segnalibro nel documento

1. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi del pulsante **addText.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb" id="Snippet8":::

2. In C# è necessario aggiungere un gestore eventi per il clic sul pulsante. È possibile inserire questo codice nel `InsertTextControl` costruttore dopo la chiamata a `InitializeComponent` . Per informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori eventi in Office progetti](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet9":::

## <a name="add-code-to-show-the-actions-pane"></a>Aggiungere il codice per visualizzare il riquadro azioni
 Per visualizzare il riquadro azioni, aggiungere il controllo creato all'insieme dei controlli.

### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni

1. Creare una nuova istanza del controllo riquadro azioni nella `ThisDocument` classe .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet10":::

2. Aggiungere il codice seguente al <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore eventi di `ThisDocument` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet11":::

## <a name="test-the-application"></a>Testare l'applicazione
 Testare il documento per verificare che il riquadro azioni si apra all'apertura del documento e che il testo digitato nelle caselle di testo sia inserito nei segnalibri quando si fa clic sul pulsante.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Verificare che il riquadro azioni sia visibile.

3. Digitare il nome e l'indirizzo nelle caselle di testo del riquadro azioni e fare clic su **Inserisci.**

## <a name="next-steps"></a>Passaggi successivi
 Ecco alcune possibili attività successive:

- Creare un riquadro azioni in Excel. Per altre informazioni, vedere [Procedura: Aggiungere un riquadro azioni a](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))Excel cartelle di lavoro.

- Associare dati ai controlli in un riquadro azioni. Per altre informazioni, vedere [Procedura dettagliata: Associare dati a controlli in un riquadro azioni di Word.](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
- [Procedura: Aggiungere un riquadro azioni a documenti di Word o Excel cartelle di lavoro](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura: Aggiungere un riquadro azioni alle cartelle di lavoro Excel lavoro](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Procedura: Gestire il layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Controllo Bookmark](../vsto/bookmark-control.md)
