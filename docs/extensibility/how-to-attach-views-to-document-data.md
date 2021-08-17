---
title: 'Procedura: Associare visualizzazioni a document data | Microsoft Docs'
description: Potrebbe essere possibile allegare una nuova visualizzazione documento a un oggetto dati del documento esistente. Utilizzare questa procedura per determinare se è possibile collegare la vista.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 16b014141d2f4f396d35b2e163b7c191ab0115325988d7484a544066a077ce98
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376599"
---
# <a name="how-to-attach-views-to-document-data"></a>Procedura: Associare visualizzazioni ai dati del documento
Se si dispone di una nuova visualizzazione documento, è possibile collegarla a un oggetto dati del documento esistente.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Per determinare se è possibile collegare una vista a un oggetto dati del documento esistente

1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Nell'implementazione di `IVsEditorFactory::CreateEditorInstance` chiamare `QueryInterface` sull'oggetto dati del documento esistente quando l'IDE chiama l'implementazione `CreateEditorInstance` di .

    La `QueryInterface` chiamata di consente di esaminare l'oggetto dati del documento esistente, specificato nel `punkDocDataExisting` parametro .

    Le interfacce esatte su cui è necessario eseguire una query, tuttavia, dipendono dall'editor che apre il documento, come descritto nel passaggio 4.

3. Se non si trovano le interfacce appropriate nell'oggetto dati del documento esistente, restituire all'editor un codice di errore che indica che l'oggetto dati del documento non è compatibile con l'editor.

    Nell'implementazione dell'IDE di , una finestra di messaggio notifica che il documento è aperto in un altro editor e chiede se <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> si vuole chiuderlo.

4. Se si chiude questo documento, Visual Studio chiama la factory dell'editor per la seconda volta. In questa chiamata, il `DocDataExisting` parametro è uguale a NULL. L'implementazione della factory dell'editor può quindi aprire l'oggetto dati del documento nel proprio editor.

   > [!NOTE]
   > Per determinare se è possibile usare un oggetto dati del documento esistente, è anche possibile usare una conoscenza privata dell'implementazione dell'interfaccia eseguendo il cast di un puntatore alla classe effettiva [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] dell'implementazione privata. Ad esempio, tutti gli editor standard implementano `IVsPersistFileFormat` , che eredita da <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Di conseguenza, è possibile chiamare per e, se l'ID classe nell'oggetto dati del documento esistente corrisponde all'ID classe dell'implementazione, è possibile usare `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> l'oggetto dati del documento.

## <a name="robust-programming"></a>Programmazione efficiente
 Quando Visual Studio chiama l'implementazione del metodo , passa un puntatore all'oggetto dati del documento esistente nel parametro <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> `punkDocDataExisting` , se presente. Esaminare l'oggetto dati del documento restituito in per determinare se l'oggetto dati del documento è appropriato per l'editor, come descritto nella nota del passaggio 4 della `punkDocDataExisting` procedura di questo argomento. Se è appropriato, la factory dell'editor deve fornire una seconda visualizzazione per i dati, come descritto in [Supportare più visualizzazioni documento.](../extensibility/supporting-multiple-document-views.md) In caso contrario, verrà visualizzato un messaggio di errore appropriato.

## <a name="see-also"></a>Vedi anche
- [Supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md)
- [Dati del documento e visualizzazione dei documenti negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)
