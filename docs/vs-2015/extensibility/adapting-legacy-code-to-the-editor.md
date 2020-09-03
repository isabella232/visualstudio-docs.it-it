---
title: Adattamento del codice legacy all'editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184913"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Adattamento del codice legacy all'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor di Visual Studio dispone di molte funzionalità a cui è possibile accedere dai componenti di codice esistenti. Nelle istruzioni seguenti viene illustrato come adattare un componente non MEF, ad esempio un pacchetto VSPackage, per utilizzare la funzionalità dell'editor. Nelle istruzioni viene inoltre illustrato come utilizzare gli adapter per ottenere i servizi dell'editor sia nel codice gestito che nel codice non gestito.  
  
## <a name="editor-adapters"></a>Adattatori editor  
 Gli adapter o gli shim di editor sono wrapper per gli oggetti editor che espongono anche le classi e le interfacce nell' <xref:Microsoft.VisualStudio.TextManager.Interop> API. È possibile utilizzare gli adapter per spostarsi tra i servizi non editor, ad esempio i comandi della shell di Visual Studio e i servizi dell'editor. (Questo è il modo in cui l'editor è attualmente ospitato in Visual Studio). Gli adapter consentono inoltre il funzionamento corretto dell'editor legacy e delle estensioni del servizio di linguaggio in Visual Studio.  
  
## <a name="using-editor-adapters"></a>Uso degli adattatori editor  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Fornisce metodi che passano tra le nuove interfacce di editor e le interfacce legacy, nonché i metodi per la creazione di adapter.  
  
 Se si usa questo servizio in una parte del componente MEF, è possibile importare il servizio come indicato di seguito.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Se si vuole usare questo servizio in un componente non MEF, seguire le istruzioni riportate nella sezione "uso dei servizi dell'editor di Visual Studio in un componente non MEF" più avanti in questo argomento.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Cambio tra la nuova API editor e l'API legacy  
 Usare i metodi seguenti per passare da un oggetto editor a un'interfaccia legacy e viceversa.  
  
|Metodo|Conversione|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Converte un oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer> in un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Converte un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> in un oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Converte un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> in un oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Converte un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> in un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Converte un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in un oggetto <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Creazione di adattatori  
 Usare i metodi seguenti per creare gli adapter per le interfacce legacy.  
  
|Metodo|Conversione|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per un oggetto specificato <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Creazione di adapter nel codice non gestito  
 Tutte le classi di adapter sono registrate come cocreabili locali e possono essere create tramite la `VsLocalCreateInstance()` funzione.  
  
 Tutti gli adapter vengono creati utilizzando i GUID definiti nel file vsshlids. h in. Cartella \VisualStudioIntegration\Common\Inc\ dell'installazione di Visual Studio SDK. Per creare un'istanza di VsTextBufferAdapter, usare il codice seguente.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Creazione di adapter nel codice gestito  
 Nel codice gestito è possibile creare la co-creazione degli adapter in modo analogo a quanto descritto per il codice non gestito. È inoltre possibile utilizzare un servizio MEF che consente di creare e interagire con gli adapter. Questo modo di ottenere un adapter consente un controllo più granulare rispetto a quello che si ha quando si crea la co-creazione.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Per creare un adapter per IVsTextView  
  
1. Aggiungere un riferimento a Microsoft.VisualStudio.Editor.dll. Assicurarsi che `CopyLocal` sia impostato su `false`.  
  
2. Creare un'istanza di <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , come indicato di seguito.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Chiamare il metodo `CreateX()` .  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Uso dell'editor di Visual Studio direttamente dal codice non gestito  
 Lo spazio dei nomi Microsoft. VisualStudio. Platform. VSEditor e lo spazio dei nomi Microsoft. VisualStudio. Platform. VSEditor. Interop espongono le interfacce COM richiamabili come interfacce IVx *. Ad esempio, l'interfaccia Microsoft. VisualStudio. Platform. VSEditor. Interop. IVxTextBuffer è la versione COM dell' <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia. Dalla `IVxTextBuffer` è possibile ottenere l'accesso agli snapshot del buffer, modificare il buffer, restare in ascolto degli eventi di modifica del testo nel buffer e creare punti di rilevamento e intervalli. Nei passaggi seguenti viene illustrato come accedere a `IVxTextBuffer` da un `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Per ottenere un IVxTextBuffer  
  
1. Le definizioni per le interfacce IVx * si trovano nel file VSEditor. h nel.. Cartella \VisualStudioIntegration\Common\Inc\ dell'installazione di Visual Studio SDK.  
  
2. Il codice seguente crea un'istanza di un buffer di testo usando il `IVsUserData->GetData()` metodo. Nel codice seguente, `pData` è un puntatore a un `IVsUserData` oggetto.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Uso dei servizi di editor di Visual Studio in un componente non MEF  
 Se si dispone di un componente di codice gestito esistente che non utilizza MEF e si desidera utilizzare i servizi dell'editor di Visual Studio, è necessario aggiungere un riferimento all'assembly che contiene il pacchetto VSPackage ComponentModelHost e ottenere il relativo servizio SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Per utilizzare i componenti dell'editor di Visual Studio da un componente non MEF  
  
1. Aggiungere un riferimento all'assembly Microsoft.VisualStudio.ComponentModelHost.dll nel.. Cartella \Common7\IDE\ dell'installazione di Visual Studio. Assicurarsi che `CopyLocal` sia impostato su `false`.  
  
2. Aggiungere un `IComponentModel` membro privato alla classe in cui si desidera utilizzare i servizi di editor di Visual Studio, come indicato di seguito.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Creare un'istanza del modello di componente nel metodo di inizializzazione per il componente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Successivamente, è possibile ottenere uno dei servizi di editor di Visual Studio chiamando il `IComponentModel.GetService<T>()` metodo per il servizio desiderato.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
