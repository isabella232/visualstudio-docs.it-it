---
title: 'Procedura: aggiungere marcatori di testo standard | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839299"
---
# <a name="how-to-add-standard-text-markers"></a>Procedura: Aggiungere marcatori di testo standard
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilizzare la procedura seguente per creare uno dei tipi di marcatore di testo predefiniti forniti con l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale.  
  
### <a name="to-create-a-text-marker"></a>Per creare un marcatore di testo  
  
1. A seconda del fatto che si usi un sistema di coordinate uno o bidimensionale, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo o il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodo per creare un nuovo marcatore di testo.  
  
     In questa chiamata al metodo specificare un tipo di marcatore, un intervallo di testo su cui creare il marcatore e un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia. Questo metodo restituisce quindi un puntatore al marcatore di testo appena creato. I tipi di marcatore vengono ricavati dall' <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> enumerazione. Specificare un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia se si desidera essere informati degli eventi del marcatore.  
  
    > [!NOTE]
    > Creare marcatori di testo solo sul thread principale dell'interfaccia utente. L'editor principale si basa sul contenuto del buffer di testo per creare marcatori di testo e il buffer di testo non è thread-safe.  
  
## <a name="adding-a-custom-command"></a>Aggiunta di un comando personalizzato  
 L'implementazione dell' `IVsTextMarkerClient` interfaccia e la fornitura di un puntatore da un marcatore migliorano il comportamento del marcatore in diversi modi. In primo luogo, è possibile fornire suggerimenti per il marcatore e per eseguire i comandi. Questo consente anche di ricevere notifiche degli eventi per singoli marcatori e di creare un menu di scelta rapida personalizzato sul marcatore. Utilizzare la seguente procedura per aggiungere un comando personalizzato al menu di scelta rapida del marcatore.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Per aggiungere un comando personalizzato al menu di scelta rapida  
  
1. Prima che venga visualizzato il menu di scelta rapida, l'ambiente chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> metodo e passa un puntatore al marcatore di testo interessato e al numero dell'elemento del comando nel menu di scelta rapida.  
  
     Ad esempio, i comandi specifici del punto di interruzione nel menu di scelta rapida includono **Rimuovi** punto di interruzione tramite nuovo punto di **interruzione**, come visualizzato nello screenshot seguente.  
  
     ![Menu di scelta rapida Marcatore](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. Passare di nuovo il testo che identifica il nome del comando personalizzato. Ad esempio, **Remove breakpoint** potrebbe essere un comando personalizzato se non è già stato fornito dall'ambiente. Viene inoltre restituito se il comando è supportato, disponibile e abilitato e/o un interruttore on-off. L'ambiente utilizza queste informazioni per visualizzare il comando personalizzato nel menu di scelta rapida in modo corretto.  
  
3. Per eseguire il comando, l'ambiente chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metodo, passando un puntatore al marcatore di testo e il numero del comando selezionato dal menu di scelta rapida.  
  
     Usare queste informazioni da questa chiamata per eseguire qualsiasi azione del marcatore di testo che il comando personalizzato impone.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)   
 [Procedura: creare marcatori di testo personalizzati](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: Usare i marcatori di testo](../extensibility/how-to-use-text-markers.md)
