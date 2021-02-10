---
title: Visualizzazioni singole e a più schede | Microsoft Docs
description: Informazioni su come implementare visualizzazioni a più schede negli editor, ad esempio le finestre dell'editor di codice e una finestra di progettazione di form.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6cea04557fb0bf3075461b22979cac2168af322
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942984"
---
# <a name="single-and-multi-tab-views"></a>Visualizzazioni a schede singole e multiple
Un editor può creare tipi diversi di visualizzazioni. Un esempio è una finestra dell'editor di codice, un'altra è una finestra di progettazione di form.

 Una visualizzazione a più schede è una visualizzazione con più schede. Nell'editor HTML, ad esempio, sono presenti due schede nella parte inferiore: **progettazione** e **origine**, ciascuna di una visualizzazione logica. Nella visualizzazione progettazione viene visualizzata una pagina Web di cui è stato eseguito il rendering, mentre l'altra Visualizza il codice HTML che include la pagina Web.

## <a name="accessing-physical-views"></a>Accesso a visualizzazioni fisiche
 Le visualizzazioni fisiche ospitano oggetti visualizzazione del documento, ognuno dei quali rappresenta una visualizzazione dei dati nel buffer, ad esempio il codice o un form. Di conseguenza, ogni oggetto visualizzazione del documento dispone di una visualizzazione fisica, identificata da un elemento noto come stringa di visualizzazione fisica, e in genere una singola visualizzazione logica.

 In alcuni casi, tuttavia, una visualizzazione fisica può avere due o più visualizzazioni logiche. Alcuni esempi sono rappresentati da un editor che dispone di una finestra divisa con visualizzazioni affiancate oppure da una finestra di progettazione di form che dispone di una GUI/visualizzazione progettazione e una visualizzazione code-behind-the-form.

 Per consentire all'editor di accedere a tutte le visualizzazioni fisiche disponibili, è necessario creare una stringa di visualizzazione fisica univoca per ogni tipo di oggetto visualizzazione del documento che può essere creato dalla factory dell'editor. Ad esempio, la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Factory dell'editor può creare oggetti visualizzazione documento per una finestra del codice e una finestra di progettazione dei form.

## <a name="creating-multi-tabbed-views"></a>Creazione di visualizzazioni a più schede
 Sebbene sia necessario associare un oggetto visualizzazione documento a una visualizzazione fisica tramite una stringa di visualizzazione fisica univoca, è possibile inserire più schede nella visualizzazione fisica per consentire la visualizzazione dei dati in modi diversi. In questa configurazione a più schede, tutte le schede sono associate alla stessa stringa di visualizzazione fisica, ma a ogni scheda viene assegnato un GUID di visualizzazione logica diverso.

 Per creare una visualizzazione a più schede per un editor, implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> interfaccia e quindi associare un GUID di visualizzazione logica diverso ( <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> ) a ogni scheda creata.

 L'editor HTML di Visual Studio è un esempio di editor con una visualizzazione a più schede. Contiene schede di **progettazione** e di **origine** . Per abilitare questa impostazione, una visualizzazione logica diversa è associata a ogni scheda, `LOGICALVIEWID_TextView` per la scheda **progettazione** e `LOGICALVIEWID_Code` per la scheda **origine** .

 Specificando la visualizzazione logica appropriata, un pacchetto VSPackage può accedere alla vista che corrisponde a uno scopo specifico, ad esempio la progettazione di un modulo, la modifica di codice o il debug di codice. Tuttavia, una delle finestre deve essere identificata dalla stringa NULL e deve corrispondere alla visualizzazione logica primaria ( `LOGVIEWID_Primary` ).

 Nella tabella seguente sono elencati i valori di visualizzazione logica disponibili e il relativo utilizzo.

|GUID LOGVIEWID|Uso consigliato|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Visualizzazione predefinita/principale della factory dell'editor.<br /><br /> Tutte le factory dell'editor devono supportare questo valore. Questa vista deve usare la stringa NULL come stringa di visualizzazione fisica. È necessario impostare almeno una visualizzazione logica su questo valore.|
|`LOGVIEWID_Debugging`|Visualizzazione di debug. Viene in genere eseguito `LOGVIEWID_Debugging` il mapping alla stessa visualizzazione di `LOGVIEWID_Code` .|
|`LOGVIEWID_Code`|Visualizzazione avviata dal comando **Visualizza codice** .|
|`LOGVIEWID_Designer`|Visualizzazione avviata dal comando **Visualizza modulo** .|
|`LOGVIEWID_TextView`|Visualizzazione dell'editor di testo. Si tratta della vista che restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> , da cui è possibile accedere a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|`LOGVIEWID_UserChooseView`|Richiede all'utente di scegliere la visualizzazione da usare.|
|`LOGVIEWID_ProjectSpecificEditor`|Passato dalla finestra di dialogo **Apri con con**<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Quando l'utente sceglie la voce "(editor predefinito progetto)".|

 Sebbene i GUID della visualizzazione logica siano estendibili, è possibile usare solo i GUID della visualizzazione logica definiti nel pacchetto VSPackage.

 All'arresto, Visual Studio mantiene il GUID della factory dell'editor e le stringhe di visualizzazione fisiche associate alla finestra del documento, in modo che possa essere usato per riaprire le finestre dei documenti quando la soluzione viene riaperta. Solo le finestre aperte quando una soluzione viene chiusa vengono rese permanente nel file della soluzione (. suo). Questi valori corrispondono ai `VSFPROPID_guidEditorType` valori e `VSFPROPID_pszPhysicalView` passati nel `propid` parametro nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo.

## <a name="example"></a>Esempio
 Questo frammento di codice illustra come <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> viene usato l'oggetto per accedere a una vista che implementa `IVsCodeWindow` . In questo caso, il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> servizio viene utilizzato per chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> e richiedere `LOGVIEWID_TextView` , ottenendo un puntatore a una cornice della finestra. Un puntatore all'oggetto visualizzazione del documento viene ottenuto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> e specificando il valore `VSFPROPID_DocView` . Dall'oggetto visualizzazione del documento, `QueryInterface` viene chiamato per `IVsCodeWindow` . In questo caso si prevede che venga restituito un editor di testo, quindi l'oggetto visualizzazione del documento restituito nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo è una finestra del codice.

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

## <a name="see-also"></a>Vedi anche
- [Supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md)
- [Procedura: Collegare visualizzazioni ai dati documento](../extensibility/how-to-attach-views-to-document-data.md)
- [Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)
