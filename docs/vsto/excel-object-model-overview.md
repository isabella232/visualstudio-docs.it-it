---
title: Excel Panoramica del modello a oggetti
description: Informazioni su come interagire con gli oggetti forniti dal modello Excel a oggetti per sviluppare soluzioni che usano Microsoft Office Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5c37a0251d9414871e568275bdb0b94bb55e5c401487e843186186105175d82e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352110"
---
# <a name="excel-object-model-overview"></a>Excel panoramica del modello a oggetti
  Per sviluppare soluzioni che utilizzano Microsoft Office Excel, è possibile interagire con gli oggetti forniti dal modello a oggetti di Excel. In questo argomento vengono introdotti gli oggetti più importanti:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Il modello a oggetti è strettamente basato sull'interfaccia utente. L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> rappresenta l'intera applicazione e ogni oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> contiene una raccolta di oggetti `Worksheet`. La principale astrazione che rappresenta le celle è l’oggetto <xref:Microsoft.Office.Interop.Excel.Range> che consente di lavorare con singole celle o gruppi di celle.

  Oltre al modello Excel a oggetti, i progetti Office in Visual Studio forniscono elementi *host* e controlli *host* che estendono alcuni oggetti nel Excel a oggetti. Gli elementi host e i controlli host si comportano come gli oggetti di Excel che estendono, ma dispongono anche di funzionalità aggiuntive, ad esempio funzionalità di associazione dati ed eventi aggiuntivi. Per altre informazioni, vedere [Automate Excel by using extended objects](../vsto/automating-excel-by-using-extended-objects.md) and Host items and host controls [overview](../vsto/host-items-and-host-controls-overview.md).

  In questo argomento viene illustrato brevemente il modello a oggetti di Excel. Per le risorse in cui è possibile ottenere altre informazioni sull'intero modello Excel a oggetti, vedere la documentazione Excel sul modello [a oggetti.](#ExcelOMDocumentation)

## <a name="access-objects-in-an-excel-project"></a>Accedere agli oggetti in un Excel progetto
 Quando si crea un nuovo progetto VSTO componente aggiuntivo per Excel, Visual Studio crea automaticamente un file di codice *ThisAddIn.vb* o *ThisAddIn.cs.* È possibile accedere all'oggetto applicazione tramite `Me.Application` o `this.Application`.

 Quando si crea un nuovo progetto a livello di documento per Excel, è possibile creare un nuovo progetto cartella di lavoro di Excel o modello di Excel. Visual Studio crea automaticamente i file di codice seguenti nel nuovo progetto di Excel per i progetti di cartella di lavoro e modello.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sheet1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 È possibile utilizzare la classe `Globals` nel progetto per accedere a `ThisWorkbook`, `Sheet1`, `Sheet2` o `Sheet3` dall'esterno della rispettiva classe. Per altre informazioni, vedere [Accesso globale agli oggetti nei Office .](../vsto/global-access-to-objects-in-office-projects.md) Nell'esempio seguente viene chiamato il metodo di indipendentemente dal fatto che il codice sia inserito in una <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> `Sheet1` delle `Sheet` *n* classi o nella `ThisWorkbook` classe .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet82":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet82":::

 Poiché i dati in un documento di Excel sono altamente strutturati, il modello a oggetti è gerarchico e diretto. Excel fornisce centinaia di oggetti con cui è possibile interagire, ma è possibile iniziare a usare il modello a oggetti concentrandosi su un piccolo subset degli oggetti disponibili. Questi oggetti sono i seguenti quattro:

- Applicazione

- Cartella di lavoro

- Foglio di lavoro

- Intervallo

  La maggior parte del lavoro svolto con Excel coinvolge questi quattro oggetti e i relativi membri.

### <a name="application-object"></a>Oggetto applicazione
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> di Excel rappresenta l'applicazione Excel stessa. L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> espone una grande quantità di informazioni sull'applicazione in esecuzione, le opzioni applicate a tale istanza e gli oggetti dell'utente corrente aperti all'interno dell'istanza.

> [!NOTE]
> Non è necessario impostare la proprietà <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Application> in Excel su **false**. Impostando questa proprietà su false si impedisce ad Excel di generare eventi, inclusi gli eventi dei controlli host.

### <a name="workbook-object"></a>Oggetto Workbook
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> rappresenta una singola cartella di lavoro all'interno dell'applicazione Excel.

 Gli strumenti di sviluppo di Office in Visual Studio estendono l'oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> fornendo il tipo <xref:Microsoft.Office.Tools.Excel.Workbook> . Questo tipo consente di accedere a tutte le funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook>. Per altre informazioni, vedere Elemento [host cartella di lavoro](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Worksheet (oggetto)
 L'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> è membro della raccolta <xref:Microsoft.Office.Interop.Excel.Worksheets>. Molte proprietà, metodi ed eventi dell’oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> sono identici o simili ai membri forniti dagli oggetti <xref:Microsoft.Office.Interop.Excel.Application> o <xref:Microsoft.Office.Interop.Excel.Workbook>.

 Excel fornisce una raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> come proprietà di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook>. Ogni membro della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> può essere un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart>.

 Gli strumenti di sviluppo di Office in Visual Studio estendono l'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> fornendo il tipo <xref:Microsoft.Office.Tools.Excel.Worksheet> . Questo tipo consente di accedere a tutte le funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet>, nonché nuove funzionalità quali la possibilità di ospitare controlli gestiti e gestire i nuovi eventi. Per altre informazioni, vedere Elemento [host Worksheet](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Oggetto Range
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Range> è quello più utilizzato nelle applicazioni di Excel. Prima di poter modificare un'area in Excel, è necessario esprimerlo come oggetto <xref:Microsoft.Office.Interop.Excel.Range> e utilizzare i metodi e le proprietà di tale intervallo. Un oggetto <xref:Microsoft.Office.Interop.Excel.Range> rappresenta una cella, una riga, una colonna, una selezione di celle contenenti uno o più blocchi di celle che possono o meno essere contigui o anche un gruppo di celle in più fogli.

 Visual Studio estende l’oggetto <xref:Microsoft.Office.Interop.Excel.Range> fornendo i tipi <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Questi tipi hanno la maggior parte delle medesime funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Range>, nonché nuove funzionalità, quali la funzionalità di data binding, e nuovi eventi. Per altre informazioni, vedere [Controllo NamedRange e](../vsto/namedrange-control.md) [Controllo XmlMappedRange](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>Usare la documentazione Excel modello a oggetti
 Per informazioni complete sul modello a oggetti di Excel, è possibile utilizzare il riferimento di assembly di interoperabilità primario di Excel e il riferimento del modello a oggetti VBA.

### <a name="primary-interop-assembly-reference"></a>Informazioni di riferimento sull'assembly di interoperabilità primario
 Nella documentazione di riferimento dell’assembly di interoperabilità primario di Excel vengono descritti i tipi dell'assembly di interoperabilità primario per Excel. Questa documentazione è disponibile nel percorso seguente: riferimento all'assembly di interoperabilità primario [Excel 2010.](office-primary-interop-assemblies.md)

 Per altre informazioni sulla progettazione dell'assembly di interoperabilità primario Excel, ad esempio le differenze tra classi e interfacce nell'assembly di interoperabilità primario e il modo in cui vengono implementati gli eventi nell'assembly di interoperabilità primario, vedere Panoramica delle classi e delle interfacce negli assembly di interoperabilità primari [di Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Informazioni di riferimento sul modello a oggetti VBA
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Excel esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere Excel riferimento al modello a oggetti [di 2010.](/office/vba/api/overview/Excel/object-model)

 Tutti gli oggetti e i membri del riferimento del modello a oggetti VBA corrispondono ai tipi e ai membri dell'assembly di interoperabilità primario di Excel. Ad esempio, l'oggetto Worksheet nel riferimento al modello a oggetti VBA corrisponde <xref:Microsoft.Office.Interop.Excel.Worksheet> all'oggetto nell'Excel PIA. Sebbene il riferimento del modello a oggetti VBA fornisce esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA di questo riferimento per Visual Basic o Visual C#, se si desidera utilizzarlo in un progetto di Excel che è possibile creare tramite Visual Studio.

### <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Excel soluzioni](../vsto/excel-solutions.md)|Viene illustrato come creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Excel.|
|[Usare gli intervalli](../vsto/working-with-ranges.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con gli intervalli.|
|[Usare i fogli di lavoro](../vsto/working-with-worksheets.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con i fogli di lavoro.|
|[Usare le cartelle di lavoro](../vsto/working-with-workbooks.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con le cartelle di lavoro.|
