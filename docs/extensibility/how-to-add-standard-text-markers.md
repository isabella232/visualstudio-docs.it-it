---
title: 'Procedura: Aggiungere i marcatori di testo Standard | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e49b8f2b0cdccbf4c6acfab0c8b68b0f3ad1a5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340960"
---
# <a name="how-to-add-standard-text-markers"></a>Procedura: Aggiungere i marcatori di testo standard
Usare la procedura seguente per creare uno dei tipi di marcatore di testo predefinito forniti con il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale.

## <a name="to-create-a-text-marker"></a>Per creare un marcatore di testo

1. A seconda se si usa un unidimensionale o bidimensionale sistema di coordinate, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo o il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodo per creare un nuovo marcatore di testo.

     In questa chiamata al metodo, specificare un tipo di marcatore, un intervallo di testo per creare il marcatore di failover e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia. Quindi, questo metodo restituisce un puntatore al marcatore di testo appena creata. Tipi di marcatori vengono prelevati i <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> enumerazione. Specificare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia se si desidera essere informati di eventi del marcatore.

    > [!NOTE]
    > Creare i marcatori di testo sul thread principale della UI solo. L'editor principale è basato sul contenuto del buffer di testo per creare marcatori di testo e il buffer di testo non è thread-safe.

## <a name="add-a-custom-command"></a>Aggiungere un comando personalizzato
 Implementazione di `IVsTextMarkerClient` interfaccia e che fornisce un puntatore a esso da un marcatore migliora il comportamento di marcatore in diversi modi. In primo luogo, in questo modo è possibile fornire suggerimenti per il marcatore e di eseguire i comandi. Ciò consente anche di ricevere le notifiche degli eventi per i marcatori di singoli e per creare un menu contestuale personalizzato sul marcatore. Utilizzare la procedura seguente per aggiungere un comando personalizzato per il menu di scelta rapida marcatore.

### <a name="to-add-a-custom-command-to-the-context-menu"></a>Per aggiungere un comando personalizzato per il menu di scelta rapida

1. Prima che venga visualizzato il menu di scelta rapida, l'ambiente chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> metodo e passa un puntatore per il marcatore di testo è interessato e il numero dell'elemento comando nel menu di scelta rapida.

     Ad esempio, i comandi specifici punti di interruzione nel menu di scelta rapida includono **Rimuovi punto di interruzione** attraverso **nuovo punto di interruzione**, come visualizzato nello screenshot seguente.

     ![Marker Context Menu](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")

2. Passare di nuovo un testo che identifica il nome del comando personalizzato. Ad esempio, **Rimuovi punto di interruzione** potrebbe essere un comando personalizzato se l'ambiente non ha già fornito. Anche passare di nuovo se il comando è supportato, disponibile e abilitato, e/o un interruttore on / off. L'ambiente Usa queste informazioni per visualizzare il comando personalizzato nel menu di scelta rapida in modo corretto.

3. Per eseguire il comando, l'ambiente chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> , passando è un puntatore per il marcatore di testo e il numero del comando scelto dal menu di scelta rapida.

     Usare queste informazioni da questa chiamata per eseguire qualsiasi azione del marcatore di testo del comando personalizzato determina.

## <a name="see-also"></a>Vedere anche
- [Usare marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)
- [Procedura: Implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)
- [Procedura: Creare i marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)
- [Procedura: Usare marcatori di testo](../extensibility/how-to-use-text-markers.md)