---
title: Uso di marcatori di testo con l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695472"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Uso di marcatori di testo con l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un marcatore di testo è un intervallo mobile di testo in un buffer che può influire sulla visualizzazione e sul comportamento di un'area di testo. I marcatori includono punti di interruzione, segnalibri, sottolineature ondulate e aree di sola lettura. I marcatori di testo sono fondamentalmente diversi dalla colorazione della sintassi. La colorazione della sintassi è un modo rapido per comunicare la sintassi del linguaggio associata a un'area di testo. La colorazione della sintassi è generalmente richiesta quando Windows disegna la schermata, quando la velocità è importante. La colorazione della sintassi modifica solo il colore del testo. I marcatori di testo possono modificare molte altre proprietà di testo. I marcatori di testo possono "float" e applicano un comportamento speciale e una colorazione.  
  
 A causa dell'overhead delle prestazioni associato ai marcatori di testo, non creare molti marcatori per i buffer di testo. Ogni marcatore viene aggiornato ogni volta che un utente modifica il contenuto del buffer.  
  
> [!NOTE]
> Gli utenti possono modificare il colore di un tipo di marcatore visibile, ma non la forma e lo stile. Per ulteriori informazioni, vedere [tipi di carattere e colori, ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Aggiungere marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md)|Viene descritto come aggiungere un tipo di marcatore di testo standard fornito dall' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale a una visualizzazione di testo.|  
|[Procedura: Implementare marcatori di errore](../extensibility/how-to-implement-error-markers.md)|Viene descritto come implementare un'istanza del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] marcatore utilizzato per indicare gli errori utilizzando sottolineature ondulate rosse.|  
|[Procedura: Creare marcatori di testo personalizzati](../extensibility/how-to-create-custom-text-markers.md)|Viene descritto come creare e aggiungere un tipo di marcatore di testo personalizzato a una visualizzazione di testo.|  
|[Procedura: Usare i marcatori di testo](../extensibility/how-to-use-text-markers.md)|Viene illustrato come aggiungere indicatori di testo.|  
|[Analisi dell'editor principale](../extensibility/inside-the-core-editor.md)|Vengono descritte le funzionalità dell'editor principale e vengono fornite informazioni dettagliate sulla personalizzazione dell'editor principale.|  
|[Funzionalità dell'editor](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Descrive le funzionalità disponibili nell' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale.|  
  
## <a name="reference"></a>Informazioni di riferimento  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fornisce un meccanismo uniforme per ottenere informazioni su un tipo di marcatore di testo specifico, se predefinito dall'editor o registrato da un pacchetto VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Consente di accedere e modificare la posizione di un marcatore di testo in un buffer di testo utilizzando coordinate bidimensionali.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Fornisce metodi per la gestione di marcatori di testo.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fornisce callback all' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE e ad altri processi usati per modificare un marcatore di testo.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Estende la funzionalità disponibile tramite l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia fornendo callback aggiuntivi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Estende la funzionalità disponibile tramite l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia fornendo callback aggiuntivi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Consente a un tipo di marcatore di determinare se altri tipi di marcatore condividono lo stesso set di colori.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fornisce contesto per marcatori di testo nell'editor principale. Per ogni tipo di marcatore di testo nell'editor principale, l'IDE crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> oggetto separato.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Gestore fornito per i marcatori i cui glifi supportano la modifica tramite trascinamento della selezione. Un glifo è un'icona che indica la posizione di un marcatore.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Restituisce un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfaccia da un servizio che fornisce un marcatore di testo ad altri VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Consente di accedere a e di regolare la posizione di un marcatore di testo in un buffer di testo usando coordinate unidimensionali. Se possibile, non utilizzare questa interfaccia.
