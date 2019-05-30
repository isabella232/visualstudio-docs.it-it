---
title: Adattamento del codice Legacy nell'editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdc507e3897398e47ed8038fa28165eb4add166c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313571"
---
# <a name="adapt-legacy-code-to-the-editor"></a>Adatta il codice legacy per l'editor
Editor di Visual Studio offre numerose funzionalità che è possibile accedere da componenti di codice esistenti. Le istruzioni seguenti illustrano come adattare il componente non MEF, ad esempio, un pacchetto VSPackage, usare la funzionalità dell'editor. Le istruzioni illustrano anche come utilizzare gli adapter per ottenere i servizi dell'editor di codice gestito e non gestito.

## <a name="editor-adapters"></a>Schede editor
Schede editor o gli shim, sono wrapper per gli oggetti di editor che espongono anche le classi e le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop> API. È possibile usare le schede per spostarsi tra i servizi non di editor, ad esempio, i comandi di Visual Studio shell e servizi di editor. (Si tratta come l'editor è attualmente ospitato in Visual Studio). Gli adapter anche abilitare estensioni legacy di servizio di editor e linguaggio funzionava correttamente in Visual Studio.

## <a name="use-editor-adapters"></a>Utilizzare schede editor
Il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> fornisce metodi che passare tra le nuove interfacce di editor e le interfacce legacy e anche i metodi che creano schede.

Se si usa questo servizio in una parte del componente MEF, è possibile importare il servizio come indicato di seguito.

```
[Import(typeof(IVsEditorAdaptersFactoryService))]
internal IVsEditorAdaptersFactoryService editorFactory;
```

Se si desidera usare questo servizio in un componente non MEF, seguire le istruzioni nella sezione "Utilizzando Visual Studio Editor servizi in un Non-componente MEF" più avanti in questo argomento.

## <a name="switch-between-the-new-editor-api-and-the-legacy-api"></a>Passare tra la nuova API di editor e l'API legacy
Usare i metodi seguenti per passare da un oggetto editor e un'interfaccia legacy.

|Metodo|Conversione|
|------------|----------------|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Converte un' <xref:Microsoft.VisualStudio.Text.ITextBuffer> a un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Converte un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> a un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Converte un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> a un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Converte un' <xref:Microsoft.VisualStudio.Text.Editor.ITextView> a un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Converte un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|

## <a name="create-adapters"></a>Creazione di adapter
Usare i metodi seguenti per creare adattatori per le interfacce legacy.

|Metodo|Conversione|
|------------|----------------|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per un determinato <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|

## <a name="creating-adapters-in-unmanaged-code"></a>Creazione di schede in codice non gestito
Tutte le classi di adapter registrate per essere locale condiviso generabile e può essere creata un'istanza usando la `VsLocalCreateInstance()` (funzione).

Tutte le schede vengono create utilizzando il GUID definiti nel *vsshlids.h* del file nei *\..\VisualStudioIntegration\Common\Inc\\* cartella di Visual Studio SDK installazione. Per creare un'istanza di VsTextBufferAdapter, usare il codice seguente.

```
IVsTextBuffer *pBuf = NULL;
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);
```

## <a name="create-adapters-in-managed-code"></a>Creare schede nel codice gestito
Nel codice gestito, è possibile CO-creare le schede di esattamente a quello descritto per codice non gestito. È anche possibile usare un servizio MEF che ti permette di creare e interagire con gli adapter. In questo modo di ottenere un adattatore consente un controllo più accurato rispetto a quanto disponibile durante la co-creazione.

### <a name="to-create-an-adapter-for-ivstextview"></a>Creare un adattatore per IVsTextView

1. Aggiungere un riferimento a *Microsoft.VisualStudio.Editor.dll*. Verificare che l'opzione `CopyLocal` è impostata su `false`.

2. Creare un'istanza di <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, come indicato di seguito.

    ```
    using Microsoft.VisualStudio.Editor;
    ...
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();
    ```

3. Chiamare il metodo `CreateX()`.

    ```
    adapterFactoryService.CreateTextViewAdapter(textView);
    ```

## <a name="use-the-visual-studio-editor-directly-from-unmanaged-code"></a>Usare l'editor di Visual Studio direttamente dal codice non gestito
Lo spazio dei nomi Microsoft.VisualStudio.Platform.VSEditor e lo spazio dei nomi Microsoft.VisualStudio.Platform.VSEditor.Interop espongono interfacce COM callable come IVx * interfacce. Ad esempio, l'interfaccia Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer è la versione COM del <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia. Dal `IVxTextBuffer`, è possibile ottenere l'accesso agli snapshot del buffer, del buffer, l'ascolto degli eventi di modifica testo nel buffer e creare punti di rilevamento e intervalli. La procedura seguente illustra come accedere a un `IVxTextBuffer` da un `IVsTextBuffer`.

### <a name="to-get-an-ivxtextbuffer"></a>Per ottenere un oggetto IVxTextBuffer

1. Le definizioni per il IVx\* interfacce sono nel *VSEditor.h* del file nei *\..\VisualStudioIntegration\Common\Inc\\* cartella di Visual Studio Installazione del SDK.

2. Il codice seguente crea un'istanza di un buffer di testo usando il `IVsUserData->GetData()` (metodo). Nel codice seguente, `pData` è un puntatore a un `IVsUserData` oggetto.

    ```cpp
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

## <a name="use-visual-studio-editor-services-in-a-non-mef-component"></a>Usare i servizi di editor di Visual Studio in un componente non MEF
Se si dispone di un componente di codice gestito esistente che non usa il framework MEF e si desidera utilizzare i servizi dell'editor di Visual Studio, è necessario aggiungere un riferimento all'assembly che contiene il ComponentModelHost VSPackage e ottenere il relativo servizio SComponentModel acquisisca i.

### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Per utilizzare i componenti dell'editor di Visual Studio da un componente non MEF

1. Aggiungere un riferimento al *Microsoft.VisualStudio.ComponentModelHost.dll* assembly nel *\..\Common7\IDE\\* cartella di installazione di Visual Studio. Verificare che l'opzione `CopyLocal` è impostata su `false`.

2. Aggiungere una privata `IComponentModel` membro alla classe in cui si desidera utilizzare i servizi di editor di Visual Studio, come indicato di seguito.

    ```
    using Microsoft.VisualStudio.ComponentModelHost;
    ....
    private IComponentModel componentModel;
    ```

3. Creare un'istanza di modello del componente nel metodo di inizializzazione per il componente.

    ```
    componentModel =
        (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));
    ```

4. Successivamente, è possibile ottenere uno qualsiasi dei servizi di editor di Visual Studio tramite la chiamata di `IComponentModel.GetService<T>()` metodo per il servizio desiderato.

    ```
    textBufferFactoryService =
        componentModel.GetService<ITextBufferFactoryService>();
    ```
