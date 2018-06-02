---
title: Rendere persistenti i controlli dinamici nei documenti di Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b7544549460ab7582ce1af8fde7616213c79e9df
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692795"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Rendere persistenti i controlli dinamici nei documenti di Office
  I controlli aggiunti in fase di esecuzione non vengono mantenuti quando il documento o la cartella di lavoro viene salvato e chiuso. Il comportamento effettivo varia a seconda che il controllo sia host o Windows Form. In entrambi casi è possibile aggiungere codice alla soluzione per ricreare i controlli quando l'utente riapre il documento.  
  
 I controlli aggiunti ai documenti in fase di esecuzione sono noti come *controlli dinamici*. Per ulteriori informazioni sui controlli dinamici, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="persist-host-controls-in-the-document"></a>Rendere persistenti i controlli host nel documento  
 Quando si salva e si chiude un documento, tutti i controlli host dinamici vengono rimossi dal documento. Soltanto gli oggetti nativi di Office sottostanti restano nel documento. Ad esempio, un controllo host <xref:Microsoft.Office.Tools.Excel.ListObject> diviene <xref:Microsoft.Office.Interop.Excel.ListObject>. Gli oggetti nativi di Office non sono connessi agli eventi del controllo host e non dispongono della funzionalità di associazione dati del controllo host.  
  
 Nella tabella seguente viene indicato l'oggetto nativo di Office che resta in un documento per ogni tipo di controllo host.  
  
|Tipo di controllo host|Tipo di oggetto nativo di Office|  
|-----------------------|-------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Ricreare controlli host dinamici all'apertura dei documenti  
 È possibile ricreare controlli host dinamici al posto dei controlli nativi esistenti ogni volta che un utente apre un documento. Questa modalità di creazione dei controlli host all'apertura di un documento simula l'esperienza d'uso prevista dagli utenti.  
  
 Per ricreare un controllo host per Word o un <xref:Microsoft.Office.Tools.Excel.NamedRange> o <xref:Microsoft.Office.Tools.Excel.ListObject> controllo host per Excel, usare un `Add` \< *classe del controllo*> metodo di un <xref:Microsoft.Office.Tools.Excel.ControlCollection> o <xref:Microsoft.Office.Tools.Word.ControlCollection> oggetto. Usare un metodo che dispone di un parametro per l'oggetto nativo di Office.  
  
 Ad esempio, se si desidera creare un controllo host <xref:Microsoft.Office.Tools.Excel.ListObject> da un controllo nativo <xref:Microsoft.Office.Interop.Excel.ListObject> esistente quando il documento viene aperto, usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> e passare il controllo <xref:Microsoft.Office.Interop.Excel.ListObject>esistente. Nell'esempio di codice seguente viene illustrata la stessa procedura in un progetto a livello di documento per Excel. Il codice ricrea un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> dinamico basato su un oggetto <xref:Microsoft.Office.Interop.Excel.ListObject> esistente denominato `MyListObject` nella classe `Sheet1` .  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]  
  
### <a name="re-create-chart"></a>Creare di nuovo grafico 
 Per ricreare un controllo host <xref:Microsoft.Office.Tools.Excel.Chart> , è innanzitutto necessario eliminare l'oggetto nativo <xref:Microsoft.Office.Interop.Excel.Chart>e quindi ricreare <xref:Microsoft.Office.Tools.Excel.Chart> usando il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> oppure il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> . Non esiste alcun `Add` \< *classe del controllo*> metodo che consente di creare un nuovo <xref:Microsoft.Office.Tools.Excel.Chart> in base a un oggetto esistente <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Se non si elimina innanzitutto l'oggetto <xref:Microsoft.Office.Interop.Excel.Chart>nativo, verrà creato un secondo grafico duplicato quando si ricrea <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
## <a name="persist-windows-forms-controls-in-documents"></a>Rendere persistenti i controlli Windows Form nei documenti  
 Quando si salva e si chiude un documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuove automaticamente dal documento tutti i controlli Windows Form creati dinamicamente. Tuttavia, il comportamento varia a seconda che il progetto sia a livello di documento o a livello di componente aggiuntivo VSTO.  
  
 Nelle personalizzazioni a livello di documento, i controlli e i relativi wrapper ActiveX sottostanti (usati per ospitare i controlli nel documento) vengono rimossi alla successiva apertura del documento. Dopo la rimozione, dei controlli non resta alcuna traccia.  
  
 Anche nei componenti aggiuntivi VSTO i controlli vengono rimossi, tuttavia i wrapper ActiveX rimangono nel documento. Alla successiva apertura del documento da parte dell'utente, i wrapper ActiveX sono visibili. In Excel, i wrapper ActiveX visualizzano le immagini dei controlli nello stesso modo in cui erano visualizzati l'ultima volta che il documento è stato salvato. In Word, i wrapper ActiveX sono invisibili a meno che l'utente non faccia clic su di essi. In questo caso, viene visualizzata una linea punteggiata che delinea il bordo dei controlli. Esistono diversi modi per rimuovere i wrapper ActiveX. Per altre informazioni, vedere [rimuovere wrapper ActiveX contenuti in un componente aggiuntivo](#removingActiveX).  
  
### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Ricreare i controlli Windows Form all'apertura dei documenti  
 È possibile ricreare i controlli Windows Form eliminati quando l'utente riapre il documento. A questo scopo, la soluzione deve eseguire le attività seguenti:  
  
1.  Memorizzare le informazioni sulla dimensione, il percorso e lo stato dei controlli quando il documento viene salvato o chiuso. In una personalizzazione a livello di documento, è possibile salvare i dati nella cache di dati nel documento. In un componente aggiuntivo VSTO, è possibile salvare i dati in una parte XML personalizzata nel documento.  
  
2.  Ricreare i controlli in un evento generato all'apertura del documento. Nei progetti a livello di documento, questa attività può essere eseguita nei gestori eventi `Sheet`*n*`_Startup` o `ThisDocument_Startup` . Nei progetti di componenti aggiuntivi VSTO, questa attività può essere eseguita nei gestori degli eventi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .  
  
###  <a name="removingActiveX"></a> Rimuovere i wrapper ActiveX in un componente aggiuntivo  
 Quando si usa un componente aggiuntivo VSTO per aggiungere controlli Windows Form dinamici ai documenti, è possibile impedire che i wrapper ActiveX dei controlli vengano visualizzati nel documento alla successiva apertura di quest'ultimo.  
  
#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Rimuovere i wrapper ActiveX all'apertura del documento  
 Per rimuovere tutti i wrapper ActiveX, chiamare il `GetVstoObject` per generare un elemento host per il <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Workbook> che rappresenta il documento appena aperto. Per rimuovere tutti i wrapper ActiveX da un documento di Word, ad esempio, è possibile chiamare il `GetVstoObject` per generare un elemento host per il <xref:Microsoft.Office.Interop.Word.Document> oggetto passato al gestore dell'evento per il <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> evento.  
  
 Questa procedura è utile quando si sa che il documento verrà aperto solo su computer in cui è stato installato il componente aggiuntivo VSTO. Se esiste la possibilità che il documento venga passato ad altri utenti che non hanno installato il componente aggiuntivo VSTO, rimuovere i controlli prima di chiudere il documento.  
  
 Esempio di codice seguente viene illustrato come chiamare il `GetVstoObject` metodo quando il documento viene aperto.  
  
 [!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
 [!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]  
  
 Sebbene il `GetVstoObject` venga usato principalmente per generare un nuovo elemento host in fase di esecuzione, questo metodo cancella tutti i wrapper ActiveX dal documento la prima volta che viene chiamato per un documento specifico. Per ulteriori informazioni su come usare il `GetVstoObject` metodo, vedere [documenti estendere Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Si noti che se il componente aggiuntivo VSTO crea controlli dinamici all'apertura del documento, il componente aggiuntivo VSTO chiamerà già il `GetVstoObject` metodo come parte del processo di creazione dei controlli. Non è necessario aggiungere una chiamata separata al `GetVstoObject` metodo utile per rimuovere i wrapper ActiveX in questo scenario.  
  
#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Rimuovere i controlli dinamici prima che quest'ultimo viene chiuso  
 Il componente aggiuntivo VSTO può rimuovere in modo esplicito ogni controllo dinamico dal documento prima che quest'ultimo venga chiuso. Questa procedura è utile per i documenti che possono essere passati a utenti che non hanno installato il componente aggiuntivo VSTO.  
  
 Nell'esempio di codice seguente viene illustrato come rimuovere tutti i controlli Windows Form da un documento di Word alla chiusura del documento.  
  
 [!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
 [!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  