---
title: Viste a scheda singola e a più schede Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699983"
---
# <a name="single-and-multi-tab-views"></a>Visualizzazioni a schede singole e multiple
Un editor può creare diversi tipi di viste. Un esempio è una finestra dell'editor di codice, un altro è una finestra di progettazione di form.

 Una vista a più schede è una vista con più schede. Ad esempio, l'editor HTML dispone di due schede nella parte inferiore: **Progettazione** e **Origine**, ognuna una visualizzazione logica. La visualizzazione Progettazione visualizza una pagina Web sottoposta a rendering, mentre l'altra visualizza il codice HTML che comprende la pagina Web.

## <a name="accessing-physical-views"></a>Accesso alle viste fisiche
 Le visualizzazioni fisiche ospitano oggetti visualizzazione documento, ognuno dei quali rappresenta una visualizzazione dei dati nel buffer, ad esempio codice o un form. Di conseguenza, ogni oggetto visualizzazione documento ha una visualizzazione fisica (identificata da un elemento noto come una stringa di visualizzazione fisica) e in genere una singola visualizzazione logica.

 In alcuni casi, tuttavia, una visualizzazione fisica può avere due o più visualizzazioni logiche. Alcuni esempi sono un editor con una finestra divisa con visualizzazioni affiancate o una finestra di progettazione di moduli con una visualizzazione GUI/progettazione e una visualizzazione code-behind-the-form.

 Per consentire all'editor di accedere a tutte le visualizzazioni fisiche disponibili, è necessario creare una stringa di visualizzazione fisica univoca per ogni tipo di oggetto visualizzazione documento che è possibile creare nella factory dell'editor. Ad esempio, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] la factory dell'editor può creare oggetti visualizzazione documento per una finestra del codice e una finestra di progettazione form.

## <a name="creating-multi-tabbed-views"></a>Creazione di viste a più schede
 Anche se un oggetto visualizzazione documento deve essere associato a una vista fisica tramite una stringa di visualizzazione fisica univoca, è possibile inserire più schede all'interno della visualizzazione fisica per consentire la visualizzazione dei dati in modi diversi. In questa configurazione a più schede, tutte le schede sono associate alla stessa stringa di visualizzazione fisica, ma a ogni scheda viene assegnato un GUID di visualizzazione logica diverso.

 Per creare una visualizzazione a più schede <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> per un editor, implementare<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>l'interfaccia e quindi associare un GUID di visualizzazione logica diverso ( ) a ogni scheda creata.

 L'editor HTML di Visual Studio è un esempio di editor con una visualizzazione a più schede. Dispone di schede **Progettazione** e **Origine.** A tale scopo, a ogni scheda è `LOGICALVIEWID_TextView` associata una `LOGICALVIEWID_Code` visualizzazione logica diversa, per la scheda **Progettazione** e per la scheda **Origine.**

 Specificando la visualizzazione logica appropriata, un VSPackage può accedere alla visualizzazione che corrisponde a uno scopo particolare, ad esempio la progettazione di un form, la modifica del codice o il debug del codice. Tuttavia, una delle finestre deve essere identificata dalla stringa NULL`LOGVIEWID_Primary`e deve corrispondere alla visualizzazione logica primaria ( ).

 Nella tabella seguente sono elencati i valori di visualizzazione logica disponibili e il relativo utilizzo.

|LOGVIEWID GUID|Uso consigliato|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Visualizzazione predefinita/primaria della factory dell'editor.<br /><br /> Tutte le factory dell'editor devono supportare questo valore. Questa visualizzazione deve utilizzare la stringa NULL come stringa di visualizzazione fisica. È necessario impostare almeno una visualizzazione logica su questo valore.|
|`LOGVIEWID_Debugging`|Visualizzazione di debug. In `LOGVIEWID_Debugging` genere, esegue il `LOGVIEWID_Code`mapping alla stessa visualizzazione di .|
|`LOGVIEWID_Code`|Vista avviata dal comando **Visualizza codice.**|
|`LOGVIEWID_Designer`|Visualizzazione avviata dal comando **Visualizza modulo.**|
|`LOGVIEWID_TextView`|Visualizzazione dell'editor di testo. Questa è la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>visualizzazione che restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, da cui è possibile accedere a .|
|`LOGVIEWID_UserChooseView`|Richiede all'utente di scegliere la visualizzazione da utilizzare.|
|`LOGVIEWID_ProjectSpecificEditor`|Passato dalla finestra di dialogo **Apri con** a<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> quando l'utente sceglie la voce "(Editor predefinito del progetto)".|

 Anche se i GUID di visualizzazione logica sono estensibili, è possibile utilizzare solo i GUID di visualizzazione logica definiti nel pacchetto VSPackage.

 All'arresto, Visual Studio mantiene il GUID della factory dell'editor e le stringhe di visualizzazione fisica associate alla finestra del documento in modo che possa essere utilizzato per riaprire le finestre di documento quando la soluzione viene riaperta. Solo le finestre aperte quando una soluzione viene chiusa vengono mantenute nel file di soluzione (con estensione suo). Questi valori corrispondono `VSFPROPID_pszPhysicalView` ai `propid` valori `VSFPROPID_guidEditorType` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> passati nel parametro nel metodo .

## <a name="example"></a>Esempio
 Questo frammento di <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> codice illustra come viene `IVsCodeWindow`utilizzato l'oggetto per accedere a una visualizzazione che implementa . In questo caso, il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> servizio <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> viene `LOGVIEWID_TextView`utilizzato per chiamare e richiedere , che ottiene un puntatore a una cornice della finestra. Un puntatore all'oggetto visualizzazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> documento viene ottenuto `VSFPROPID_DocView`chiamando e specificando un valore di . Dall'oggetto visualizzazione `QueryInterface` documento, `IVsCodeWindow`viene chiamato per . In questo caso si prevede che venga restituito un editor di testo <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> e pertanto l'oggetto visualizzazione documento restituito nel metodo è una finestra del codice.

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
