---
title: Comportamento nuovo o modificato con schede dell'Editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194184"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportamento nuovo o modificato con gli adattatori di editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si sta aggiornando il codice che è stato scritto in versioni precedenti dell'editor principale di Visual Studio e si prevede di usare l'editor schede (o gli shim) invece di usare la nuova API, è necessario considerare le seguenti differenze nel comportamento delle schede dell'editor Per quanto riguarda l'editor principale precedente.  
  
## <a name="features"></a>Funzionalità  
  
#### <a name="using-setsite"></a>Usando SetSite)  
 È necessario chiamare <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> quando si creare buffer di testo, le visualizzazioni di testo e finestre del codice prima di eseguire altre operazioni su di essi. Tuttavia, ciò non è necessario se si usa la <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> crearli, poiché i metodi Create () di questo servizio autonomamente chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hosting oggetto IVsCodeWindow e IVsTextView nel proprio contenuto  
 È possibile ospitare entrambi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nel proprio contenuto usando la modalità di Win32 o WPF. È tuttavia necessario tenere presente che esistono alcune differenze nelle due modalità.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Con le versioni di Win32 e WPF di oggetto IVsCodeWindow  
 Finestra del codice dell'editor è derivata da <xref:Microsoft.VisualStudio.Shell.WindowPane>, che implementa il meno recente Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> dell'interfaccia, nonché il nuovo controllo WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfaccia. È possibile usare la <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metodo per creare un ambiente di hosting basato su HWND, o <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> metodo per creare un ambiente di hosting di WPF. L'editor sottostante Usa sempre WPF, ma è possibile creare il tipo di riquadro della finestra che si adatta alle esigenze di hosting se si intende incorporare questo riquadro della finestra direttamente nel proprio contenuto.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Con le versioni di Win32 e WPF di IVsTextView  
 È possibile impostare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> alla modalità di Win32 o WPF.  
  
 Quando una factory dell'editor crea una visualizzazione di testo, per impostazione predefinita è ospitato in un oggetto HWND, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> restituisce un oggetto HWND. È consigliabile usare questa modalità per incorporare l'editor all'interno di un controllo WPF.  
  
 Per impostare una visualizzazione di testo alla modalità WPF, è necessario chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> e passare <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> come uno dell'inizializzazione flag nel `InitView` parametro. È possibile ottenere il <xref:System.Windows.FrameworkElement> chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Modalità WPF è diversa dalla modalità Win32 in due modi. In primo luogo, la visualizzazione di testo può essere ospitata in un contesto WPF. È possibile accedere al riquadro WPF eseguendo il cast di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> e la chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Secondo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> comunque restituisce un oggetto HWND, ma questo HWND può essere usato solo per controllare la posizione e impostare lo stato attivo su di esso. È necessario utilizzare questo oggetto HWND per rispondere a un messaggio WM_PAINT, non perché non verranno influenzati, come l'editor consente di disegnare la finestra. Oggetto HWND è presente solo per agevolare la transizione al nuovo editor di codice tramite gli adapter. Si consiglia vivamente che non è consigliabile usare `VIF_NO_HWND_SUPPORT` se il componente richiede un oggetto HWND, a causa di limitazioni nell'HWND restituito da `GetWindowHandle` in questa modalità.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Passaggio di matrici come parametri nel codice nativo  
 Esistono molti metodi nell'API legacy editor che dispongono di parametri che includono una matrice e il relativo conteggio. Alcuni esempi:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Se si chiama questi metodi nel codice nativo, è necessario passare in un solo elemento alla volta. Se si passa più di un elemento, la chiamata verrà rifiutata, a causa di problemi con l'implementazione di interoperabilità primario.  
  
 Il problema è più complesso con i metodi, ad esempio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Ogni volta che viene chiamato questo metodo, Cancella l'elenco precedente dei tipi di marcatore verrà ignorata, pertanto non è possibile semplicemente chiamare questo metodo per tre volte con tre tipi di marcatore diverso. L'unico rimedio consiste nel chiamare questo metodo solo nel codice gestito.  
  
#### <a name="threading"></a>Threading  
 È necessario chiamare l'adattatore del buffer sempre dal thread dell'interfaccia utente. L'adattatore del buffer è un oggetto gestito, che significa che la chiamata al suo interno dal codice gestito possono ignorare il marshalling COM e la chiamata verrà automaticamente effettuare il marshalling al thread dell'interfaccia utente.  Se si chiama l'adattatore del buffer da un thread in background, è necessario usare <xref:System.Windows.Threading.Dispatcher.Invoke%2A> o un metodo simile.  
  
#### <a name="lockbuffer-methods"></a>Metodi LockBuffer  
 Tutti i metodi LockBuffer() sono deprecati. Alcuni esempi:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Eseguire il commit di eventi  
 Eseguire il commit degli eventi non sono supportati. Chiamare il metodo che informa che per questi eventi, il metodo restituire un codice di errore.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 Il <xref:EnvDTE.TextEditorEvents> non vengono attivati su Commit (). Vengono invece attivati in ogni modifica del testo.  
  
#### <a name="text-markers"></a>Marcatori di testo  
 È necessario chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> oggetti quando vengono rimossi. Nelle versioni precedenti, è necessario solo per i marcatori di rilascio.  
  
#### <a name="line-numbers"></a>Numeri di riga  
 Per un'ampia gamma di metodi su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, i numeri di riga corrispondono ai numeri di riga del buffer sottostante, i numeri di riga non tale fattore nella struttura e di ritorno a capo automatico, come in Visual Studio 2008.  
  
 I metodi interessati includono i seguenti (nell'elenco non è completo):  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>struttura  
 I client di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> visualizzeranno solo le aree della struttura che sono stati aggiunti utilizzando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Non visualizzeranno le aree ad hoc, perché non vengono aggiunte tramite le schede dell'editor. Analogamente, questi client non verranno visualizzato aggiunte dai linguaggi (inclusi i linguaggi c# e C++) che utilizzano il nuovo editor di codice piuttosto che le schede dell'editor di aree della struttura.  
  
#### <a name="line-heights"></a>Altezza delle righe  
 Nel nuovo editor, le righe di testo possono avere altezza diversa, a seconda della dimensione del carattere e trasformazioni di riga possibili che possono spostare la riga relativa alle altre linee. L'altezza della riga restituita dai metodi, ad esempio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> corrisponde all'altezza di una riga con le dimensioni del carattere predefinito non trasformazioni di riga applicate. Questa altezza può o potrebbe non riflettere l'effettivo altezza di una riga nella vista.  
  
#### <a name="eventing-and-undo"></a>Gestione degli eventi e annullamento  
 Nel nuovo editor, la visualizzazione continua a eseguire operazioni quali il rendering e la generazione di eventi in modo continuo, anche quando un cluster di annullamento è aperto. Questo comportamento è diverso da quello delle visualizzazioni legacy, che non ha eseguito le operazioni fino a quando non dopo la chiusura del cluster di annullamento.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> metodo avrà esito negativo se si passa in una classe che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. I popup proprietario Win32 personalizzati non sono più supportati.  
  
#### <a name="smarttags"></a>SmartTags  
 Non è supportata per gli smart tag creati con adapter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfacce.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> Non è implementata.  
  
## <a name="unimplemented-methods"></a>Metodi non implementati  
 Alcuni metodi non sono stati implementati nell'adattatore del buffer di testo, adattatore della visualizzazione di testo e adattatore del livello di testo.  
  
|Interfaccia|Non implementato|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` Non è implementata.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> viene implementata negli adapter ma ignorato dall'interfaccia utente della struttura.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> viene implementata negli adapter ma ignorato dall'interfaccia utente della struttura.|
