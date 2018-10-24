---
title: Panoramica del modello a oggetti di Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ca93cae45eed272b683275896efcf83229ca9a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880793"
---
# <a name="excel-object-model-overview"></a>Cenni preliminari sul modello a oggetti di Excel
  Per sviluppare soluzioni che utilizzano Microsoft Office Excel, è possibile interagire con gli oggetti forniti dal modello a oggetti di Excel. In questo argomento vengono introdotti gli oggetti più importanti:  
  
- <xref:Microsoft.Office.Interop.Excel.Application>  
  
- <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
- <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
- <xref:Microsoft.Office.Interop.Excel.Range>  
  
  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
  Il modello a oggetti è strettamente basato sull'interfaccia utente. L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> rappresenta l'intera applicazione e ogni oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> contiene una raccolta di oggetti `Worksheet`. La principale astrazione che rappresenta le celle è l’oggetto <xref:Microsoft.Office.Interop.Excel.Range> che consente di lavorare con singole celle o gruppi di celle.  
  
  Oltre al modello di oggetto di Excel, progetti di Office in Visual Studio forniscono *elementi host* e *controlli host* che estendono alcuni oggetti nel modello a oggetti Excel. Gli elementi host e i controlli host si comportano come gli oggetti di Excel che estendono, ma dispongono anche di funzionalità aggiuntive, ad esempio funzionalità di data binding ed eventi aggiuntivi. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md) e [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).  
  
  In questo argomento viene illustrato brevemente il modello a oggetti di Excel. Per le risorse in cui altre informazioni sull'intero modello a oggetti Excel, vedere [usare la documentazione del modello a oggetti Excel](#ExcelOMDocumentation).  
  
  ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [How do i: utilizzare i gestori di eventi in Excel 2007 componente aggiuntivo?](http://go.microsoft.com/fwlink/?LinkID=130291), e [procedura ricerca per categorie: utilizzare le forme per creare un grafico a bolle in Excel? ](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## <a name="access-objects-in-an-excel-project"></a>Accedere agli oggetti in un progetto di Excel  
 Quando si crea un nuovo progetto di componente aggiuntivo VSTO per Excel, Visual Studio crea automaticamente un *ThisAddIn. vb* oppure *ThisAddIn.cs* file di codice. È possibile accedere all'oggetto applicazione tramite `Me.Application` o `this.Application`.  
  
 Quando si crea un nuovo progetto a livello di documento per Excel, è possibile creare un nuovo progetto cartella di lavoro di Excel o modello di Excel. Visual Studio crea automaticamente i file di codice seguenti nel nuovo progetto di Excel per i progetti di cartella di lavoro e modello.  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 È possibile utilizzare la classe `Globals` nel progetto per accedere a `ThisWorkbook`, `Sheet1`, `Sheet2` o `Sheet3` dall'esterno della rispettiva classe. Per altre informazioni, vedere [globale accedere agli oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md). L'esempio seguente chiama il <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodo di `Sheet1` indipendentemente dal fatto che il codice viene inserito in uno delle `Sheet` *n* classi o `ThisWorkbook` classe.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Poiché i dati in un documento di Excel sono altamente strutturati, il modello a oggetti è gerarchico e diretto. In Excel sono disponibili centinaia di oggetti con cui è possibile interagire, ma è possibile ottenere un buon punto di partenza sul modello a oggetti focalizzando l'attenzione su un piccolo subset degli oggetti disponibili. Questi oggetti sono i seguenti quattro:  
  
- Applicazione  
  
- Workbook  
  
- Worksheet  
  
- Intervallo  
  
  La maggior parte del lavoro svolto con Excel coinvolge questi quattro oggetti e i relativi membri.  
  
### <a name="application-object"></a>Oggetto Application  
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> di Excel rappresenta l'applicazione Excel stessa. L’oggetto <xref:Microsoft.Office.Interop.Excel.Application> espone una grande quantità di informazioni sull'applicazione in esecuzione, le opzioni applicate a tale istanza e gli oggetti dell'utente corrente aperti all'interno dell'istanza.  
  
> [!NOTE]  
>  Non è necessario impostare la proprietà <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Application> in Excel su **false**. Impostando questa proprietà su false si impedisce ad Excel di generare eventi, inclusi gli eventi dei controlli host.  
  
### <a name="workbook-object"></a>Oggetto cartella di lavoro  
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> rappresenta una singola cartella di lavoro all'interno dell'applicazione Excel.  
  
 Gli strumenti di sviluppo di Office in Visual Studio estendono l'oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> fornendo il tipo <xref:Microsoft.Office.Tools.Excel.Workbook> . Questo tipo consente di accedere a tutte le funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook>. Per altre informazioni, vedere [elemento host Workbook](../vsto/workbook-host-item.md).  
  
### <a name="worksheet-object"></a>Worksheet (oggetto)  
 L'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> è membro della raccolta <xref:Microsoft.Office.Interop.Excel.Worksheets>. Molte proprietà, metodi ed eventi dell’oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> sono identici o simili ai membri forniti dagli oggetti <xref:Microsoft.Office.Interop.Excel.Application> o <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Excel fornisce una raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> come proprietà di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook>. Ogni membro della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> può essere un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Gli strumenti di sviluppo di Office in Visual Studio estendono l’oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> fornendo il tipo <xref:Microsoft.Office.Tools.Excel.Worksheet>. Questo tipo consente di accedere a tutte le funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet>, nonché nuove funzionalità quali la possibilità di ospitare controlli gestiti e gestire i nuovi eventi. Per altre informazioni, vedere [elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
### <a name="range-object"></a>Oggetto Range  
 L’oggetto <xref:Microsoft.Office.Interop.Excel.Range> è quello più utilizzato nelle applicazioni di Excel. Prima di poter modificare un'area in Excel, è necessario esprimerlo come oggetto <xref:Microsoft.Office.Interop.Excel.Range> e utilizzare i metodi e le proprietà di tale intervallo. Un oggetto <xref:Microsoft.Office.Interop.Excel.Range> rappresenta una cella, una riga, una colonna, una selezione di celle contenenti uno o più blocchi di celle che possono o meno essere contigui o anche un gruppo di celle in più fogli.  
  
 Visual Studio estende l’oggetto <xref:Microsoft.Office.Interop.Excel.Range> fornendo i tipi <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Questi tipi hanno la maggior parte delle medesime funzionalità di un oggetto <xref:Microsoft.Office.Interop.Excel.Range>, nonché nuove funzionalità, quali la funzionalità di data binding, e nuovi eventi. Per altre informazioni, vedere [NamedRange control](../vsto/namedrange-control.md) e [controllo XmlMappedRange](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Uso della documentazione sul modello a oggetti di Excel  
 Per informazioni complete sul modello a oggetti di Excel, è possibile utilizzare il riferimento di assembly di interoperabilità primario di Excel e il riferimento del modello a oggetti VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Riferimento all'assembly di interoperabilità primario  
 Nella documentazione di riferimento dell’assembly di interoperabilità primario di Excel vengono descritti i tipi dell'assembly di interoperabilità primario per Excel. Questa documentazione è disponibile dal percorso seguente: [riferimento all'assembly di interoperabilità primario di Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Per altre informazioni sulla progettazione dei PIA Excel, ad esempio le differenze tra classi e interfacce nell'assembly di interoperabilità primario e sull'implementazione degli eventi nell'assembly di interoperabilità primario, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primaridiOffice](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Riferimento del modello a oggetti VBA  
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Excel esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimento del modello a oggetti Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Tutti gli oggetti e i membri del riferimento del modello a oggetti VBA corrispondono ai tipi e ai membri dell'assembly di interoperabilità primario di Excel. Ad esempio, l'oggetto foglio di lavoro nel riferimento del modello a oggetti VBA corrisponde alla <xref:Microsoft.Office.Interop.Excel.Worksheet> oggetto nell'assembly di interoperabilità primario di Excel. Sebbene il riferimento del modello a oggetti VBA fornisce esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA di questo riferimento per Visual Basic o Visual C#, se si desidera utilizzarlo in un progetto di Excel che è possibile creare tramite Visual Studio.  
  
### <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Soluzioni Excel](../vsto/excel-solutions.md)|Viene illustrato come creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Excel.|  
|[Lavorare con intervalli](../vsto/working-with-ranges.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con gli intervalli.|  
|[Usare i fogli di lavoro](../vsto/working-with-worksheets.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con i fogli di lavoro.|  
|[Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)|Vengono forniti esempi che illustrano come eseguire attività comuni con le cartelle di lavoro.|  
  
  