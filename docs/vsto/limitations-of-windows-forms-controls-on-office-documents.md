---
title: Limitazioni dei controlli Windows Forms nei documenti di Office
description: Informazioni sulle limitazioni dei metodi e delle proprietà di controllo Windows Forms nei documenti di Microsoft Office.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63459f4daf1f9fe717946491a997ba47510fbab8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524453"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitazioni dei controlli Windows Forms nei documenti di Office

Esistono alcune differenze tra i controlli Windows Forms aggiunti ai documenti Microsoft Office Word o Microsoft Office fogli di lavoro di Excel e Windows Forms i controlli aggiunti a Windows Forms. Ad esempio, quando si aggiunge un <xref:Microsoft.Office.Tools.Word.Controls.Button> controllo a un documento, le proprietà come <xref:System.Windows.Forms.Control.Dock> , <xref:System.Windows.Forms.Control.Anchor> e non <xref:System.Windows.Forms.Control.TabIndex> si comportano come previsto.

Molte di queste differenze sono causate dalla modalità di hosting dei controlli Windows Forms nei documenti. Quando un controllo Windows Forms viene aggiunto a un documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incorpora un controllo ActiveX che quindi ospita il controllo Windows Forms nel documento. Il controllo Windows Forms non è incorporato direttamente nel documento.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitazioni dei metodi e delle proprietà dei controlli Windows Forms

Esistono diversi metodi e proprietà dei controlli Windows Forms che non funzionano allo stesso modo in un documento come in un Windows Form e, pertanto, è consigliabile non usarli. Ad esempio, l'impostazione di proprietà come <xref:System.Windows.Forms.Control.Dock> e <xref:System.Windows.Forms.Control.Anchor> influisca solo sulla posizione del controllo rispetto al controllo ActiveX del contenitore, anziché sul documento. Di seguito è riportato un elenco di proprietà e metodi non supportati di controlli Windows Forms per Word ed Excel:

- Proprietà non supportate dei controlli di Excel:

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

Non è inoltre possibile impostare <xref:System.Windows.Forms.Control.Left> la <xref:System.Windows.Forms.Control.Top> proprietà o di Windows Forms controlli che sono in linea con il testo in un documento di Word. I controlli Windows Forms vengono aggiunti in linea con il testo nei casi seguenti:

- Si aggiunge a livello di codice un controllo a un documento di Word e si usa un metodo che specifica un intervallo per la posizione.

- Si aggiunge un controllo Windows Forms a un documento di Word in fase di progettazione. È possibile modificare questa impostazione modificando il controllo nella finestra di progettazione.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Differenze nei controlli Windows Forms nei documenti di Office

I controlli Windows Forms in genere hanno lo stesso comportamento in un documento di Office, come avviene in un Windows Form, ma esistono alcune differenze. Nella tabella seguente vengono descritte le differenze esistenti per Windows Forms controlli nei documenti di Office.

|Funzionalità|Differenza|
|-------------------|----------------|
|Ordine di tabulazione del controllo|Non è possibile scorrere i controlli posizionati in un foglio di lavoro di Excel o in un documento di Word.|
|Raggruppamento di controlli|Non è possibile usare un <xref:System.Windows.Forms.GroupBox> controllo per contenere altri controlli in un documento di Office. Quando si aggiungono più pulsanti di opzione direttamente al documento, i pulsanti di opzione non si escludono a vicenda. È possibile scrivere codice per rendere i pulsanti di opzione che si escludono a vicenda; Tuttavia, l'approccio migliore consiste nell'aggiungere i pulsanti di opzione a un controllo utente e quindi aggiungere il controllo utente al documento. Per ulteriori informazioni, vedere l'esempio relativo ai controlli di Word o ai controlli Excel in [esempi e procedure dettagliate per lo sviluppo di Office](../vsto/office-development-samples-and-walkthroughs.md).|
|Tipo di controllo|Windows Forms controlli utilizzati nei documenti vengono incapsulati in una classe fornita da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che fornisce ai controlli funzionalità aggiuntive specifiche del foglio di lavoro di Excel o del documento di Word. Se, ad esempio, si dispone di un controllo **Button** in un foglio di lavoro di Excel, assicurarsi di specificare il tipo come <xref:Microsoft.Office.Tools.Excel.Controls.Button> anziché quando si fa riferimento o si esegue <xref:System.Windows.Forms.Button> il cast dell'oggetto.|
|Posizione e dimensioni del controllo|Le dimensioni e la posizione del controllo sono determinate dalle proprietà che fanno parte del controllo ActiveX del contenitore. Le proprietà del controllo ActiveX accettano valori diversi dalle proprietà equivalenti di un controllo Windows Forms. Quando si impostano le `Top` `Left` proprietà,, `Height` o `Width` di un controllo, questo viene misurato in punti, anziché in pixel.|
|Posizione del controllo sui documenti di Word|Se si aggiungono controlli a un layout basato sul flusso, tenere presente che i controlli vengono propagati con il contenuto quando il contenuto cambia. Non è possibile ancorare il controllo a un paragrafo quando lo si trascina dalla **casella degli strumenti** perché il controllo viene aggiunto al documento di Word in linea con il testo. Se si usa un altro metodo per aggiungere il controllo, ad esempio facendo doppio clic sul controllo, il controllo viene inserito in base all'opzione Word impostata per l'inserimento di immagini.<br /><br /> Non è possibile impostare `Left` la `Top` proprietà o di un controllo inline con testo.<br /><br /> Non è possibile inserire i controlli in un'intestazione o in un piè di pagina o in un documento secondario.|
|Eventi di controllo|Quando il controllo è selezionato, genera eventi nell'ordine seguente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Quando il controllo viene deselezionato, genera eventi nell'ordine seguente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Ridimensionamento del controllo|Quando si modifica l'impostazione di zoom di un documento su un valore diverso da 100%, i controlli sono disabilitati, sebbene risultino ridimensionati con il documento. Se, ad esempio, si fa clic su un pulsante quando lo zoom del documento è al 130%, verrà visualizzato un messaggio che indica che il controllo è stato disabilitato fino a quando lo zoom è impostato su 100%. I controlli funzioneranno correttamente quando si imposta lo zoom su 100%.|
|Controllare i valori delle proprietà|Sebbene le proprietà dei controlli in un Windows Form siano impostate su un valore integer, vengono impostate su un singolo oggetto per i controlli in un documento di Word. In Excel, i valori della proprietà dei controlli sono impostati su un valore Double. Se la `Height` `Width` proprietà e di un controllo in un foglio di controllo supera le dimensioni del foglio di foglio o dello schermo, il valore viene troncato.|
|Ridimensionamento del controllo|Se si ridimensiona un controllo nel documento utilizzando uno degli otto quadratini di ridimensionamento, le nuove dimensioni del controllo non vengono riflesse nella finestra **Proprietà** fino a quando il controllo non viene riselezionato.|
|Comportamento del controllo|I controlli in un foglio di lavoro di Excel potrebbero comportarsi in modo imprevedibile quando la finestra del foglio di lavoro è Ad esempio, è possibile che l'accesso a un oggetto nel <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> foglio di foglio sia disponibile solo in una delle finestre.|
|Denominazione dei controlli|Non è possibile usare parole riservate per denominare i controlli. Se ad esempio si aggiunge un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.Button> a un foglio di lavoro e si modifica il nome in **System**, si verificano errori durante la compilazione del progetto.|
|Aggiunta di controlli a livello di codice|Non usare il costruttore del controllo per aggiungere un controllo al documento in fase di esecuzione. Usare invece i metodi helper forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Ad esempio, usare il <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> metodo per aggiungere un pulsante a un foglio di foglio. Se si desidera aggiungere un controllo non supportato da questi metodi helper, è possibile utilizzare il `AddControl` metodo. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Copia di controlli|Se si copia un controllo Windows Forms e lo si incolla in un documento in fase di esecuzione, nel documento viene incollato un controllo ActiveX contenitore vuoto. Il controllo Windows Forms non viene visualizzato nella nuova posizione e il codice dietro il controllo originale non viene copiato nel controllo ActiveX del contenitore.|

## <a name="limitations-in-document-level-projects"></a>Limitazioni nei progetti a livello di documento

Alcune limitazioni dell'utilizzo di controlli Windows Forms sui documenti sono univoche per i progetti a livello di documento.

### <a name="control-support-at-design-time"></a>Controllo del supporto in fase di progettazione

Alcuni controlli Windows Forms vengono rimossi dalla **casella degli strumenti** quando si apre un foglio di lavoro di Excel o un documento di Word nella finestra di progettazione di Visual Studio. Questo è dovuto a limitazioni tecniche o perché la funzionalità è già disponibile in Word o Excel. I progetti di Excel e Word supportano tutti i controlli Windows Forms e altri componenti visualizzati nella **casella degli strumenti** quando il documento ha lo stato attivo ed è anche possibile aggiungere controlli di terze parti a un foglio di lavoro o a un documento.

> [!NOTE]
> Tutti i controlli vengono rimossi dalla **casella degli strumenti** quando un documento è protetto. Per informazioni sulla protezione dei documenti, vedere la pagina relativa [alla protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Per poter essere usati in una soluzione Office, i controlli di terze parti devono avere l' <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributo impostato su **true** .

I controlli e i componenti seguenti non sono disponibili nella **casella degli strumenti**:

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

Se si crea un progetto di Office a livello di documento che usa un documento di Word o una cartella di lavoro di Excel esistente che contiene controlli ActiveX, la funzionalità dei controlli ActiveX non viene persa. Tuttavia, non è disponibile alcun supporto per l'aggiunta di nuovi controlli ActiveX ai documenti dall'interno di Visual Studio. Se, ad esempio, il documento di Word include un pulsante dalla casella degli strumenti del **controllo** che esegue una macro Visual Basic, Applications Edition (VBA), continuerà a eseguire la macro dopo che il documento è stato usato in un progetto di Office. Tuttavia, è consigliabile rimuovere i controlli ActiveX e le macro VBA e sostituirli con controlli Windows Forms e codice gestito.

## <a name="see-also"></a>Vedere anche

- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Cenni preliminari sui controlli Windows Forms nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Procedura: aggiungere controlli Windows Forms ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
