---
title: Comportamento nuovo o modificato con gli adapter editor | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194184"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportamento nuovo o modificato con gli adattatori di editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si aggiorna il codice scritto con le versioni precedenti dell'editor principale di Visual Studio e si prevede di utilizzare gli adattatori (o gli shim) dell'editor anziché utilizzare la nuova API, è necessario tenere presenti le differenze seguenti nel comportamento delle schede dell'editor rispetto all'editor principale precedente.  
  
## <a name="features"></a>Funzionalità  
  
#### <a name="using-setsite"></a>Utilizzo di SESITE ()  
 È necessario chiamare <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> quando si Cocreano buffer di testo, visualizzazioni di testo e finestre del codice prima di eseguire altre operazioni su di essi. Tuttavia, ciò non è necessario se si usa <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> per crearli, perché i metodi Create () di questo servizio chiamano <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hosting di IVsCodeWindow e IVsTextView nel proprio contenuto  
 È possibile ospitare sia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> che <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nel proprio contenuto usando la modalità Win32 o la modalità WPF. Tuttavia, è necessario tenere presente che esistono alcune differenze nelle due modalità.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Uso delle versioni Win32 e WPF di IVsCodeWindow  
 La finestra del codice dell'editor è derivata da <xref:Microsoft.VisualStudio.Shell.WindowPane> , che implementa l'interfaccia Win32 precedente e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> la nuova <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfaccia WPF. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metodo per creare un ambiente host basato su HWND oppure il <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> metodo per creare un ambiente di hosting WPF. L'editor sottostante usa sempre WPF, ma è possibile creare il tipo di riquadro della finestra che soddisfa i requisiti di hosting se si incorpora questo riquadro della finestra direttamente nel contenuto.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Uso delle versioni Win32 e WPF di IVsTextView  
 È possibile impostare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> su modalità Win32 o WPF.  
  
 Quando una factory dell'editor crea una visualizzazione di testo, per impostazione predefinita è ospitata in un HWND e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> restituisce un HWND. Non usare questa modalità per incorporare l'editor all'interno di un controllo WPF.  
  
 Per impostare una visualizzazione di testo in modalità WPF, è necessario chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> e passare <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> come uno dei flag di inizializzazione nel `InitView` parametro. È possibile ottenere <xref:System.Windows.FrameworkElement> chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 La modalità WPF differisce dalla modalità Win32 in due modi. In primo luogo, la visualizzazione di testo può essere ospitata in un contesto WPF. È possibile accedere al riquadro WPF eseguendo il cast <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> di a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> e chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . In secondo luogo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> restituisce comunque un HWND, ma questo HWND può essere utilizzato solo per controllarne la posizione e impostare lo stato attivo. Non è necessario utilizzare questo HWND per rispondere a un messaggio di WM_PAINT, perché non influirà sul modo in cui l'editor disegna la finestra. Questo HWND è presente solo per facilitare la transizione al nuovo codice dell'editor tramite gli adapter. Si consiglia di non utilizzare `VIF_NO_HWND_SUPPORT` se il componente richiede un HWND per funzionare, a causa delle limitazioni nell'HWND restituito da `GetWindowHandle` in questa modalità.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Passaggio di matrici come parametri nel codice nativo  
 Nell'API dell'editor legacy sono disponibili molti metodi con parametri che includono una matrice e il relativo conteggio. Alcuni esempi:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Se si chiamano questi metodi in codice nativo, è necessario passare un solo elemento alla volta. Se si passa più di un elemento, la chiamata verrà rifiutata, a causa di problemi con l'implementazione di interoperabilità primaria.  
  
 Il problema è più complesso con metodi quali <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . Ogni volta che viene chiamato questo metodo, cancella l'elenco precedente di tipi di marcatori ignorati, pertanto non è possibile semplicemente chiamare questo metodo tre volte con tre tipi di marcatori diversi. L'unico rimedio consiste nel chiamare questo metodo solo nel codice gestito.  
  
#### <a name="threading"></a>Threading  
 È necessario chiamare sempre l'adattatore del buffer dal thread UI. L'adattatore del buffer è un oggetto gestito, ovvero la chiamata al metodo dal codice gestito ignora il marshalling COM e la chiamata non viene sottoposta automaticamente a marshalling al thread dell'interfaccia utente.  Se si chiama l'adattatore del buffer da un thread in background, è necessario usare <xref:System.Windows.Threading.Dispatcher.Invoke%2A> o un metodo simile.  
  
#### <a name="lockbuffer-methods"></a>Metodi LockBuffer  
 Tutti i metodi LockBuffer () sono deprecati. Alcuni esempi:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Eventi di commit  
 Gli eventi di commit non sono supportati. La chiamata a un metodo che fornisce un Consiglio per questi eventi fa in modo che il metodo restituisca un codice di errore.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 L'oggetto <xref:EnvDTE.TextEditorEvents> non viene più attivato in commit (). Viene invece attivato ogni modifica del testo.  
  
#### <a name="text-markers"></a>Marcatori di testo  
 È necessario chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> sugli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> oggetti quando vengono rimossi. Nelle versioni precedenti era necessario solo rilasciare i marcatori.  
  
#### <a name="line-numbers"></a>Numeri di riga  
 Per diversi metodi su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> e, i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> numeri di riga corrispondono ai numeri di riga del buffer sottostante, non ai numeri di riga che determinano la struttura e il ritorno a capo automatico, come in Visual Studio 2008.  
  
 I metodi interessati includono quanto segue (l'elenco non è esaustivo):  
  
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
 I client di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> visualizzeranno solo le aree della struttura aggiunte mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . Non vedranno le aree ad hoc, perché non vengono aggiunte tramite gli adattatori dell'editor. In modo analogo, questi client non vedranno le aree della struttura aggiunte dalle lingue (incluso C# e C++) che usano il nuovo codice dell'editor anziché gli adattatori dell'editor.  
  
#### <a name="line-heights"></a>Altezze linea  
 Nel nuovo editor le righe di testo possono avere altezze diverse, a seconda delle dimensioni del carattere e delle possibili trasformazioni di riga che possono spostare la riga rispetto ad altre righe. L'altezza della riga restituita dai metodi, ad esempio, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> è l'altezza di una riga che utilizza la dimensione predefinita del carattere senza alcuna trasformazione di linea applicata. Questa altezza può indicare o meno l'altezza effettiva di una riga nella visualizzazione.  
  
#### <a name="eventing-and-undo"></a>Evento e annullamento  
 Nel nuovo editor, la visualizzazione continua a eseguire operazioni come il rendering e la generazione di eventi in modo continuo, anche quando viene aperto un cluster di annullamento. Questo comportamento è diverso da quello delle viste legacy, che non hanno eseguito tali operazioni fino alla chiusura del cluster di annullamento.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> metodo avrà esito negativo se si passa una classe che non implementa né <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . I popup personalizzati creati dal proprietario di Win32 non sono più supportati.  
  
#### <a name="smarttags"></a>Degli smart tag  
 Non è disponibile supporto dell'adapter per gli smart tag creati con le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> interfacce,, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> non è implementato.  
  
## <a name="unimplemented-methods"></a>Metodi non implementati  
 Alcuni metodi non sono stati implementati nell'adattatore del buffer di testo, nell'adattatore della visualizzazione di testo e nella scheda livello testo.  
  
|Interfaccia|Non implementato|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` non è implementato.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> viene implementato nelle schede, ma viene ignorato dall'interfaccia utente della struttura.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> viene implementato nelle schede, ma viene ignorato dall'interfaccia utente della struttura.|
