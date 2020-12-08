---
title: Panoramica del riquadro azioni
description: Informazioni su come un riquadro azioni è un riquadro attività personalizzabile di azioni documento associato a una specifica Microsoft Office documento di Word o una cartella di lavoro di Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d03ba8968b08fb07eb2cc9c17839af57cf06eca
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844829"
---
# <a name="actions-pane-overview"></a>Panoramica del riquadro azioni
  Un riquadro azioni è un riquadro attività personalizzabile di **azioni documento** associato a una specifica Microsoft Office documento di Word o Microsoft Office cartella di lavoro di Excel. Il riquadro azioni è ospitato all'interno del riquadro attività di Office insieme ad altri riquadri attività incorporati, ad esempio il riquadro attività **origine XML** in Excel o il riquadro attività **stili e formattazione** in Word. È possibile usare controlli Windows Form o controlli WPF per progettare l'interfaccia utente del riquadro azioni.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile creare un riquadro azioni solo in una personalizzazione a livello di documento per Word o Excel. Non è possibile cerare un riquadro azioni in un componente aggiuntivo VSTO. Per ulteriori informazioni, vedere [funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Il riquadro azioni è diverso dai riquadri attività. I riquadri attività personalizzati sono associati all'applicazione e non a un documento specifico. È possibile creare riquadri attività personalizzati in componenti aggiuntivi VSTO per alcune applicazioni di Microsoft Office. Per ulteriori informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).

## <a name="display-the-actions-pane"></a>Visualizzare il riquadro azioni
 Il riquadro azioni è rappresentato dalla classe <xref:Microsoft.Office.Tools.ActionsPane>. Quando si crea un progetto a livello di documento, un'istanza di questa classe è disponibile per il codice usando il campo `ActionsPane` della classe `ThisWorkbook` (per Excel) o `ThisDocument` (per Word) nel progetto. Per visualizzare il riquadro azioni, aggiungere un controllo Windows Form alla proprietà <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> del campo `ActionsPane`. L'esempio di codice seguente aggiunge un controllo denominato `actions` al riquadro azioni.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Il riquadro azioni diventa visibile in fase di esecuzione non appena vi si aggiunge in modo esplicito un controllo. Dopo che il riquadro azioni viene visualizzato, è possibile aggiungere o rimuovere dinamicamente controlli in risposta alle azioni dell'utente. In genere, è necessario aggiungere il codice per visualizzare il riquadro azioni nel gestore eventi `Startup` di `ThisDocument` o `ThisWorkbook` in modo che il riquadro azioni sia visibile quando l'utente apre per la prima volta il documento. Potrebbe tuttavia essere necessario visualizzare il riquadro azioni solo in risposta all'azione di un utente nel documento. Ad esempio, è possibile aggiungere il codice all'evento `Click` di un controllo nel documento.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Aggiungere più controlli al riquadro azioni
 Quando si aggiungono più controlli al riquadro azioni, è necessario raggruppare i controlli in un controllo utente e quindi aggiungere il controllo utente alla <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> Proprietà. Questo processo include i due passaggi seguenti:

1. Creare l'interfaccia utente del riquadro azioni aggiungendo un **controllo del riquadro azioni** o un elemento del **controllo utente** al progetto. Entrambi questi elementi includono una classe <xref:System.Windows.Forms.UserControl> personalizzata di Windows Form. Il **controllo del riquadro azioni** e gli elementi del **controllo utente** sono equivalenti; l'unica differenza è il nome.

2. Aggiungere controlli Windows Form a <xref:System.Windows.Forms.UserControl> usando la finestra di progettazione o scrivendo codice.

   > [!NOTE]
   > È anche possibile aggiungere controlli WPF al riquadro azioni aggiungendo un oggetto <xref:System.Windows.Controls.UserControl> all'oggetto <xref:System.Windows.Forms.UserControl> di Windows Form. Per altre informazioni, vedere [usare i controlli WPF nelle soluzioni Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Aggiungere un'istanza del controllo utente personalizzato ai controlli contenuti nel campo `ActionsPane` della classe `ThisWorkbook` (per Excel) o `ThisDocument` (per Word) nel progetto.

   Per esempi che illustrano questo processo in modo più dettagliato, vedere [procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Nascondere il riquadro azioni
 Benché la classe <xref:Microsoft.Office.Tools.ActionsPane> includa un metodo <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> e una proprietà <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, non è possibile rimuovere il riquadro azioni dall'interfaccia utente usando membri della classe <xref:Microsoft.Office.Tools.ActionsPane> stessa. La chiamata al <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metodo o l'impostazione della <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> proprietà su **false** nasconde solo i controlli nel riquadro azioni e non nasconde il riquadro attività.

 Per nascondere il riquadro attività nella soluzione, sono disponibili diverse opzioni:

- Per Word, impostare la <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> proprietà dell' <xref:Microsoft.Office.Interop.Word.TaskPane> oggetto che rappresenta il riquadro attività azioni documento su **false**. L'esempio di codice seguente deve essere eseguito dalla classe `ThisDocument` nel progetto.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Per Excel, impostare la <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> proprietà dell' <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> oggetto su **false**. L'esempio di codice seguente deve essere eseguito dalla classe `ThisWorkbook` nel progetto.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Per Word o Excel, è possibile impostare in alternativa la <xref:Microsoft.Office.Core.CommandBar.Visible%2A> proprietà della barra dei comandi che rappresenta il riquadro attività su **false**. L'esempio di codice seguente deve essere eseguito dalla classe `ThisDocument` o `ThisWorkbook` nel progetto.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Cancella il riquadro azioni quando il documento viene aperto
 Quando un utente salva il documento mentre il riquadro azioni è visibile, il riquadro azioni è visibile ogni volta che viene aperto il documento, indipendentemente dal fatto che il riquadro azioni contenga controlli. Per controllare i momenti in cui viene visualizzato, chiamare il metodo <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> del campo `ActionsPane` nel gestore eventi `Startup` di `ThisDocument` o `ThisWorkbook` per fare in modo che il riquadro azioni non sia visibile all'apertura del documento.

### <a name="determine-when-the-actions-pane-is-closed"></a>Determinare quando il riquadro azioni viene chiuso
 Quando il riquadro azioni viene chiuso, non viene generato alcun evento. Benché la classe <xref:Microsoft.Office.Tools.ActionsPane> includa un evento <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, questo evento non viene generato quando l'utente finale chiude il riquadro azioni. Al contrario, questo evento viene generato quando i controlli nel riquadro azioni sono nascosti chiamando il <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metodo o impostando la <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> proprietà su **false**.

 Quando l'utente chiude il riquadro azioni, l'utente può visualizzarlo di nuovo eseguendo una delle procedure riportate di seguito nell'interfaccia utente dell'applicazione.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Per visualizzare il riquadro azioni usando l'interfaccia utente di Word o Excel

1. Sulla barra multifunzione fare clic sulla scheda **Visualizza** .

2. Nel gruppo **Mostra/Nascondi** fare clic sull'interruttore **azioni documento** .

## <a name="program-actions-pane-events"></a>Eventi del riquadro azioni programma
 È possibile aggiungere più controlli utente al riquadro azioni e quindi scrivere codice in risposta a eventi nel documento mostrando e nascondendo i controlli utente. Se si esegue il mapping di elementi XML Schema al documento, è possibile mostrare determinati controlli utente nel riquadro azioni ogni volta che il punto di inserimento si trova all'interno di uno degli elementi XML. Per altre informazioni, vedere [procedura: eseguire il mapping degli schemi ai documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) e [procedura: eseguire il mapping degli schemi ai fogli di dati all'interno di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 È anche possibile scrivere codice per rispondere agli eventi di qualsiasi oggetto, tra cui controlli host, applicazioni o eventi del documento. Per ulteriori informazioni, vedere [procedura dettagliata: programma per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Associare dati a controlli nel riquadro azioni
 I controlli nel riquadro azioni hanno le stesse caratteristiche di data binding di quelli in Windows Form. È possibile associare i controlli a origini dati come set di dati, set di dati tipizzati e XML. Per ulteriori informazioni, vedere [Data Binding e Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 È possibile associare controlli nel riquadro azioni e controlli nel documento allo stesso set di dati. Ad esempio, è possibile creare una relazione master/dettaglio tra i controlli nel riquadro azioni e i controlli nel foglio di lavoro. Per ulteriori informazioni, vedere [procedura dettagliata: associare dati a controlli in un riquadro azioni di Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

## <a name="validate-data-in-actions-pane-controls"></a>Convalida dei dati nei controlli del riquadro azioni
 Se si visualizza una finestra di messaggio nel gestore eventi <xref:System.Windows.Forms.Control.Validating> di un controllo nel riquadro azioni, l'evento potrebbe essere generato una seconda volta quando lo stato attivo passa dal controllo alla finestra di messaggio. Per evitare questo problema, usare un controllo <xref:System.Windows.Forms.ErrorProvider> per visualizzare eventuali messaggi di errore di convalida.

## <a name="user-control-stacking-order"></a>Ordine di sovrapposizione del controllo utente
 Se si usano più controlli utente, è possibile scrivere codice per sovrapporre correttamente i controlli utenti nel riquadro azioni, quando è ancorato in verticale o in orizzontale. È possibile impostare l'ordine di sovrapposizione nel riquadro azioni usando l'enumerazione <xref:Microsoft.Office.Tools.StackStyle> della proprietà <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Per altre informazioni, vedere [procedura: gestire il layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 La proprietà <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> può accettare i valori dell'enumerazione <xref:Microsoft.Office.Tools.StackStyle> seguenti.

|Stile di sovrapposizione|Definizione|
|--------------------|----------------|
|FromBottom|Sovrapposizione dal basso del riquadro azioni.|
|FromLeft|Sovrapposizione dal lato sinistro del riquadro azioni.|
|FromRight|Sovrapposizione dal lato destro del riquadro azioni.|
|FromTop|Sovrapposizione dall'alto del riquadro azioni.|
|Nessuno|Nessun ordine di sovrapposizione definito. L'ordine è controllato dallo sviluppatore.|

 Il codice seguente imposta la proprietà <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> per ordinare i controlli utente dall'alto del riquadro azioni.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Ancoraggi (controlli)
 Se l'utente ridimensiona il riquadro azioni in fase di esecuzione, i controlli possono essere ridimensionati insieme al riquadro azioni. È possibile usare la proprietà <xref:System.Windows.Forms.Control.Anchor%2A> di un controllo Windows Form per ancorare i controlli al riquadro azioni. È anche possibile ancorare i controlli Windows Form nel controllo utente allo stesso modo. Per altre informazioni, vedere [How to: Anchor Controls on Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Ridimensionare il riquadro azioni
 Non è possibile modificare direttamente le dimensioni di un oggetto <xref:Microsoft.Office.Tools.ActionsPane> perché <xref:Microsoft.Office.Tools.ActionsPane> è incorporato nel riquadro attività. È tuttavia modificare a livello di codice la larghezza del riquadro attività impostando la proprietà <xref:Microsoft.Office.Core.CommandBar.Width%2A> dell'oggetto <xref:Microsoft.Office.Core.CommandBar> che rappresenta il riquadro attività. È possibile modificare l'altezza del riquadro attività se è ancorato in orizzontale o se è mobile.

 Non è consigliabile ridimensionare a livello di codice il riquadro attività perché l'utente deve essere in grado di selezionare la dimensione del riquadro attività più adatta alle proprie esigenze. Tuttavia, se è necessario ridimensionare la larghezza del riquadro attività, è possibile usare il codice seguente a questo scopo.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Riposizionare il riquadro azioni
 Non è possibile riposizionare direttamente l'oggetto <xref:Microsoft.Office.Tools.ActionsPane> perché è incorporato nel riquadro attività. È tuttavia possibile spostare il riquadro attività a livello di codice impostando la proprietà <xref:Microsoft.Office.Core.CommandBar.Position%2A> dell'oggetto <xref:Microsoft.Office.Core.CommandBar> che rappresenta il riquadro attività.

 Il riposizionamento del riquadro attività a livello di codice non è consigliato perché l'utente deve essere in grado di scegliere la posizione del riquadro attività sullo schermo che meglio soddisfa le proprie esigenze. Tuttavia, se è necessario spostare il riquadro attività in una posizione specifica, è possibile usare il codice seguente a questo scopo.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Gli utenti finali possono riposizionare manualmente il riquadro attività in qualsiasi momento. Non esiste alcun modo per garantire che il riquadro attività resti ancorato nella posizione indicata a livello di codice. Tuttavia, è possibile controllare le modifiche di orientamento e garantire che i controlli nel riquadro azioni siano sovrapposti nella direzione corretta. Per altre informazioni, vedere [procedura: gestire il layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 L'impostazione <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> delle <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> proprietà e di <xref:Microsoft.Office.Tools.ActionsPane> non modifica la posizione perché l' <xref:Microsoft.Office.Tools.ActionsPane> oggetto è incorporato nel riquadro attività.

 Se il riquadro attività non è ancorato, è possibile impostare le proprietà <xref:Microsoft.Office.Core.CommandBar.Top%2A> e <xref:Microsoft.Office.Core.CommandBar.Left%2A> dell'oggetto <xref:Microsoft.Office.Core.CommandBar> che rappresenta il riquadro attività. Il codice seguente sposta un riquadro attività non ancorato nell'angolo superiore sinistro del documento.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>Vedi anche
- [Usare i controlli WPF nelle soluzioni Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura dettagliata: inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Procedura dettagliata: associare dati a controlli in un riquadro azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Procedura dettagliata: associare dati a controlli in un riquadro azioni di Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Procedura: gestire il layout di controllo nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Procedura dettagliata: inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
