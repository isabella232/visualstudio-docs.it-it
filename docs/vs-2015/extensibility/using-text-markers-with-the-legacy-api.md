---
title: Utilizzo di marcatori di testo con l'API Legacy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b276a678d4b5e97e3ef949bdf1fd74b37070f9d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518246"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Utilizzo di marcatori di testo con l'API Legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [usando i marcatori di testo con l'API Legacy](https://docs.microsoft.com/visualstudio/extensibility/using-text-markers-with-the-legacy-api).  
  
Un marcatore di testo è un intervallo di testo in un buffer che può influenzare la visualizzazione a virgola mobile e il comportamento di un'area di testo. Marcatori di includono i punti di interruzione, i segnalibri, sottolineature ondulate di colore e le aree di sola lettura. Marcatori di testo sono fondamentalmente diversi da colorazione della sintassi. Colorazione della sintassi è un modo rapido per comunicare la sintassi del linguaggio che è associata a un'area di testo. Colorazione della sintassi viene in genere richiesta quando Windows viene ridisegnato schermo, la velocità è importante. Colorazione della sintassi viene modificato solo il colore del testo. Marcatori di testo è possono modificare molte altre proprietà di testo. Marcatori di testo è possono "spostarsi" e applicare un comportamento speciale e la colorazione.  
  
 A causa dell'overhead delle prestazioni associati marcatori di testo, non creare molti marcatori per i buffer di testo. Ogni indicatore viene aggiornato ogni volta che un utente modifica il contenuto del buffer.  
  
> [!NOTE]
>  Gli utenti possono modificare il colore di un tipo di marcatore visibili, ma non la forma e stile. Per altre informazioni, vedere [Fonts and Colors, Environment, Options Dialog Box](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Aggiungere marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md)|Viene descritto come aggiungere un tipo di marcatore di testo standard fornito dal [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale per una visualizzazione di testo.|  
|[Procedura: Implementare marcatori di errore](../extensibility/how-to-implement-error-markers.md)|Viene descritto come implementare un'istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] marcatore utilizzato per indicare gli errori tramite sottolineature ondulate di colore rosso.|  
|[Procedura: Creare marcatori di testo personalizzati](../extensibility/how-to-create-custom-text-markers.md)|Viene descritto come creare e aggiungere un tipo di marcatore di testo personalizzato a una visualizzazione di testo.|  
|[Procedura: Usare i marcatori di testo](../extensibility/how-to-use-text-markers.md)|Viene illustrato come aggiungere i marcatori di testo.|  
|[Componenti e funzionalità dell'editor principale](../extensibility/inside-the-core-editor.md)|Vengono descritte le funzionalità dell'editor principale e vengono fornite informazioni dettagliate su come personalizzare l'editor principale.|  
|[Funzionalità dell'editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Descrive le funzionalità disponibili nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale.|  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fornisce un meccanismo uniforme per ottenere informazioni su un tipo di marcatore di testo specifico, se predefinito dall'editor o registrato da un pacchetto VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Fornisce l'accesso e consente di regolare la posizione di un marcatore di testo in un buffer di testo utilizzando le coordinate bidimensionali.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Fornisce metodi per la gestione di marcatori di testo.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fornisce i callback per il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE e altri processi che consentono di modificare un marcatore di testo.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Estende le funzionalità disponibili tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia fornendo callback aggiuntivi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Estende le funzionalità disponibili tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia fornendo callback aggiuntivi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Consente a un tipo di marcatore determinare se altri tipi di marcatore condividono lo stesso set di colori.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fornisce contesto per marcatori di testo nell'editor principale. Per ogni tipo di marcatore di testo che si trova in editor principale, l'IDE crea un oggetto separato <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> oggetto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Gestore che viene fornito per i marcatori i cui glifi supportano la modifica di trascinamento e rilascio. Un glifo è presente un'icona che indica la posizione di un marcatore.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Restituisce un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfaccia dal servizio che fornisce un testo di marcatori da altri pacchetti VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Fornisce l'accesso e regola la posizione di un marcatore di testo in un buffer di testo utilizzando coordinate unidimensionali. Se è possibile, non usare questa interfaccia.
