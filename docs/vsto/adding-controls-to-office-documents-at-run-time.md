---
title: Aggiungere controlli ai Office in fase di esecuzione
description: Informazioni su come aggiungere controlli a un documento di Microsoft Office Word e Microsoft Office Excel cartella di lavoro in fase di esecuzione.
ms.custom: SEO-VS-2020
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
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2b6f8fdd05bde0714abc90f8c18e6217708deb6313871e41e8600acecf40af10
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440903"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Aggiungere controlli ai Office in fase di esecuzione
  È possibile aggiungere controlli a un documento di Microsoft Office Word e a una cartella di lavoro di Microsoft Office Excel in fase di esecuzione. È inoltre possibile rimuoverli in fase di esecuzione. I controlli aggiunti o rimossi in fase di esecuzione sono noti come *controlli dinamici*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 In questo argomento viene illustrato quanto segue:

- [Gestire i controlli in fase di esecuzione usando raccolte di controlli](#ControlsCollection).

- [Aggiungere controlli host ai documenti](#HostControls).

- [Aggiungere Windows form ai documenti](#WindowsForms).

## <a name="manage-controls-at-run-time-by-using-control-collections"></a><a name="ControlsCollection"></a> Gestire i controlli in fase di esecuzione usando raccolte di controlli
 Per aggiungere, ottenere o rimuovere i controlli in fase di esecuzione, usare i metodi di supporto degli oggetti <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> .

 La modalità di accesso a questi oggetti dipende dal tipo di progetto che si sta sviluppando:

- In un progetto a livello di documento per Excel, usare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> delle classi `Sheet1`, `Sheet2`e `Sheet3` . Per altre informazioni su queste classi, vedere Elemento [host Worksheet.](../vsto/worksheet-host-item.md)

- In un progetto a livello di documento per Word, usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> della classe `ThisDocument` . Per altre informazioni su questa classe, vedere Document [host item](../vsto/document-host-item.md).

- In un VSTO di componente aggiuntivo per Excel o Word, usare la proprietà di un oggetto o generato in `Controls` <xref:Microsoft.Office.Tools.Excel.Worksheet> fase di <xref:Microsoft.Office.Tools.Word.Document> esecuzione. Per altre informazioni sulla generazione di questi oggetti in fase di esecuzione, vedere Estendere documenti di Word e cartelle di lavoro [Excel in VSTO componenti aggiuntivi in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="add-controls"></a>Aggiungere controlli
 I tipi <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> includono metodi di supporto che è possibile usare per aggiungere controlli host e controlli Windows Form comuni a documenti e fogli di lavoro. Il nome di ciascun metodo presenta il formato `Add`*classe del controllo*, dove *classe del controllo* rappresenta il nome del controllo che si desidera aggiungere. Ad esempio, per aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> al documento, usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> .

 Nell'esempio di codice seguente viene aggiunto un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un oggetto `Sheet1` di un progetto a livello di documento per Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb" id="Snippet3":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs" id="Snippet3":::


### <a name="access-and-delete-controls"></a>Controlli di accesso ed eliminazione
 È possibile usare la proprietà `Controls` di un oggetto <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> per scorrere tutti i controlli nel documento, compresi i controlli aggiunti in fase di progettazione. Questi controlli sono anche noti come *controlli statici*.

 È possibile rimuovere i controlli dinamici chiamando il metodo del controllo o chiamando `Delete` il metodo di ogni raccolta `Remove` Controls. Nell'esempio di codice seguente, il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> viene usato per rimuovere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> dall'oggetto `Sheet1` di un progetto a livello di documento per Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs" id="Snippet4":::


 I controlli statici non possono essere rimossi in fase di esecuzione. Se si tenta di usare il metodo `Delete` o il metodo `Remove` per rimuovere un controllo statico, verrà generata un'eccezione <xref:Microsoft.Office.Tools.CannotRemoveControlException>.

> [!NOTE]
> Non rimuovere a livello di codice i controlli nel gestore eventi `Shutdown` del documento. Gli elementi di interfaccia utente del documento non sono più disponibili quando viene generato l'evento `Shutdown` . Se si desidera rimuovere i controlli prima della chiusura del documento, aggiungere il codice al gestore eventi per un altro evento, ad esempio <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> o <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> per Word oppure <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>o <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> per Excel.

## <a name="add-host-controls-to-documents"></a><a name="HostControls"></a> Aggiungere controlli host ai documenti

Quando si aggiunge a livello di codice un controllo host a un documento, è necessario specificare un nome che identifichi il controllo in modo univoco, nonché la posizione del documento in cui aggiungere il controllo. Per istruzioni specifiche, vedere gli argomenti seguenti:

- [Procedura: Aggiungere controlli ListObject ai fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Procedura: Aggiungere controlli NamedRange ai fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Procedura: Aggiungere controlli Chart ai fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Procedura: Aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Procedura: Aggiungere controlli Bookmark ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Per altre informazioni sui controlli host, vedere [Cenni preliminari sugli elementi host e sui controlli host.](../vsto/host-items-and-host-controls-overview.md)

Quando si salva e si chiude un documento, tutti i controlli host creati dinamicamente vengono disconnessi dai relativi eventi e perdono le proprie funzionalità di associazione dati. È possibile aggiungere codice alla soluzione per ricreare i controlli host quando il documento viene riaperto. Per altre informazioni, vedere [Rendere persistenti i controlli dinamici nei Office documenti.](../vsto/persisting-dynamic-controls-in-office-documents.md)

> [!NOTE]
> I controlli host <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>e <xref:Microsoft.Office.Tools.Word.XMLNodes>non possono essere aggiunti a livello di codice ai documenti. Di conseguenza, per tali controlli non viene fornito alcun metodo di supporto.

## <a name="add-windows-forms-controls-to-documents"></a><a name="WindowsForms"></a>Aggiungere Windows form ai documenti
 Quando si aggiunge a livello di codice un controllo Windows Form a un documento, è necessario fornire il percorso del controllo e un nome che lo identifichi in modo univoco. Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fornisce metodi di supporto per ogni controllo. Questi metodi sono sottoposti a overload per consentire il passaggio di un intervallo o le coordinate specifiche per la posizione del controllo.

 Quando si salva e si chiude un documento, tutti i controlli Windows Form creati dinamicamente vengono rimossi dal documento. È possibile aggiungere codice alla soluzione per ricreare i controlli quando il documento viene riaperto. Se si creano controlli Windows form dinamici usando un componente aggiuntivo VSTO, i wrapper ActiveX per i controlli vengono lasciati nel documento. Per altre informazioni, vedere [Rendere persistenti i controlli dinamici nei Office documenti.](../vsto/persisting-dynamic-controls-in-office-documents.md)

> [!NOTE]
> I controlli Windows Form non possono essere aggiunti a documenti protetti a livello di codice. Per rimuovere a livello di codice la protezione di un documento di Word o di un foglio di lavoro di Excel allo scopo di aggiungere un controllo, è necessario scrivere codice aggiuntivo per rimuovere il wrapper ActiveX del controllo alla chiusura del documento. Il wrapper ActiveX del controllo non viene eliminato automaticamente dai documenti protetti.

### <a name="add-custom-controls"></a>Aggiungere controlli personalizzati
 Se si desidera aggiungere un <xref:System.Windows.Forms.Control> non supportato dai metodi di supporto disponibili, ad esempio un controllo utente personalizzato, usare i metodi seguenti:

- Per Excel, usare uno dei metodi <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> di un oggetto <xref:Microsoft.Office.Tools.Excel.ControlCollection> .

- Per Word, usare uno dei metodi <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.ControlCollection> .

  Per aggiungere il controllo, passare il controllo <xref:System.Windows.Forms.Control>, la posizione del controllo e un nome che lo identifichi in modo univoco per il metodo `AddControl`. Il metodo `AddControl` restituisce un oggetto che definisce la modalità di interazione del controllo con il foglio di lavoro o il documento. Il `AddControl` metodo restituisce un oggetto <xref:Microsoft.Office.Tools.Excel.ControlSite> (per Excel) o <xref:Microsoft.Office.Tools.Word.ControlSite> un oggetto (per Word).

  Nell'esempio di codice seguente viene illustrato come usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> per aggiungere dinamicamente un controllo utente personalizzato a un foglio di lavoro in un progetto Excel a livello di documento. In questo esempio, il controllo utente è denominato `UserControl1`e <xref:Microsoft.Office.Interop.Excel.Range> è denominato `range1`. Per usare questo esempio, eseguirlo dalla classe `Sheet`*n* nel progetto.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet2":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet2":::

### <a name="use-members-of-custom-controls"></a>Usare membri di controlli personalizzati
 Dopo aver usato uno dei metodi `AddControl` per aggiungere un controllo a un foglio di lavoro o a un documento, si dispone di due oggetti controllo diversi:

- Il controllo <xref:System.Windows.Forms.Control> che rappresenta il controllo personalizzato.

- Oggetto `ControlSite`, `OLEObject` o `OLEControl` che rappresenta il controllo dopo l'aggiunta al foglio di lavoro o al documento.

  Questi controlli condividono molti metodi e proprietà. È importante accedere a questi membri mediante il controllo appropriato:

- Per accedere ai membri appartenenti esclusivamente al controllo personalizzato, usare <xref:System.Windows.Forms.Control>.

- Per accedere a membri condivisi dai controlli, usare l'oggetto `ControlSite`, `OLEObject` o `OLEControl`.

  Se si accede a un membro condiviso da <xref:System.Windows.Forms.Control>, è possibile che vengano generati risultati non validi oppure che si verifichi un errore senza che vengano visualizzati avvisi o notifiche. Usare sempre i metodi o le proprietà dell'oggetto `ControlSite`, `OLEObject` o `OLEControl`, a meno che il metodo o la proprietà da usare non sia disponibile; solo in questo caso è opportuno fare riferimento a <xref:System.Windows.Forms.Control>.

  Ad esempio, sia la classe <xref:Microsoft.Office.Tools.Excel.ControlSite> che la classe <xref:System.Windows.Forms.Control> dispongono di una proprietà `Top`. Per ottenere o impostare la distanza fra la parte superiore del controllo e quella del documento, usare la proprietà <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> del controllo <xref:Microsoft.Office.Tools.Excel.ControlSite>anziché la proprietà <xref:System.Windows.Forms.Control.Top%2A> del controllo <xref:System.Windows.Forms.Control>.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet3":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet3":::

## <a name="see-also"></a>Vedi anche
- [Controlli su Office documenti](../vsto/controls-on-office-documents.md)
- [Rendere persistenti i controlli dinamici Office documenti](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Procedura: Aggiungere controlli ListObject ai fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli NamedRange ai fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli Chart ai fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Procedura: Aggiungere controlli Bookmark ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Windows Panoramica dei controlli form Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Procedura: Aggiungere controlli form Windows a Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
