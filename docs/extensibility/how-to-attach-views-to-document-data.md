---
title: 'Procedura: aggiungere visualizzazioni ai dati del documento | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5437e3a5d4fb0d6d33d570eb4d8923245cb287b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905890"
---
# <a name="how-to-attach-views-to-document-data"></a>Procedura: aggiungere visualizzazioni ai dati del documento
Se si dispone di una nuova visualizzazione del documento, potrebbe essere possibile collegarla a un oggetto dati del documento esistente.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Per determinare se è possibile aggiungere una vista a un oggetto dati del documento esistente

1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Nell'implementazione di `IVsEditorFactory::CreateEditorInstance` , chiamare `QueryInterface` sull'oggetto dati del documento esistente quando l'IDE chiama l' `CreateEditorInstance` implementazione.

    `QueryInterface`La chiamata a consente di esaminare l'oggetto dati del documento esistente, specificato nel `punkDocDataExisting` parametro.

    Le interfacce esatte su cui è necessario eseguire query, tuttavia, dipendono dall'editor che sta aprendo il documento, come descritto nel passaggio 4.

3. Se non si trovano le interfacce appropriate nell'oggetto dati del documento esistente, restituire un codice di errore all'editor che indica che l'oggetto dati del documento non è compatibile con l'editor.

    Nell'implementazione dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> una finestra di messaggio informa che il documento è aperto in un altro editor e chiede se si desidera chiuderlo.

4. Se si chiude il documento, Visual Studio chiama la factory dell'editor per la seconda volta. In questa chiamata il `DocDataExisting` parametro è uguale a null. L'implementazione della factory dell'editor può quindi aprire l'oggetto dati del documento nell'editor personalizzato.

   > [!NOTE]
   > Per determinare se è possibile utilizzare un oggetto dati documento esistente, è anche possibile utilizzare la conoscenza privata dell'implementazione dell'interfaccia eseguendo il cast di un puntatore alla [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] classe effettiva dell'implementazione privata. Ad esempio, tutti gli editor standard implementano `IVsPersistFileFormat` , che eredita da <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Pertanto, è possibile chiamare `QueryInterface` per <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> e se l'ID di classe nell'oggetto dati del documento esistente corrisponde all'ID di classe dell'implementazione, è possibile utilizzare l'oggetto dati del documento.

## <a name="robust-programming"></a>Programmazione efficiente
 Quando Visual Studio chiama l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo, restituisce un puntatore all'oggetto dati del documento esistente nel `punkDocDataExisting` parametro, se esistente. Esaminare l'oggetto dati del documento restituito in `punkDocDataExisting` per determinare se l'oggetto dati del documento è appropriato per l'editor, come descritto nella nota nel passaggio 4 della procedura descritta in questo argomento. Se è appropriato, la factory dell'editor deve fornire una seconda visualizzazione dei dati, come descritto in [supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md). In caso contrario, verrà visualizzato un messaggio di errore appropriato.

## <a name="see-also"></a>Vedere anche
- [Supportare più visualizzazioni di documenti](../extensibility/supporting-multiple-document-views.md)
- [Documenti e visualizzazione dei documenti negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)
