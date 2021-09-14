---
title: Visualizzazioni singole e a più schede | Microsoft Docs
description: Informazioni su come implementare visualizzazioni con più schede negli editor, ad esempio una finestra dell'editor di codice e una finestra di progettazione form.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d03563fe84d8985ab1fd1b746a05cd0c8d43e485
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627252"
---
# <a name="single-and-multi-tab-views"></a>Visualizzazioni a schede singole e multiple
Un editor può creare tipi diversi di visualizzazioni. Un esempio è una finestra dell'editor di codice, un'altra è una finestra di progettazione di form.

 Una visualizzazione a più schede è una visualizzazione con più schede. Ad esempio, l'editor HTML ha due schede nella parte inferiore: **Progettazione** **e Origine**, ognuna delle quali è una visualizzazione logica. Nella visualizzazione Progettazione viene visualizzata una pagina Web sottoposta a rendering, mentre l'altra visualizza il codice HTML che include la pagina Web.

## <a name="accessing-physical-views"></a>Accesso alle visualizzazioni fisiche
 Le visualizzazioni fisiche ospitano oggetti visualizzazione documento, ognuno dei quali rappresenta una visualizzazione dei dati nel buffer, ad esempio codice o modulo. Di conseguenza, ogni oggetto visualizzazione documento ha una visualizzazione fisica (identificata da una stringa di visualizzazione fisica) e in genere una singola visualizzazione logica.

 In alcuni casi, tuttavia, una vista fisica può avere due o più visualizzazioni logiche. Alcuni esempi sono un editor con una finestra divisa con visualizzazioni affiancate o una finestra di progettazione di moduli con una visualizzazione GUI/progettazione e una visualizzazione code-behind-modulo.

 Per consentire all'editor di accedere a tutte le visualizzazioni fisiche disponibili, è necessario creare una stringa di visualizzazione fisica univoca per ogni tipo di oggetto visualizzazione documento che la factory dell'editor può creare. Ad esempio, la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] factory dell'editor può creare oggetti visualizzazione documento per una finestra del codice e una finestra di progettazione form.

## <a name="creating-multi-tabbed-views"></a>Creazione di visualizzazioni a più schede
 Anche se un oggetto visualizzazione documento deve essere associato a una visualizzazione fisica tramite una stringa di visualizzazione fisica univoca, è possibile inserire più schede all'interno della visualizzazione fisica per abilitare la visualizzazione dei dati in modi diversi. In questa configurazione a più schede tutte le schede sono associate alla stessa stringa di visualizzazione fisica, ma a ogni scheda viene assegnato un GUID di visualizzazione logica diverso.

 Per creare una visualizzazione a più schede per un editor, implementare l'interfaccia e quindi associare un GUID di visualizzazione logica <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> diverso ( ) a ogni scheda <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> creata.

 L Visual Studio editor HTML è un esempio di editor con una visualizzazione a più schede. Sono disponibili **le schede Progettazione** e **Origine.** A tale scopo, a ogni scheda è associata una visualizzazione logica diversa, `LOGICALVIEWID_TextView` per la scheda **Progettazione** e per `LOGICALVIEWID_Code` la **scheda** Origine.

 Specificando la visualizzazione logica appropriata, un VSPackage può accedere alla visualizzazione corrispondente a uno scopo specifico, ad esempio la progettazione di un modulo, la modifica del codice o il debug del codice. Tuttavia, una delle finestre deve essere identificata dalla stringa NULL e deve corrispondere alla vista logica primaria ( `LOGVIEWID_Primary` ).

 Nella tabella seguente sono elencati i valori di visualizzazione logica disponibili e il relativo utilizzo.

|LOGVIEWID GUID|Uso consigliato|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Visualizzazione predefinita/primaria della factory dell'editor.<br /><br /> Tutte le factory dell'editor devono supportare questo valore. Questa vista deve usare la stringa NULL come stringa di visualizzazione fisica. Almeno una vista logica deve essere impostata su questo valore.|
|`LOGVIEWID_Debugging`|Visualizzazione di debug. In genere, `LOGVIEWID_Debugging` esegue il mapping alla stessa visualizzazione di `LOGVIEWID_Code` .|
|`LOGVIEWID_Code`|Visualizzazione avviata dal **comando Visualizza** codice.|
|`LOGVIEWID_Designer`|Visualizzazione avviata dal **comando Visualizza** modulo.|
|`LOGVIEWID_TextView`|Visualizzazione dell'editor di testo. Si tratta della visualizzazione che restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> , da cui è possibile accedere a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|`LOGVIEWID_UserChooseView`|Richiede all'utente di scegliere la visualizzazione da usare.|
|`LOGVIEWID_ProjectSpecificEditor`|Passata dalla **finestra di dialogo** Apri con a<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> quando l'utente sceglie la voce "(Project editor predefinito)".|

 Anche se i GUID di visualizzazione logica sono estendibili, è possibile usare solo i GUID di visualizzazione logica definiti nel pacchetto VSPackage.

 All'arresto, Visual Studio mantiene il GUID della factory dell'editor e le stringhe di visualizzazione fisica associate alla finestra del documento in modo che possa essere usato per riaperre le finestre del documento quando la soluzione viene riaperta. Solo le finestre aperte quando una soluzione viene chiusa vengono mantenute nel file della soluzione (con estensione suo). Questi valori corrispondono ai `VSFPROPID_guidEditorType` valori e passati nel parametro nel metodo `VSFPROPID_pszPhysicalView` `propid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .

## <a name="example"></a>Esempio
 Questo frammento di codice illustra come <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> viene usato l'oggetto per accedere a una vista che implementa `IVsCodeWindow` . In questo caso, il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> servizio viene usato per chiamare e richiedere , che ottiene un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> `LOGVIEWID_TextView` puntatore a una cornice di finestra. Un puntatore all'oggetto visualizzazione documento viene ottenuto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> e specificando il valore `VSFPROPID_DocView` . Dall'oggetto di visualizzazione del documento `QueryInterface` viene chiamato per `IVsCodeWindow` . L'aspettativa in questo caso è che viene restituito un editor di testo e quindi l'oggetto visualizzazione documento restituito nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo è una finestra del codice.

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
