---
title: Estendere la documentazione di Word & cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione
description: Informazioni su come usare un componente aggiuntivo VSTO per personalizzare i documenti di Word e le cartelle di lavoro di Excel in diversi modi.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 465e28ed0c632bba45fac1670dd40cd90ef417f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970374"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Estendi i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione
  È possibile usare un componente aggiuntivo VSTO per personalizzare i documenti di Word e le cartelle di lavoro di Excel nei modi seguenti:

- Aggiungere controlli gestiti a qualsiasi foglio di lavoro o documento aperto.

- Convertire un oggetto elenco di un foglio di lavoro di Excel in un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> esteso che espone gli eventi e che può essere associato a dati mediante il modello di associazione dati di Windows Form.

- Eventi di accesso a livello di applicazione esposti da Word ed Excel per documenti, cartelle di lavoro e fogli di lavoro specifici.

  Per usare questa funzionalità, è necessario creare un oggetto in fase di esecuzione che estenda il documento o la cartella di lavoro.

  **Si applica a:** Le informazioni contenute in questo articolo sono valide per i progetti di componenti aggiuntivi VSTO per le seguenti applicazioni: Excel e Word. Per ulteriori informazioni, vedere [funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="generate-extended-objects-in-vsto-add-ins"></a>Generare oggetti estesi nei componenti aggiuntivi VSTO
 Gli *oggetti estesi* rappresentano istanze di tipi forniti da Visual Studio Tools per Office Runtime e aggiungono funzionalità a oggetti che esistono in modo nativo nei modelli a oggetti di Word o Excel (chiamati *oggetti nativi di Office*). Per creare un oggetto esteso per un oggetto di Word o Excel, utilizzare il metodo `GetVstoObject`. La prima volta che si chiama il `GetVstoObject` metodo per un oggetto di Word o Excel specificato, viene restituito un nuovo oggetto che estende l'oggetto specificato. Tutte le altre volte in cui si chiama un metodo e si specifica lo stesso oggetto di Word o Excel, viene restituito lo stesso oggetto esteso.

 Il tipo dell'oggetto esteso dispone dello stesso nome di quello dell'oggetto nativo di Office; tuttavia, il tipo è definito nello spazio dei nomi <xref:Microsoft.Office.Tools.Excel> o <xref:Microsoft.Office.Tools.Word> . Ad esempio, se si chiama il metodo `GetVstoObject` per estendere un oggetto <xref:Microsoft.Office.Interop.Word.Document>, il metodo restituisce un oggetto <xref:Microsoft.Office.Tools.Word.Document>.

 l metodi `GetVstoObject` devono essere usati principalmente nei progetti di componente aggiuntivo VSTO. È inoltre possibile usare questi metodi nei progetti a livello di documento, ma si comportano in modo diverso e sono caratterizzati da minori possibilità di utilizzo.

 Per determinare se un oggetto esteso sia stato già creato per un particolare oggetto nativo di Office, usare il metodo `HasVstoObject`. Per ulteriori informazioni, vedere [determinare se un oggetto di Office è stato esteso](#HasVstoObject).

### <a name="generate-host-items"></a>Genera elementi host
 Quando si utilizza `GetVstoObject` per estendere un oggetto a livello di documento (ovvero,, <xref:Microsoft.Office.Interop.Excel.Workbook> <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Word.Document> ), l'oggetto restituito viene denominato *elemento host*. Un elemento host è un tipo che può contenere altri oggetti, inclusi altri oggetti estesi e controlli. È simile al tipo corrispondente presente nell'assembly di interoperabilità primaria di Word o Excel, ma dispone di funzionalità aggiuntive. Per ulteriori informazioni sugli elementi host, vedere [Cenni preliminari sugli elementi host e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

 Dopo aver generato un elemento host, è possibile usarlo per aggiungere controlli gestiti al documento, alla cartella di lavoro o al foglio di lavoro. Per ulteriori informazioni, vedere [aggiunta di controlli gestiti a documenti e fogli di](#AddControls)dati.

#### <a name="to-generate-a-host-item-for-a-word-document"></a>Creare un elemento host per un documento di Word

- Nel seguente esempio di codice viene spiegato come creare un elemento host per il documento attivo.

     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]

#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Creare un elemento host per una cartella di lavoro di Excel

- Nel seguente esempio di codice viene spiegato come creare un elemento host per la cartella di lavoro attiva.

     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]

#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Creare un elemento host per un foglio di lavoro di Excel

- Nel seguente esempio di codice viene spiegato come creare un elemento host per il foglio di lavoro attivo.

     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]

### <a name="generate-listobject-host-controls"></a>Genera controlli host ListObject
 Quando si usa il metodo `GetVstoObject` per estendere un <xref:Microsoft.Office.Interop.Excel.ListObject>, il metodo restituisce un <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject>Dispone di tutte le funzionalità dell'oggetto originale <xref:Microsoft.Office.Interop.Excel.ListObject> . Dispone inoltre di funzionalità aggiuntive e può essere associato ai dati tramite il modello di Windows Form data binding. Per ulteriori informazioni, vedere [controllo ListObject](../vsto/listobject-control.md).

#### <a name="to-generate-a-host-control-for-a-listobject"></a>Creare un controllo host per ListObject

- Nel seguente esempio di codice viene spiegato come creare un <xref:Microsoft.Office.Tools.Excel.ListObject> per il primo <xref:Microsoft.Office.Interop.Excel.ListObject> nel foglio di lavoro attivo di un progetto.

     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]

### <a name="add-managed-controls-to-documents-and-worksheets"></a><a name="AddControls"></a> Aggiungere controlli gestiti a documenti e fogli di
 Dopo aver generato un <xref:Microsoft.Office.Tools.Word.Document> o un <xref:Microsoft.Office.Tools.Excel.Worksheet>, è possibile aggiungere controlli al documento o al foglio di lavoro rappresentato da tali oggetti estesi. Per aggiungere controlli, utilizzare la `Controls` proprietà di <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet> . Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

 È possibile aggiungere controlli Windows Form o *controlli host*. Un controllo host viene fornito dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e che esegue il wrapping di un controllo corrispondente nell'assembly di interoperabilità primario di Word o di Excel. Un controllo host espone tutti i comportamenti dell'oggetto nativo di Office sottostante. Genera inoltre eventi e può essere associato ai dati tramite il modello di Windows Form data binding. Per altre informazioni, vedere [Cenni preliminari sugli elementi host e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

> [!NOTE]
> Non è possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> a un foglio di lavoro, un controllo <xref:Microsoft.Office.Tools.Word.XMLNode> oppure <xref:Microsoft.Office.Tools.Word.XMLNodes> a un documento usando un componente aggiuntivo VSTO. Questi controlli host non possono essere aggiunti a livello di codice. Per ulteriori informazioni, vedere [limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="persist-and-remove-controls"></a>Mantieni e Rimuovi controlli
 Quando si aggiungono controlli gestiti a un documento oppure a un foglio di lavoro, tali controlli non vengono conservati al momento di salvataggio e chiusura del documento. Tutti i controlli host vengono rimossi; in questo modo, vengono conservati soltanto gli oggetti Office nativi. Ad esempio, un <xref:Microsoft.Office.Tools.Excel.ListObject> diventa un <xref:Microsoft.Office.Interop.Excel.ListObject>. Inoltre, vengono rimossi tutti i controlli Windows Form. Tuttavia, i wrapper ActiveX dei controlli vengono mantenuti nel documento. È necessario includere un codice nel componente aggiuntivo VSTO per pulire i controlli oppure per creare di nuovo i controlli alla successiva apertura del documento. Per ulteriori informazioni, vedere la pagina relativa alla [permanenza dei controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

## <a name="access-application-level-events-on-documents-and-workbooks"></a>Accedere a eventi a livello di applicazione su documenti e cartelle di lavoro
 Alcuni eventi relativi a documenti, cartelle di lavoro e fogli di lavoro nei modelli a oggetti nativi di Word ed Excel vengono generati soltanto a livello di applicazione. Ad esempio, l'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> viene generato quando si apre un documento di Word; tuttavia, tale evento viene definito nella classe <xref:Microsoft.Office.Interop.Word.Application> invece che nella classe <xref:Microsoft.Office.Interop.Word.Document> .

 Quando si usano soltanto oggetti nativi di Office nel componente aggiuntivo VSTO, è necessario gestire tali eventi a livello di applicazione e scrivere codice aggiuntivo per determinare se il documento che ha creato l'evento è uno di quelli personalizzati. Gli elementi host forniscono questi eventi a livello di documento, in modo che sia più semplice gestire gli eventi per un documento specifico. È possibile creare un elemento host e gestire l'evento per quell'elemento host.

### <a name="example-that-uses-native-word-objects"></a>Esempio che usa oggetti nativi di Word
 Nel seguente esempio di codice viene descritto come gestire un evento a livello di applicazione per i documenti di Word. Il metodo `CreateDocument` consente di creare un nuovo documento e di definire il gestore eventi <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> che impedisce di salvare il documento. Si tratta di un evento a livello di applicazione generato per l' <xref:Microsoft.Office.Interop.Word.Application> oggetto e il gestore eventi deve confrontare il `Doc` parametro con l' `document1` oggetto per determinare se `document1` rappresenta il documento salvato.

 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]

### <a name="examples-that-use-a-host-item"></a>Esempi in cui viene utilizzato un elemento host
 Negli esempi di codice seguenti, il processo viene semplificato gestendo l'evento <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> di un elemento host <xref:Microsoft.Office.Tools.Word.Document> . Il `CreateDocument2` metodo in questi esempi genera un <xref:Microsoft.Office.Tools.Word.Document> oggetto che estende l' `document2` oggetto e quindi definisce un <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> gestore eventi che impedisce il salvataggio del documento. Il gestore eventi viene chiamato solo quando `document2` viene salvato e può annullare l'azione di salvataggio senza eseguire operazioni aggiuntive per verificare quale documento è stato salvato.

 Nell'esempio di codice seguente viene illustrata questa attività.

 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]

## <a name="determine-whether-an-office-object-has-been-extended"></a><a name="HasVstoObject"></a> Determinare se un oggetto di Office è stato esteso
 Per determinare se un oggetto esteso sia stato già creato per un particolare oggetto nativo di Office, usare il metodo `HasVstoObject`. Questo metodo restituisce **true** se è già stato generato un oggetto esteso.

 Usare il metodo `Globals.Factory.HasVstoMethod`. Passare all'oggetto Word o Excel nativo (ad esempio, un <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>) che si desidera sottoporre a test per un oggetto esteso.

 Il metodo `HasVstoObject` è utile se si desidera eseguire il codice nel caso in cui un oggetto di Office disponga di un oggetto esteso. Se, ad esempio, si dispone di un componente aggiuntivo VSTO di Word che gestisce l' <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> evento per rimuovere i controlli gestiti da un documento prima che venga salvato, utilizzare il `HasVstoObject` metodo per determinare se il documento è stato esteso. Se il documento non è stato esteso, non può avere controlli gestiti e il gestore dell'evento può restituire senza provare a pulire i controlli del documento.

## <a name="see-also"></a>Vedi anche
- [Componenti aggiuntivi VSTO di programma](../vsto/programming-vsto-add-ins.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Procedure dettagliate e esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md)
