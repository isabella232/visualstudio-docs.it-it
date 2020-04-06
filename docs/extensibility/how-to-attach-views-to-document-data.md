---
title: 'Procedura: allegare viste ai dati del documento Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711082"
---
# <a name="how-to-attach-views-to-document-data"></a>Procedura: associare visualizzazioni ai dati del documentoHow to: Attach views to document data
Se si dispone di una nuova visualizzazione del documento, è possibile allegarla a un oggetto dati del documento esistente.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Per determinare se è possibile associare una vista a un oggetto dati del documento esistente

1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Nell'implementazione `IVsEditorFactory::CreateEditorInstance`di `QueryInterface` , chiamare l'oggetto dati del `CreateEditorInstance` documento esistente quando l'IDE chiama l'implementazione.

    La `QueryInterface` chiamata consente di esaminare l'oggetto dati `punkDocDataExisting` del documento esistente, specificato nel parametro .

    Le interfacce esatte su cui è necessario eseguire una query, tuttavia, dipendono dall'editor che sta aprendo il documento, come descritto nel passaggio 4.

3. Se non si trovano le interfacce appropriate nell'oggetto dati del documento esistente, restituire un codice di errore all'editor che indica che l'oggetto dati del documento non è compatibile con l'editor.

    Nell'implementazione dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, una finestra di messaggio notifica che il documento è aperto in un altro editor e chiede se si desidera chiuderlo.

4. Se si chiude questo documento, Visual Studio chiama la factory dell'editor per una seconda volta. In questa chiamata, il `DocDataExisting` parametro è uguale a NULL. L'implementazione factory dell'editor può quindi aprire l'oggetto dati del documento nel proprio editor.

   > [!NOTE]
   > Per determinare se è possibile utilizzare un oggetto dati documento esistente, è anche possibile utilizzare [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] la conoscenza privata dell'implementazione dell'interfaccia eseguendo il cast di un puntatore alla classe effettiva dell'implementazione privata. Ad esempio, tutti gli `IVsPersistFileFormat`editor standard <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>implementano , che eredita da . Pertanto, è `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>possibile chiamare per , e se l'ID di classe nell'oggetto dati del documento esistente corrisponde all'ID di classe dell'implementazione, è possibile utilizzare l'oggetto dati del documento.

## <a name="robust-programming"></a>Programmazione efficiente
 Quando Visual Studio chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> l'implementazione del metodo, passa nuovamente un `punkDocDataExisting` puntatore all'oggetto dati del documento esistente nel parametro, se presente. Esaminare l'oggetto dati `punkDocDataExisting` del documento restituito in per determinare se l'oggetto dati del documento è appropriato per l'editor, come descritto nella nota nel passaggio 4 della procedura descritta in questo argomento. Se appropriato, la factory dell'editor deve fornire una seconda visualizzazione per i dati, come descritto in [Supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md). In caso contrario, dovrebbe essere visualizzato un messaggio di errore appropriato.

## <a name="see-also"></a>Vedere anche
- [Supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md)
- [Dati del documento e visualizzazione del documento negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)
