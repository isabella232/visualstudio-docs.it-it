---
title: Mantieni controlli dinamici nei documenti di Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d48dfab18ec2165753ac19330f7fbe18c923da9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256001"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Mantieni controlli dinamici nei documenti di Office

I controlli che vengono aggiunti in fase di esecuzione non vengono mantenuti al salvataggio e alla chiusura di un documento o di una cartella di lavoro. Il comportamento effettivo varia a seconda che il controllo sia host o Windows Form. In entrambi casi è possibile aggiungere codice alla soluzione per ricreare i controlli quando l'utente riapre il documento.

I controlli aggiunti ai documenti in fase di esecuzione sono noti come *controlli dinamici*. Per altre informazioni sui controlli dinamici, vedere [aggiungere controlli ai documenti di Office in](../vsto/adding-controls-to-office-documents-at-run-time.md)fase di esecuzione.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Mantieni i controlli host nel documento

Quando si salva e si chiude un documento, tutti i controlli host dinamici vengono rimossi dal documento. Soltanto gli oggetti nativi di Office sottostanti restano nel documento. Ad esempio, un controllo host <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> diviene <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>. Gli oggetti nativi di Office non sono connessi agli eventi del controllo host e non dispongono della funzionalità di associazione dati del controllo host.

Nella tabella seguente viene indicato l'oggetto nativo di Office che resta in un documento per ogni tipo di controllo host.

|Tipo di controllo host|Tipo di oggetto nativo di Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Ricrea i controlli host dinamici all'apertura di documenti

È possibile ricreare controlli host dinamici al posto dei controlli nativi esistenti ogni volta che un utente apre un documento. Questa modalità di creazione dei controlli host all'apertura di un documento simula l'esperienza d'uso prevista dagli utenti.

Per ricreare un controllo host per Word o <xref:Microsoft.Office.Tools.Excel.NamedRange> un controllo host o <xref:Microsoft.Office.Tools.Excel.ListObject> per Excel, utilizzare una <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> `Add` \<classe Control > Metodo di un oggetto o <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> . Usare un metodo che dispone di un parametro per l'oggetto nativo di Office.

Ad esempio, se si desidera creare un controllo host <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> da un controllo nativo <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> esistente quando il documento viene aperto, usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> e passare il controllo <xref:Microsoft.Office.Interop.Excel.ListObject>esistente. Nell'esempio di codice seguente viene illustrata la stessa procedura in un progetto a livello di documento per Excel. Il codice ricrea un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> dinamico basato su un oggetto <xref:Microsoft.Office.Interop.Excel.ListObject> esistente denominato `MyListObject` nella classe `Sheet1` .

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>Ricrea grafico

Per ricreare un <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> controllo host, è innanzitutto necessario eliminare l'oggetto nativo <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>e <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> quindi ricreare usando il <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> metodo. Non esiste alcuna `Add` \< *classe del controllo*> metodo che consente di creare un nuovo <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> oggetto basato su un <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>oggetto esistente.

Se non si elimina prima l'oggetto nativo <xref:Microsoft.Office.Interop.Excel.Chart>, verrà creato un secondo grafico duplicato quando si <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>ricrea.

## <a name="persist-windows-forms-controls-in-documents"></a>Mantieni Windows Forms controlli nei documenti

Quando si salva e si chiude un documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuove automaticamente dal documento tutti i controlli Windows Form creati dinamicamente. Tuttavia, il comportamento varia a seconda che il progetto sia a livello di documento o a livello di componente aggiuntivo VSTO.

Nelle personalizzazioni a livello di documento, i controlli e i relativi wrapper ActiveX sottostanti (usati per ospitare i controlli nel documento) vengono rimossi alla successiva apertura del documento. Dopo la rimozione, dei controlli non resta alcuna traccia.

Anche nei componenti aggiuntivi VSTO i controlli vengono rimossi, tuttavia i wrapper ActiveX rimangono nel documento. Alla successiva apertura del documento da parte dell'utente, i wrapper ActiveX sono visibili. In Excel, i wrapper ActiveX visualizzano le immagini dei controlli nello stesso modo in cui erano visualizzati l'ultima volta che il documento è stato salvato. In Word, i wrapper ActiveX sono invisibili a meno che l'utente non faccia clic su di essi. In questo caso, viene visualizzata una linea punteggiata che delinea il bordo dei controlli. Esistono diversi modi per rimuovere i wrapper ActiveX. Per ulteriori informazioni, vedere [rimuovere wrapper ActiveX in un componente aggiuntivo](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Ricreare i controlli Windows Forms quando vengono aperti i documenti

È possibile ricreare i controlli Windows Form eliminati quando l'utente riapre il documento. A questo scopo, la soluzione deve eseguire le attività seguenti:

1. Memorizzare le informazioni sulla dimensione, il percorso e lo stato dei controlli quando il documento viene salvato o chiuso. In una personalizzazione a livello di documento è possibile salvare i dati nella cache dei dati nel documento. In un componente aggiuntivo VSTO è possibile salvare i dati in una parte XML personalizzata del documento.

2. Ricreare i controlli in un evento generato all'apertura del documento. Nei progetti a livello di documento, questa attività può essere eseguita nei gestori eventi `Sheet`*n*`_Startup` o `ThisDocument_Startup` . Nei progetti di componenti aggiuntivi VSTO, questa attività può essere eseguita nei gestori degli eventi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

### <a name="removingActiveX"></a>Rimuovere i wrapper ActiveX in un componente aggiuntivo

Quando si aggiungono controlli Windows Forms dinamici ai documenti usando un componente aggiuntivo VSTO, è possibile impedire che i wrapper ActiveX dei controlli vengano visualizzati nel documento alla successiva apertura nei modi seguenti.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Rimuovi wrapper ActiveX all'apertura del documento

Per rimuovere tutti i wrapper ActiveX, chiamare il metodo `GetVstoObject` per generare un elemento host per l'oggetto <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Workbook> che rappresenta il documento appena aperto. Ad esempio, per rimuovere tutti i wrapper ActiveX da un documento di Word, è possibile chiamare il metodo `GetVstoObject` per generare un elemento host per l'oggetto <xref:Microsoft.Office.Interop.Word.Document> passato al gestore dell'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.

Questa procedura è utile quando si sa che il documento verrà aperto solo su computer in cui è stato installato il componente aggiuntivo VSTO. Se esiste la possibilità che il documento venga passato ad altri utenti che non hanno installato il componente aggiuntivo VSTO, rimuovere i controlli prima di chiudere il documento.

Nell'esempio di codice seguente viene illustrato come chiamare il metodo `GetVstoObject` all'apertura del documento.

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

Benché venga usato principalmente per generare un nuovo elemento host in fase di esecuzione, il metodo `GetVstoObject` cancella tutti i wrapper ActiveX dal documento la prima volta che viene chiamato per un documento specifico. Per altre informazioni su come usare il metodo `GetVstoObject` , vedere [estendere i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)in fase di esecuzione.

Se il componente aggiuntivo VSTO crea controlli dinamici quando il documento viene aperto, il componente aggiuntivo VSTO chiamerà già il `GetVstoObject` metodo come parte del processo per creare i controlli. In questo caso, non occorre aggiungere alcuna chiamata a parte al metodo `GetVstoObject` per rimuovere i wrapper ActiveX.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Rimuovere i controlli dinamici prima della chiusura del documento

Il componente aggiuntivo VSTO può rimuovere in modo esplicito ogni controllo dinamico dal documento prima che quest'ultimo venga chiuso. Questa procedura è utile per i documenti che possono essere passati a utenti che non hanno installato il componente aggiuntivo VSTO.

Nell'esempio di codice seguente viene illustrato come rimuovere tutti i controlli Windows Form da un documento di Word alla chiusura del documento.

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>Vedere anche

- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
