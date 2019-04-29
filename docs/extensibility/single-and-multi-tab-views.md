---
title: Viste a schede singole e multiple | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3676a19b5b5b7a4050a7d48385e76954ad0bcc96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62432884"
---
# <a name="single-and-multi-tab-views"></a>Visualizzazioni a schede singole e multiple
Un editor è possibile creare diversi tipi di viste. Un esempio è una finestra dell'editor di codice, un vantaggio è un progettista di moduli.

 Una vista a più schede è una vista che è presenti più schede. Ad esempio, l'editor HTML include due schede nella parte inferiore: **Progettazione** e **origine**, ognuna una vista logica. La visualizzazione di progettazione viene visualizzata una pagina web sottoposta a rendering, mentre l'altra consente di visualizzare il codice HTML che include la pagina web.

## <a name="accessing-physical-views"></a>Accesso alle visualizzazioni fisiche
 Le visualizzazioni fisiche ospitano gli oggetti di visualizzazione di documenti, ognuno dei quali rappresenta una visualizzazione dei dati nel buffer, ad esempio di codice o un modulo. Di conseguenza, ogni oggetto visualizzazione del documento ha una visualizzazione fisica (identificato da un elemento noto come una stringa di visualizzazione fisica) e in genere una singola visualizzazione logica.

 In alcuni casi, tuttavia, una visualizzazione fisica può avere due o più viste logiche. Alcuni esempi sono un editor che ha una finestra divisa con le visualizzazioni side-by-side, o una finestra di progettazione di form che dispone di una visualizzazione di progettazione/interfaccia utente grafica e una visualizzazione di code-behind-the-modulo.

 Per abilitare l'editor per accedere a tutte le visualizzazioni fisiche disponibili, è necessario creare una stringa di visualizzazione fisica univoco per ogni tipo di oggetto visualizzazione del documento che è possibile creare la factory dell'editor. Ad esempio, il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] factory dell'editor creare documento oggetti di visualizzazione per una finestra del codice e una finestra di progettazione form.

## <a name="creating-multi-tabbed-views"></a>Creazione di schede e viste
 Anche se un oggetto visualizzazione del documento deve essere associato a una visualizzazione fisica tramite una stringa di visualizzazione fisica univoco, è possibile inserire più schede all'interno della visualizzazione fisica per consentire la visualizzazione dei dati in modi diversi. In questa configurazione a più schede, tutte le schede sono associate con la stessa stringa di visualizzazione fisica, ma ogni scheda ha una visualizzazione logica diversi GUID.

 Per creare una vista a più schede per un editor, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> l'interfaccia e quindi associare una visualizzazione logica diversi GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) con ogni scheda è creare.

 L'editor HTML di Visual Studio è un esempio di un editor con una visualizzazione di multi-scheda. Dispone **Design** e **origine** schede. A tale scopo, è associata a ogni scheda, una vista logica diversa `LOGICALVIEWID_TextView` per il **Design** scheda e `LOGICALVIEWID_Code` per il **origine** scheda.

 Specificando la visualizzazione logica appropriata, un pacchetto VSPackage può accedere alla visualizzazione che corrisponde a uno scopo specifico, ad esempio si progetta un modulo, la modifica del codice o il debug del codice. Tuttavia, una delle finestre, deve essere identificata dalla stringa NULL e deve corrispondere alla visualizzazione logica primaria (`LOGVIEWID_Primary`).

 Nella tabella seguente sono elencati i valori di visualizzazione logica disponibili e il relativo utilizzo.

|GUID LOGVIEWID|Uso consigliato|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Visualizzazione predefinita/primaria della factory dell'editor.<br /><br /> Tutte le factory dell'editor deve supportare questo valore. In questa vista è necessario usare la stringa NULL come stringa di visualizzazione fisica. Almeno una visualizzazione logica deve essere impostata su questo valore.|
|`LOGVIEWID_Debugging`|Visualizzazione di debug. In genere `LOGVIEWID_Debugging` esegue il mapping alla stessa visualizzazione `LOGVIEWID_Code`.|
|`LOGVIEWID_Code`|Visualizzazione avviata per la **Visualizza codice** comando.|
|`LOGVIEWID_Designer`|Visualizzazione avviata per la **Visualizza modulo** comando.|
|`LOGVIEWID_TextView`|Visualizzazione dell'editor di testo. Si tratta della visualizzazione che restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, da cui è possibile accedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|`LOGVIEWID_UserChooseView`|Chiede all'utente di scegliere quale visualizzazione usare.|
|`LOGVIEWID_ProjectSpecificEditor`|Passato per il **aperta con** finestra di dialogo<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Quando l'utente sceglie la voce "(editor predefinito progetto)".|

 Sebbene la visualizzazione logica GUID sono estendibili, è possibile usare solo i GUID della visualizzazione logica definiti nel pacchetto VSPackage.

 Al momento della chiusura, Visual Studio consente di mantenere il GUID della factory dell'editor e le stringhe di visualizzazione fisica associate alla finestra di documento in modo che può essere utilizzato per aprire nuovamente le finestre dei documenti quando la soluzione viene riaperta. Solo le finestre che risultano aperte al momento della chiusura di una soluzione vengono rese persistenti nel file di soluzione (con estensione suo). Questi valori corrispondono al `VSFPROPID_guidEditorType` e `VSFPROPID_pszPhysicalView` valori passati i `propid` parametro nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> (metodo).

## <a name="example"></a>Esempio
 Questo frammento di codice viene illustrato come la <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> oggetto viene usato per accedere a una visualizzazione che implementa `IVsCodeWindow`. In questo caso, il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> servizio viene usato per chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> richiesta e `LOGVIEWID_TextView`, che ottiene un puntatore alla cornice della finestra. Un puntatore all'oggetto visualizzazione del documento viene ottenuto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> e specificando il valore `VSFPROPID_DocView`. Dall'oggetto di visualizzazione del documento `QueryInterface` viene chiamato per `IVsCodeWindow`. Si prevede in questo caso è che viene restituito un editor di testo e quindi l'oggetto visualizzazione del documento restituito nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo è una finestra del codice.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [Supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md)
- [Procedura: Collegare visualizzazioni ai dati documento](../extensibility/how-to-attach-views-to-document-data.md)
- [Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)