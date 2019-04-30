---
title: Aggiungere controlli ai documenti di Office in fase di esecuzione
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6159a7763176be236b925dce9fae66e5fc915682
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440394"
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Aggiungere controlli ai documenti di Office in fase di esecuzione
  È possibile aggiungere controlli a un documento di Microsoft Office Word e di una cartella di lavoro di Microsoft Office Excel in fase di esecuzione. È inoltre possibile rimuoverli in fase di esecuzione. I controlli che si aggiunge o rimuove in fase di esecuzione sono noti *controlli dinamici*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 In questo argomento viene illustrato quanto segue:

- [Gestire i controlli in fase di esecuzione usando raccolte di controlli](#ControlsCollection).

- [Aggiungere controlli host ai documenti](#HostControls).

- [Aggiungere controlli Windows Form ai documenti](#WindowsForms).

  ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Aggiungere controlli all'area di documento in fase di esecuzione? ](http://go.microsoft.com/fwlink/?LinkId=132782).

## <a name="ControlsCollection"></a> Gestire i controlli in fase di esecuzione usando raccolte di controlli
 Per aggiungere, ottenere o rimuovere i controlli in fase di esecuzione, utilizzare i metodi di supporto di <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> oggetti.

 La modalità di accesso a questi oggetti dipende dal tipo di progetto che si sta sviluppando:

- In un progetto a livello di documento per Excel, usare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> delle classi `Sheet1`, `Sheet2`e `Sheet3` . Per altre informazioni su queste classi, vedere [elemento host Worksheet](../vsto/worksheet-host-item.md).

- In un progetto a livello di documento per Word, usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> della classe `ThisDocument` . Per altre informazioni su questa classe, vedere [elemento host Document](../vsto/document-host-item.md).

- In un progetto di componente aggiuntivo VSTO per Excel o Word, usare il `Controls` proprietà di un <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> generato in fase di esecuzione. Per altre informazioni sulla generazione di questi oggetti in fase di esecuzione, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="add-controls"></a>Aggiungere controlli
 I tipi <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> includono metodi di supporto che è possibile usare per aggiungere controlli host e controlli Windows Form comuni a documenti e fogli di lavoro. Il nome di ciascun metodo presenta il formato `Add`*classe del controllo*, dove *classe del controllo* rappresenta il nome del controllo che si desidera aggiungere. Ad esempio, per aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> al documento, usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> .

 Nell'esempio di codice seguente viene aggiunto un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un oggetto `Sheet1` di un progetto a livello di documento per Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Controlli di accesso e delete
 È possibile usare la proprietà `Controls` di un oggetto <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> per scorrere tutti i controlli nel documento, compresi i controlli aggiunti in fase di progettazione. Questi controlli sono anche noti come *controlli statici*.

 È possibile rimuovere controlli dinamici chiamando il `Delete` metodo del controllo o chiamando il `Remove` metodo per ogni raccolta di controlli. Nell'esempio di codice seguente, il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> viene usato per rimuovere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> dall'oggetto `Sheet1` di un progetto a livello di documento per Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 Non è possibile rimuovere controlli statici in fase di esecuzione. Se si tenta di usare il metodo `Delete` o il metodo `Remove` per rimuovere un controllo statico, verrà generata un'eccezione <xref:Microsoft.Office.Tools.CannotRemoveControlException>.

> [!NOTE]
> Non rimuovere a livello di codice i controlli nel gestore eventi `Shutdown` del documento. Gli elementi di interfaccia utente del documento non sono più disponibili quando viene generato l'evento `Shutdown` . Se si desidera rimuovere i controlli prima della chiusura del documento, aggiungere il codice al gestore eventi per un altro evento, ad esempio <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> o <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> per Word oppure <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>o <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> per Excel.

## <a name="HostControls"></a> Aggiungere controlli host ai documenti

Quando si aggiunge a livello di codice un controllo host a un documento, è necessario specificare un nome che identifichi il controllo in modo univoco, nonché la posizione del documento in cui aggiungere il controllo. Per istruzioni specifiche, vedere gli argomenti seguenti:

- [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Procedura: Aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Procedura: Aggiungere contenuto controlli ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Procedura: Aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Per altre informazioni sui controlli host, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).

Quando si salva e si chiude un documento, tutti i controlli host creati dinamicamente vengono disconnessi dai relativi eventi e perdono le proprie funzionalità di associazione dati. È possibile aggiungere codice alla soluzione per ricreare i controlli host quando il documento viene riaperto. Per altre informazioni, vedere [mantengono i controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> I controlli host <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>e <xref:Microsoft.Office.Tools.Word.XMLNodes>non possono essere aggiunti a livello di codice ai documenti. Di conseguenza, per tali controlli non viene fornito alcun metodo di supporto.

## <a name="WindowsForms"></a> Aggiungere controlli Windows Form ai documenti
 Quando si aggiunge a livello di codice un controllo Windows Form a un documento, è necessario fornire il percorso del controllo e un nome che lo identifichi in modo univoco. Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fornisce metodi di supporto per ogni controllo. Questi metodi sono sottoposti a overload per consentire il passaggio di un intervallo o le coordinate specifiche per la posizione del controllo.

 Quando si salva e si chiude un documento, tutti i controlli Windows Form creati dinamicamente vengono rimossi dal documento. È possibile aggiungere codice alla soluzione per ricreare i controlli quando il documento viene riaperto. Se si creano controlli Windows Form dinamici usando un componente aggiuntivo VSTO, il wrapper ActiveX dei controlli rimangono nel documento. Per altre informazioni, vedere [mantengono i controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> I controlli Windows Form non possono essere aggiunti a documenti protetti a livello di codice. Per rimuovere a livello di codice la protezione di un documento di Word o di un foglio di lavoro di Excel allo scopo di aggiungere un controllo, è necessario scrivere codice aggiuntivo per rimuovere il wrapper ActiveX del controllo alla chiusura del documento. Il wrapper ActiveX del controllo non viene eliminato automaticamente dai documenti protetti.

### <a name="add-custom-controls"></a>Aggiungere controlli personalizzati
 Se si desidera aggiungere un <xref:System.Windows.Forms.Control> non supportato dai metodi di supporto disponibili, ad esempio un controllo utente personalizzato, usare i metodi seguenti:

- Per Excel, usare uno dei metodi <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> di un oggetto <xref:Microsoft.Office.Tools.Excel.ControlCollection> .

- Per Word, usare uno dei metodi <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.ControlCollection> .

  Per aggiungere il controllo, passare il controllo <xref:System.Windows.Forms.Control>, la posizione del controllo e un nome che lo identifichi in modo univoco per il metodo `AddControl`. Il metodo `AddControl` restituisce un oggetto che definisce la modalità di interazione del controllo con il foglio di lavoro o il documento. Il `AddControl` metodo restituisce un <xref:Microsoft.Office.Tools.Excel.ControlSite> (per Excel) o un <xref:Microsoft.Office.Tools.Word.ControlSite> oggetto (per Word).

  Nell'esempio di codice seguente viene illustrato come usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> per aggiungere dinamicamente un controllo utente personalizzato a un foglio di lavoro in un progetto Excel a livello di documento. In questo esempio, il controllo utente è denominato `UserControl1`e <xref:Microsoft.Office.Interop.Excel.Range> è denominato `range1`. Per usare questo esempio, eseguirlo dalla classe `Sheet`*n* nel progetto.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Usare i membri di controlli personalizzati
 Dopo aver usato uno dei metodi `AddControl` per aggiungere un controllo a un foglio di lavoro o a un documento, si dispone di due oggetti controllo diversi:

- Il controllo <xref:System.Windows.Forms.Control> che rappresenta il controllo personalizzato.

- Oggetto `ControlSite`, `OLEObject` o `OLEControl` che rappresenta il controllo dopo l'aggiunta al foglio di lavoro o al documento.

  Questi controlli condividono molti metodi e proprietà. È importante accedere a questi membri mediante il controllo appropriato:

- Per accedere ai membri appartenenti esclusivamente al controllo personalizzato, usare <xref:System.Windows.Forms.Control>.

- Per accedere a membri condivisi dai controlli, usare l'oggetto `ControlSite`, `OLEObject` o `OLEControl`.

  Se si accede a un membro condiviso da <xref:System.Windows.Forms.Control>, è possibile che vengano generati risultati non validi oppure che si verifichi un errore senza che vengano visualizzati avvisi o notifiche. Usare sempre i metodi o le proprietà dell'oggetto `ControlSite`, `OLEObject` o `OLEControl`, a meno che il metodo o la proprietà da usare non sia disponibile; solo in questo caso è opportuno fare riferimento a <xref:System.Windows.Forms.Control>.

  Ad esempio, sia la classe <xref:Microsoft.Office.Tools.Excel.ControlSite> che la classe <xref:System.Windows.Forms.Control> dispongono di una proprietà `Top`. Per ottenere o impostare la distanza fra la parte superiore del controllo e quella del documento, usare la proprietà <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> del controllo <xref:Microsoft.Office.Tools.Excel.ControlSite>anziché la proprietà <xref:System.Windows.Forms.Control.Top%2A> del controllo <xref:System.Windows.Forms.Control>.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]

## <a name="see-also"></a>Vedere anche
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Rendere persistenti i controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli contenuto a documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Procedura: Aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Controlli Windows Form in panoramica di documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
