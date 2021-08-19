---
title: Rendere persistenti i controlli dinamici Office documenti
description: Informazioni su come aggiungere codice alla soluzione per creare nuovamente controlli dinamici persistenti quando un utente riapre un documento chiuso.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0cb0f808dae82b696ee9d766f394a91d25c50cd2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046243"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Rendere persistenti i controlli dinamici Office documenti

I controlli che vengono aggiunti in fase di esecuzione non vengono mantenuti al salvataggio e alla chiusura di un documento o di una cartella di lavoro. Il comportamento effettivo varia a seconda che il controllo sia host o Windows Form. In entrambi casi è possibile aggiungere codice alla soluzione per ricreare i controlli quando l'utente riapre il documento.

I controlli aggiunti ai documenti in fase di esecuzione sono noti come *controlli dinamici*. Per altre informazioni sui controlli dinamici, vedere [Aggiungere controlli ai documenti Office in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Rendere persistenti i controlli host nel documento

Quando si salva e si chiude un documento, tutti i controlli host dinamici vengono rimossi dal documento. Soltanto gli oggetti nativi di Office sottostanti restano nel documento. Ad esempio, un controllo host <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> diviene <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>. Gli oggetti nativi di Office non sono connessi agli eventi del controllo host e non dispongono della funzionalità di associazione dati del controllo host.

Nella tabella seguente viene indicato l'oggetto nativo di Office che resta in un documento per ogni tipo di controllo host.

|Tipo di controllo host|Tipo di oggetto nativo di Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Creare di nuovo controlli host dinamici all'apertura di documenti

È possibile ricreare controlli host dinamici al posto dei controlli nativi esistenti ogni volta che un utente apre un documento. Questa modalità di creazione dei controlli host all'apertura di un documento simula l'esperienza d'uso prevista dagli utenti.

Per creare nuovamente un controllo host per Word o un controllo host o per Excel, usare un metodo <xref:Microsoft.Office.Tools.Excel.NamedRange> di un oggetto o <xref:Microsoft.Office.Tools.Excel.ListObject> `Add` \<*control class*> <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> . Usare un metodo che dispone di un parametro per l'oggetto nativo di Office.

Ad esempio, se si desidera creare un controllo host <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> da un controllo nativo <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> esistente quando il documento viene aperto, usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> e passare il controllo <xref:Microsoft.Office.Interop.Excel.ListObject>esistente. Nell'esempio di codice seguente viene illustrata la stessa procedura in un progetto a livello di documento per Excel. Il codice ricrea un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> dinamico basato su un oggetto <xref:Microsoft.Office.Interop.Excel.ListObject> esistente denominato `MyListObject` nella classe `Sheet1` .

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs" id="Snippet6":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb" id="Snippet6":::

### <a name="re-create-chart"></a>Creare nuovamente un grafico

Per creare nuovamente un controllo host, è necessario prima eliminare l'oggetto nativo e quindi creare <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> nuovamente l'oggetto usando il metodo <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> . Non esiste alcun `Add` \<*control class*> metodo che consenta di creare un nuovo <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> oggetto basato su un oggetto <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> esistente.

Se non si elimina prima l'oggetto nativo, si creerà un secondo grafico duplicato quando <xref:Microsoft.Office.Interop.Excel.Chart> si rie creerà <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> .

## <a name="persist-windows-forms-controls-in-documents"></a>Rendere persistenti Windows form nei documenti

Quando si salva e si chiude un documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuove automaticamente dal documento tutti i controlli Windows Form creati dinamicamente. Tuttavia, il comportamento varia a seconda che il progetto sia a livello di documento o a livello di componente aggiuntivo VSTO.

Nelle personalizzazioni a livello di documento, i controlli e i relativi wrapper ActiveX sottostanti (usati per ospitare i controlli nel documento) vengono rimossi alla successiva apertura del documento. Dopo la rimozione, dei controlli non resta alcuna traccia.

Anche nei componenti aggiuntivi VSTO i controlli vengono rimossi, tuttavia i wrapper ActiveX rimangono nel documento. Alla successiva apertura del documento da parte dell'utente, i wrapper ActiveX sono visibili. In Excel, i wrapper ActiveX visualizzano le immagini dei controlli nello stesso modo in cui erano visualizzati l'ultima volta che il documento è stato salvato. In Word, i wrapper ActiveX sono invisibili a meno che l'utente non faccia clic su di essi. In questo caso, viene visualizzata una linea punteggiata che delinea il bordo dei controlli. Esistono diversi modi per rimuovere i wrapper ActiveX. Per altre informazioni, [vedere Rimuovere ActiveX wrapper in un componente aggiuntivo.](#removingActiveX)

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Creare nuovamente i Windows Form all'apertura dei documenti

È possibile ricreare i controlli Windows Form eliminati quando l'utente riapre il documento. A questo scopo, la soluzione deve eseguire le attività seguenti:

1. Memorizzare le informazioni sulla dimensione, il percorso e lo stato dei controlli quando il documento viene salvato o chiuso. In una personalizzazione a livello di documento è possibile salvare i dati nella cache dei dati nel documento. In un VSTO componente aggiuntivo è possibile salvare i dati in una parte XML personalizzata nel documento.

2. Ricreare i controlli in un evento generato all'apertura del documento. Nei progetti a livello di documento è possibile eseguire questa operazione nei `Sheet` *gestori* eventi n `_Startup` o `ThisDocument_Startup` . Nei progetti di componenti aggiuntivi VSTO, questa attività può essere eseguita nei gestori degli eventi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

### <a name="remove-activex-wrappers-in-an-add-in"></a><a name="removingActiveX"></a>Rimuovere ActiveX wrapper in un componente aggiuntivo

Quando si aggiungono controlli Windows Form dinamici ai documenti usando un componente aggiuntivo VSTO, è possibile impedire che i wrapper ActiveX per i controlli appaiano nel documento alla successiva apertura nei modi seguenti.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Rimuovere ActiveX wrapper all'apertura del documento

Per rimuovere tutti i wrapper ActiveX, chiamare il metodo `GetVstoObject` per generare un elemento host per l'oggetto <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Workbook> che rappresenta il documento appena aperto. Ad esempio, per rimuovere tutti i wrapper ActiveX da un documento di Word, è possibile chiamare il metodo `GetVstoObject` per generare un elemento host per l'oggetto <xref:Microsoft.Office.Interop.Word.Document> passato al gestore dell'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.

Questa procedura è utile quando si sa che il documento verrà aperto solo su computer in cui è stato installato il componente aggiuntivo VSTO. Se esiste la possibilità che il documento venga passato ad altri utenti che non hanno installato il componente aggiuntivo VSTO, rimuovere i controlli prima di chiudere il documento.

Nell'esempio di codice seguente viene illustrato come chiamare il metodo `GetVstoObject` all'apertura del documento.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet11":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet11":::

Anche se il metodo viene usato principalmente per generare un nuovo elemento host in fase di esecuzione, questo metodo cancella anche tutti i wrapper ActiveX dal documento la prima volta che viene chiamato per `GetVstoObject` un documento specifico. Per altre informazioni sull'uso del metodo , vedere Estendere documenti di Word Excel cartelle di lavoro di VSTO componenti aggiuntivi `GetVstoObject` [in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

Se il componente VSTO crea controlli dinamici all'apertura del documento, il componente aggiuntivo VSTO chiamerà già il metodo come parte del processo di creazione `GetVstoObject` dei controlli. In questo caso, non occorre aggiungere alcuna chiamata a parte al metodo `GetVstoObject` per rimuovere i wrapper ActiveX.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Rimuovere i controlli dinamici prima della chiusura del documento

Il componente aggiuntivo VSTO può rimuovere in modo esplicito ogni controllo dinamico dal documento prima che quest'ultimo venga chiuso. Questa procedura è utile per i documenti che possono essere passati a utenti che non hanno installato il componente aggiuntivo VSTO.

Nell'esempio di codice seguente viene illustrato come rimuovere tutti i controlli Windows Form da un documento di Word alla chiusura del documento.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet10":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet10":::

## <a name="see-also"></a>Vedi anche

- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
