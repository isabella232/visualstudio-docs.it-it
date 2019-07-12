---
title: Limitazioni dei controlli Windows Form nei documenti di Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d5cb4bf5788e1d30933a807e2e97e064118fc076
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823404"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitazioni dei controlli Windows Form nei documenti di Office

Esistono alcune differenze tra i controlli Windows Form che vengono aggiunti ai documenti di Microsoft Office Word o fogli di lavoro di Microsoft Office Excel e controlli Windows Form che vengono aggiunti a un Windows Form. Ad esempio, quando si aggiunge un <xref:Microsoft.Office.Tools.Word.Controls.Button> controllo a un documento, proprietà, ad esempio <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, e <xref:System.Windows.Forms.Control.TabIndex> non funzionano come previsto.

Molte di queste differenze sono causate dal modo tale form di Windows sono ospitati i controlli nei documenti. Quando un controllo Windows Form viene aggiunto a un documento, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incorpora un controllo ActiveX che quindi ospita il controllo Windows Form nel documento. Il controllo Windows Form non è incorporato direttamente nel documento.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitazioni di metodi e proprietà dei controlli Windows Form

Sono disponibili numerosi metodi e proprietà dei controlli Windows Form che non funzionano allo stesso modo in un documento in un modulo di Windows e, pertanto, si consiglia di non essere utilizzati. Ad esempio, impostare proprietà quali <xref:System.Windows.Forms.Control.Dock> e <xref:System.Windows.Forms.Control.Anchor> interessa solo la posizione del controllo rispetto al controllo ActiveX contenitore, piuttosto che il documento. Di seguito è riportato un elenco di metodi non supportati e le proprietà dei controlli Windows Form per Word ed Excel:

- Non supportata delle proprietà dei controlli di Excel:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Metodi non supportati e le proprietà dei controlli di Word:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Inoltre, non è possibile impostare il <xref:System.Windows.Forms.Control.Left> o <xref:System.Windows.Forms.Control.Top> proprietà dei controlli Windows Form che sono in linea con testo in un documento di Word. Controlli Windows Form vengono aggiunti in linea con il testo nei casi seguenti:

- A livello di codice aggiungere un controllo a un documento di Word e usare un metodo che specifica un intervallo per il percorso.

- Aggiungere un controllo Windows Form a un documento di Word in fase di progettazione. È possibile modificare questo modificando il controllo nella finestra di progettazione.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Differenze nei controlli Windows Form nei documenti di Office

Controlli Windows Form in genere hanno lo stesso comportamento su un documento di Office come avviene in un Windows Form, ma esistono alcune differenze. Nella tabella seguente vengono descritte le differenze presenti per i controlli Windows Form nei documenti di Office.

|Funzionalità|Differenza|
|-------------------|----------------|
|Ordine di tabulazione di controllo|È Impossibile schede tramite i controlli inseriti in un foglio di lavoro di Excel o un documento di Word.|
|Raggruppamento dei controlli|Non è possibile usare un <xref:System.Windows.Forms.GroupBox> controllo per includere altri controlli in un documento di Office. Quando si aggiungono più pulsanti di opzione direttamente al documento, pulsanti di opzione non si escludono a vicenda. È possibile scrivere codice per rendere i pulsanti di opzione che si escludono a vicenda. Tuttavia, l'approccio consigliato consiste nell'aggiungere i pulsanti di opzione in un controllo utente e quindi aggiungere il controllo utente al documento. Per altre informazioni, vedere l'esempio relativo ai controlli Word o Excel di esempio di controlli al [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).|
|Tipo di controllo|Vengono eseguito il wrapping di controlli Windows Form nei documenti in una classe fornita dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i controlli che offre funzionalità aggiuntive specifiche per il foglio di lavoro di Excel o un documento di Word. Ad esempio, se si dispone di un **sul pulsante** control per un foglio di lavoro di Excel, assicurarsi di specificare il tipo di <xref:Microsoft.Office.Tools.Excel.Controls.Button> anziché <xref:System.Windows.Forms.Button> quando si fa riferimento o il cast dell'oggetto.|
|Posizione del controllo e le dimensioni|Le dimensioni e posizione del controllo è determinato dalle proprietà che fanno parte del contenitore di controlli ActiveX. Le proprietà del controllo ActiveX richiedere valori diversi da quelli di proprietà equivalenti di un controllo Windows Form. Quando si imposta la `Top`, `Left`, `Height`, o `Width` le proprietà di un controllo, viene calcolato in punti, invece di pixel.|
|Posizione del controllo nei documenti di Word|Se si aggiungono controlli a un layout in base al flusso, tenere presente che i controlli di flusso con il contenuto come le modifiche del contenuto. Non è possibile ancorare il controllo a un paragrafo quando si trascina dal **casella degli strumenti** perché il controllo viene aggiunto al documento di Word in linea con il testo. Se si usa un altro metodo per aggiungere il controllo, ad esempio facendo doppio clic su controllo, il controllo viene inserito in base all'opzione Word che è stato impostato per l'inserimento di immagini.<br /><br /> Non è possibile impostare il `Left` o `Top` proprietà di un controllo che è in linea con il testo.<br /><br /> È possibile posizionare i controlli in un'intestazione o piè di pagina o di un documento secondario.|
|Eventi di controllo|Quando il controllo è selezionato, vengono generati eventi nell'ordine seguente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Quando il controllo è deselezionato, vengono generati eventi nell'ordine seguente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Controllo ridimensionamento|Quando si modifica l'impostazione dello zoom di un documento su un valore qualsiasi diverso da 100%, i controlli sono disabilitati, anche se sembrano scala con il documento. Ad esempio, se si sceglie un pulsante quando il documento è in 130% zoom, un messaggio indicherà che il controllo è stato disabilitato finché non viene impostato lo zoom al 100%. I controlli funzionerà correttamente quando si modifica il valore di zoom al 100%.|
|Valori delle proprietà di controllo|Anche se le proprietà dei controlli in un Windows Form sono impostate su un valore intero, sono configurati per un singolo per i controlli in un documento di Word. In Excel, i valori delle proprietà dei controlli sono impostati in un valore double. Se il `Height` e `Width` proprietà di un controllo in un foglio di lavoro superano le dimensioni del foglio di lavoro o dello schermo, il valore viene troncato.|
|Ridimensionamento del controllo|Se si ridimensiona un controllo nel documento usando uno dei quadratini di ridimensionamento di otto, le nuove dimensioni del controllo non vengono riflesse nel **proprietà** finestra fino a quando non si seleziona di nuovo il controllo.|
|Controllare il comportamento|Controlli in un foglio di lavoro di Excel potrebbero comportarsi in modo imprevedibile quando la finestra del foglio di lavoro viene diviso. Ad esempio, accedere a un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> nel foglio di lavoro potrebbe essere disponibile solo in una delle finestre.|
|Denominazione di controllo|È possibile utilizzare parole riservate per i nomi dei controlli. Ad esempio, se si aggiunge un <xref:Microsoft.Office.Tools.Excel.Controls.Button> a un foglio di lavoro e denominarlo **sistema**, si verificano errori quando si compila il progetto.|
|Aggiunta di controlli a livello di codice|Non utilizzare il costruttore del controllo per aggiungere un controllo al documento in fase di esecuzione. Usare invece i metodi di supporto forniti dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ad esempio, usare il <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> per aggiungere un pulsante in un foglio di lavoro. Se si desidera aggiungere un controllo che non è supportato da questi metodi di supporto, è possibile usare il `AddControl` (metodo). Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Copia i controlli|Se si copia un controllo Windows Form e incollarlo in un documento in fase di esecuzione, un contenitore vuoto controllo ActiveX viene incollato nel documento. Il controllo Windows Form non vengono visualizzati nella nuova posizione e code-behind del controllo originale non viene copiato nel contenitore di controlli ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Limitazioni nei progetti a livello di documento

Alcune delle limitazioni dell'uso di controlli Windows Form nei documenti sono univoche per i progetti a livello di documento.

### <a name="control-support-at-design-time"></a>Supporto per il controllo in fase di progettazione

Alcuni controlli Windows Form vengono rimossi dal **casella degli strumenti** quando un foglio di lavoro di Excel o un documento di Word è aperto nella finestra di progettazione di Visual Studio. A causa di limitazioni tecniche o perché la funzionalità è già disponibile all'interno di Word o Excel. I progetti di Excel e Word supportano tutti i controlli Windows Form e altri componenti che vengono visualizzati nei **casella degli strumenti** quando il documento dispone dello stato attivo ed è anche possibile aggiungere controlli di terze parti a un documento o foglio di lavoro.

> [!NOTE]
> Tutti i controlli vengono rimossi dal **casella degli strumenti** quando un documento è protetto. Per informazioni sulla protezione di documenti, vedere [documentare la protezione nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Controlli di terze parti devono avere la <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributo è impostato su **true** per poter essere usato in una soluzione Office.

I controlli e i componenti seguenti non sono disponibili nel **casella degli strumenti**:

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

### <a name="support-for-legacy-activex-controls"></a>Supporto per controlli ActiveX legacy

Se si crea un progetto di Office a livello di documento che usa un documento Word esistente o una cartella di lavoro di Excel che contiene i controlli ActiveX, le funzionalità dei controlli ActiveX non andrà persa. Tuttavia, non vi è alcun supporto per l'aggiunta di nuovi controlli ActiveX ai documenti all'interno di Visual Studio. Ad esempio, se il documento di Word contiene un pulsante dal **controllo** della casella degli strumenti che esegue una macro Applications (VBA) Visual Basic, continuerà a eseguire la macro dopo che il documento è stato usato in un progetto di Office. Tuttavia, è consigliabile rimuovere i controlli ActiveX e le macro VBA e sostituirli con i controlli Windows Form e codice gestito.

## <a name="see-also"></a>Vedere anche

- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Controlli Windows Form in panoramica di documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
