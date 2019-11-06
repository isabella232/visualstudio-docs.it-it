---
title: Panoramica del modello a oggetti di Excel
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf81dea230c2cfc33eb19ca001d8c9ed06b0489c
ms.sourcegitcommit: 77ef1dcc71057cd5fdc4733ff0cb6085bd6113e0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73661855"
---
# <a name="excel-object-model-overview"></a>Panoramica del modello a oggetti di Excel
  Per sviluppare soluzioni che utilizzano Microsoft Office Excel, è possibile interagire con gli oggetti forniti dal modello a oggetti di Excel. In questo argomento vengono introdotti gli oggetti più importanti:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Il modello a oggetti è strettamente basato sull'interfaccia utente. L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> rappresenta l'intera applicazione e ogni oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> contiene una raccolta di oggetti `Worksheet`. La principale astrazione che rappresenta le celle è l’oggetto <xref:Microsoft.Office.Interop.Excel.Range> che consente di lavorare con singole celle o gruppi di celle.

  Oltre al modello a oggetti di Excel, i progetti di Office in Visual Studio forniscono *elementi host* e *controlli host* che estendono alcuni oggetti nel modello a oggetti di Excel. Gli elementi host e i controlli host si comportano come gli oggetti di Excel che estendono, ma dispongono anche di funzionalità aggiuntive, ad esempio funzionalità di associazione dati ed eventi aggiuntivi. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md) e [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

  In questo argomento viene illustrato brevemente il modello a oggetti di Excel. Per le risorse in cui è possibile ottenere altre informazioni sull'intero modello a oggetti di Excel, vedere [usare la documentazione del modello a oggetti di Excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Accedere agli oggetti in un progetto di Excel
 Quando si crea un nuovo progetto di componente aggiuntivo VSTO per Excel, Visual Studio crea automaticamente un file di codice *ThisAddIn. vb* o *ThisAddIn.cs* . È possibile accedere all'oggetto applicazione tramite `Me.Application` o `this.Application`.

 Quando si crea un nuovo progetto a livello di documento per Excel, è possibile creare un nuovo progetto cartella di lavoro di Excel o modello di Excel. Visual Studio crea automaticamente i file di codice seguenti nel nuovo progetto di Excel per i progetti di cartella di lavoro e modello.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sheet1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 È possibile utilizzare la classe `Globals` nel progetto per accedere a `ThisWorkbook`, `Sheet1`, `Sheet2` o `Sheet3` dall'esterno della rispettiva classe. Per altre informazioni, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md). Nell'esempio seguente viene chiamato il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> di `Sheet1`, indipendentemente dal fatto che il codice venga inserito in una delle classi `Sheet`*n* o nella classe `ThisWorkbook`.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Poiché i dati in un documento di Excel sono altamente strutturati, il modello a oggetti è gerarchico e diretto. In Excel sono disponibili centinaia di oggetti con cui è possibile interagire, ma è possibile iniziare a utilizzare il modello a oggetti concentrandosi su un piccolo subset degli oggetti disponibili. Questi oggetti sono i seguenti quattro:

- Applicazione

- Workbook

- Worksheet

- Intervallo

  La maggior parte del lavoro svolto con Excel coinvolge questi quattro oggetti e i relativi membri.

### <a name="application-object"></a>Oggetto Application
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> di Excel rappresenta l'applicazione Excel stessa. L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> espone una grande quantità di informazioni sull'applicazione in esecuzione, le opzioni applicate a tale istanza e gli oggetti dell'utente corrente aperti all'interno dell'istanza.

> [!NOTE]
> Non è necessario impostare la proprietà <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Application> in Excel su **false**. Impostando questa proprietà su false si impedisce ad Excel di generare eventi, inclusi gli eventi dei controlli host.

### <a name="workbook-object"></a>Oggetto cartella di lavoro
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> rappresenta una singola cartella di lavoro all'interno dell'applicazione Excel.

 Gli strumenti di sviluppo di Office in Visual Studio estendono l'oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> fornendo il tipo <xref:Microsoft.Office.Tools.Excel.Workbook> . Questo tipo consente di accedere a tutte le funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook>. Per ulteriori informazioni, vedere [elemento host Workbook](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Worksheet (oggetto)
 L'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> è membro della raccolta <xref:Microsoft.Office.Interop.Excel.Worksheets>. Molte proprietà, metodi ed eventi dell’oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> sono identici o simili ai membri forniti dagli oggetti <xref:Microsoft.Office.Interop.Excel.Application> o <xref:Microsoft.Office.Interop.Excel.Workbook>.

 Excel fornisce una raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> come proprietà di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook>. Ogni membro della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> può essere un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart>.

 Gli strumenti di sviluppo di Office in Visual Studio estendono l'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> fornendo il tipo <xref:Microsoft.Office.Tools.Excel.Worksheet> . Questo tipo consente di accedere a tutte le funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet>, nonché nuove funzionalità quali la possibilità di ospitare controlli gestiti e gestire i nuovi eventi. Per ulteriori informazioni, vedere [elemento host Worksheet](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Oggetto Range
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Range> è quello più utilizzato nelle applicazioni di Excel. Prima di poter modificare un'area in Excel, è necessario esprimerlo come oggetto <xref:Microsoft.Office.Interop.Excel.Range> e utilizzare i metodi e le proprietà di tale intervallo. Un oggetto <xref:Microsoft.Office.Interop.Excel.Range> rappresenta una cella, una riga, una colonna, una selezione di celle contenenti uno o più blocchi di celle che possono o meno essere contigui o anche un gruppo di celle in più fogli.

 Visual Studio estende l’oggetto <xref:Microsoft.Office.Interop.Excel.Range> fornendo i tipi <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Questi tipi hanno la maggior parte delle medesime funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Range>, nonché nuove funzionalità, quali la funzionalità di data binding, e nuovi eventi. Per altre informazioni, vedere [controllo NamedRange](../vsto/namedrange-control.md) e [controllo XmlMappedRange](../vsto/xmlmappedrange-control.md).

## <a name="ExcelOMDocumentation"></a>Usare la documentazione del modello a oggetti di Excel
 Per informazioni complete sul modello a oggetti di Excel, è possibile utilizzare il riferimento di assembly di interoperabilità primario di Excel e il riferimento del modello a oggetti VBA.

### <a name="primary-interop-assembly-reference"></a>Riferimento all'assembly di interoperabilità primario
 Nella documentazione di riferimento dell’assembly di interoperabilità primario di Excel vengono descritti i tipi dell'assembly di interoperabilità primario per Excel. Questa documentazione è disponibile nel percorso seguente: [riferimento all'assembly di interoperabilità primario di Excel 2010](/visualstudio/vsto/office-primary-interop-assemblies).

 Per ulteriori informazioni sulla progettazione dell'assembly di interoperabilità primario di Excel, ad esempio le differenze tra classi e interfacce nell'assembly di interoperabilità primario e il modo in cui vengono implementati gli eventi nell' [assembly di interoperabilità primario di Office](/previous-versions/office/office-12/ms247299(v=office.12))

### <a name="vba-object-model-reference"></a>Riferimento del modello a oggetti VBA
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Excel esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimento del modello a oggetti di Excel 2010](/office/vba/api/overview/Excel/object-model).

 Tutti gli oggetti e i membri del riferimento del modello a oggetti VBA corrispondono ai tipi e ai membri dell'assembly di interoperabilità primario di Excel. Ad esempio, l'oggetto foglio di lavoro nel riferimento del modello a oggetti VBA corrisponde all'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nell'assembly di interoperabilità primario di Excel. Sebbene il riferimento del modello a oggetti VBA fornisce esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA di questo riferimento per Visual Basic o Visual C#, se si desidera utilizzarlo in un progetto di Excel che è possibile creare tramite Visual Studio.

### <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Soluzioni Excel](../vsto/excel-solutions.md)|Viene illustrato come creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Excel.|
|[Usare gli intervalli](../vsto/working-with-ranges.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con gli intervalli.|
|[Usare i fogli di lavoro](../vsto/working-with-worksheets.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con i fogli di lavoro.|
|[Utilizzare le cartelle di lavoro](../vsto/working-with-workbooks.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con le cartelle di lavoro.|
