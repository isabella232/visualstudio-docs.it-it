---
title: Limitazioni dei controlli Windows Form nei Office documenti
description: Informazioni sulle limitazioni delle proprietà e dei metodi Windows Form nei Microsoft Office documenti.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8eddcb8273b1ff3c619de85c6f871d617d3c9a92
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082920"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitazioni dei controlli Windows Form nei Office documenti

Esistono alcune differenze tra i controlli Windows Forms aggiunti Microsoft Office documenti di Word o fogli di lavoro Microsoft Office Excel e i controlli Windows Forms aggiunti Windows Form. Ad esempio, quando si aggiunge un controllo a un documento, le proprietà come , e non si comportano <xref:Microsoft.Office.Tools.Word.Controls.Button> come ci si potrebbe <xref:System.Windows.Forms.Control.Dock> <xref:System.Windows.Forms.Control.Anchor> <xref:System.Windows.Forms.Control.TabIndex> aspettare.

Molte di queste differenze sono causate dal modo in cui i Windows Form sono ospitati nei documenti. Quando un Windows Form viene aggiunto a un documento, incorpora un controllo ActiveX che quindi ospita il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] controllo Windows Forms nel documento. Il Windows Form non è incorporato direttamente nel documento.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitazioni dei metodi e delle proprietà dei Windows Form

Esistono diversi metodi e proprietà dei controlli form di Windows che non funzionano allo stesso modo in un documento come in un form di Windows e, pertanto, è consigliabile non usare tali controlli. Ad esempio, l'impostazione di proprietà come e influisce solo sulla posizione del controllo rispetto al contenitore <xref:System.Windows.Forms.Control.Dock> ActiveX controllo anziché al <xref:System.Windows.Forms.Control.Anchor> documento. Di seguito è riportato un elenco di proprietà e metodi non supportati dei controlli Windows Form per Word e Excel:

- Proprietà non supportate dei Excel seguenti:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Metodi e proprietà non supportati dei controlli Word:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Non è inoltre possibile impostare la proprietà o Windows controlli Form in linea <xref:System.Windows.Forms.Control.Left> con il testo in un documento di <xref:System.Windows.Forms.Control.Top> Word. Windows I controlli form vengono aggiunti in linea con il testo nei casi seguenti:

- Si aggiunge un controllo a un documento di Word a livello di codice e si usa un metodo che specifica un intervallo per la posizione.

- Aggiungere un controllo Windows Form a un documento di Word in fase di progettazione. È possibile modificare questa impostazione modificando il controllo nella finestra di progettazione.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Differenze nei controlli Windows Form nei Office documenti

Windows I controlli form hanno in genere lo stesso comportamento in un documento Office come in un form Windows, ma esistono alcune differenze. La tabella seguente descrive le differenze esistenti per i Windows Form nei Office documenti.

|Funzionalità|Differenza|
|-------------------|----------------|
|Controllare l'ordine di tabulazione|Non è possibile scorrere i controlli posizionati in un Excel foglio di lavoro o in un documento di Word.|
|Raggruppamento di controlli|Non è possibile usare <xref:System.Windows.Forms.GroupBox> un controllo per contenere altri controlli in un Office documento. Quando si aggiungono più pulsanti di opzione direttamente al documento, i pulsanti di opzione non si escludono a vicenda. È possibile scrivere codice per fare in modo che i pulsanti di opzione si escludono a vicenda. Tuttavia, l'approccio preferito consiste nell'aggiungere i pulsanti di opzione a un controllo utente e quindi aggiungere il controllo utente al documento. Per altre informazioni, vedere l'esempio di controlli Word o l Excel di controlli di Office esempi [e procedure dettagliate di sviluppo.](../vsto/office-development-samples-and-walkthroughs.md)|
|Tipo di controllo|Windows Il wrapping dei controlli form usati nei documenti viene eseguito in una classe fornita da che fornisce ai controlli funzionalità aggiuntive specifiche del foglio di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Excel o del documento di Word. Ad esempio, se si dispone di un controllo **Button** in un foglio di lavoro Excel, assicurarsi di specificare il tipo come anziché quando si fa riferimento o si esegue il <xref:Microsoft.Office.Tools.Excel.Controls.Button> cast <xref:System.Windows.Forms.Button> dell'oggetto.|
|Posizione e dimensioni del controllo|Le dimensioni e la posizione del controllo sono determinate dalle proprietà che fanno parte del contenitore ActiveX controllo. Le ActiveX del controllo accettano valori diversi rispetto alle proprietà equivalenti di un controllo Windows Form. Quando si impostano le proprietà , , o di un controllo, questo viene misurato in punti `Top` `Left` anziché in `Height` `Width` pixel.|
|Controllare la posizione nei documenti di Word|Se si aggiungono controlli a un layout basato su flusso, tenere presente che i controlli verranno scorrono con il contenuto quando il contenuto cambia. Non è possibile ancorare il controllo a  un paragrafo quando lo si trascina dalla Casella degli strumenti perché il controllo viene aggiunto al documento di Word in linea con il testo. Se si usa un altro metodo per aggiungere il controllo, ad esempio facendo doppio clic sul controllo, il controllo viene inserito in base all'opzione di Word impostata per l'inserimento di immagini.<br /><br /> Non è possibile impostare `Left` la proprietà o di un controllo `Top` inline con testo.<br /><br /> Non è possibile inserire controlli in un'intestazione o in un piè di pagina o all'interno di un documento secondario.|
|Eventi di controllo|Quando il controllo viene selezionato, genera eventi nell'ordine seguente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Quando il controllo viene deselezionato, genera eventi nell'ordine seguente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Controllare il ridimensionamento|Quando si modifica l'impostazione di zoom di un documento su un valore diverso dal 100%, i controlli vengono disabilitati, anche se sembrano essere ridimensionati con il documento. Ad esempio, se si fa clic su un pulsante quando lo zoom del documento è al 130%, verrà visualizzato un messaggio che indica che il controllo è stato disabilitato fino a quando lo zoom non è impostato su 100%. I controlli funzioneranno correttamente quando si modifica lo zoom su 100%.|
|Controllare i valori delle proprietà|Anche se le proprietà dei controlli in Windows Form sono impostate su un valore intero, vengono impostate su un singolo controllo per i controlli in un documento di Word. In Excel, i valori delle proprietà dei controlli sono impostati su un valore double. Se la proprietà e di un controllo in un foglio di lavoro supera le dimensioni del foglio di lavoro o dello `Height` `Width` schermo, il valore viene troncato.|
|Ridimensionamento dei controlli|Se si ridimensiona un controllo nel documento usando uno degli otto quadratini di  ridimensionamento, le nuove dimensioni del controllo non vengono riflesse nella finestra Proprietà fino a quando il controllo non viene nuovamente selezionato.|
|Comportamento dei controlli|I controlli in un Excel foglio di lavoro potrebbero comportarsi in modo imprevedibile quando la finestra del foglio di lavoro viene suddivisa. Ad esempio, l'accesso a un oggetto nel foglio di lavoro <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> potrebbe essere disponibile solo in una delle finestre.|
|Denominazione dei controlli|Non è possibile usare parole riservate per assegnare un nome ai controlli. Ad esempio, se si aggiunge un oggetto a un foglio di lavoro e si modifica il nome in Sistema , si verificano <xref:Microsoft.Office.Tools.Excel.Controls.Button> errori quando si compila il progetto. |
|Aggiunta di controlli a livello di codice|Non usare il costruttore del controllo per aggiungere un controllo al documento in fase di esecuzione. Usare invece i metodi helper forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Ad esempio, usare il <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> metodo per aggiungere un pulsante a un foglio di lavoro. Se si vuole aggiungere un controllo non supportato da questi metodi helper, è possibile usare il `AddControl` metodo . Per altre informazioni, vedere [Aggiungere controlli a Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)|
|Copia dei controlli|Se si copia un controllo Windows Forms e lo si incolla in un documento in fase di esecuzione, un contenitore vuoto ActiveX controllo viene incollato nel documento. Il Windows Form non viene visualizzato nella nuova posizione e il codice dietro il controllo originale non viene copiato nel contenitore ActiveX controllo.|

## <a name="limitations-in-document-level-projects"></a>Limitazioni nei progetti a livello di documento

Alcune limitazioni dell'uso Windows i controlli Form nei documenti sono univoche per i progetti a livello di documento.

### <a name="control-support-at-design-time"></a>Supporto dei controlli in fase di progettazione

Alcuni Windows Form vengono rimossi  dalla casella degli strumenti quando un foglio di lavoro di Excel o un documento di Word è aperto nella finestra Visual Studio progettazione. Ciò è dovuto a limitazioni tecniche o perché la funzionalità è già disponibile all'interno di Word o Excel. i progetti Excel e Word supportano tutti i controlli Windows Forms  e altri componenti visualizzati nella casella degli strumenti quando il documento ha lo stato attivo ed è anche possibile aggiungere controlli di terze parti a un foglio di lavoro o a un documento.

> [!NOTE]
> Tutti i controlli vengono rimossi dalla casella **degli strumenti** quando un documento è protetto. Per informazioni sulla protezione dei documenti, vedere [Protezione dei documenti nelle soluzioni a livello di documento.](../vsto/document-protection-in-document-level-solutions.md)

> [!NOTE]
> I controlli di terze parti devono avere l'attributo impostato su true per <xref:System.Runtime.InteropServices.ComVisibleAttribute> poter essere usati in una Office soluzione. 

I controlli e i componenti seguenti non sono disponibili nella casella degli **strumenti**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Supporto per i controlli ActiveX legacy

Se si crea un progetto Office a livello di documento che usa un documento di Word esistente o una cartella di lavoro di Excel che contiene controlli ActiveX, la funzionalità dei controlli ActiveX non viene persa; Tuttavia, non è disponibile alcun supporto per l'aggiunta di nuovi ActiveX ai documenti dall'interno Visual Studio. Ad esempio, se il documento di  Word include un pulsante della casella degli strumenti Controllo che esegue una macro Visual Basic, Applications Edition (VBA), continuerà a eseguire la macro dopo che il documento è stato usato in un progetto Office. Tuttavia, è consigliabile rimuovere i ActiveX e le macro VBA e sostituirli con i Windows Form e il codice gestito.

## <a name="see-also"></a>Vedi anche

- [Controlli su Office documenti](../vsto/controls-on-office-documents.md)
- [Windows Panoramica dei controlli form Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Procedura: Aggiungere controlli form Windows a Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
