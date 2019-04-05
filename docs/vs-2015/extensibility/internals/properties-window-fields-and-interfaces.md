---
title: Proprietà Window Fields and Interfaces | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 515540eee455fcf22151e336897dd5f586867a82
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58963939"
---
# <a name="properties-window-fields-and-interfaces"></a>Campi e interfacce della finestra Proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il modello per la selezione determinare quali informazioni vengono visualizzate nel **proprietà** finestra è basata sulla finestra di stato attivo nell'IDE. Ogni finestra e oggetto all'interno della finestra selezionata, può avere relativo oggetto di contesto di selezione il push nel contesto di selezione globale. L'ambiente aggiorna il contesto di selezione globale con i valori di una cornice di finestra quando tale finestra ha lo stato attivo. Quando viene modificato lo stato attivo, pertanto, non il contesto di selezione.  
  
## <a name="tracking-selection-in-the-ide"></a>Traccia della selezione nell'IDE  
 Il frame della finestra o il sito, di proprietà dall'IDE, offre un servizio chiamato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. I passaggi seguenti mostrano come una modifica in una selezione, causata dall'utente modificando lo stato attivo a un'altra finestra aperta o selezionando un elemento di progetto diverso nel **Esplora soluzioni**, viene implementata per modificare il contenuto visualizzato nella finestra di  **Proprietà** finestra.  
  
1. L'oggetto creato dal pacchetto VSPackage che viene inserito nelle chiamate finestra selezionata <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> avere <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> richiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Il contenitore di selezione, fornito per la finestra selezionata, consente di creare un proprio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto. Quando la modifica di selezione, il pacchetto VSPackage chiama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> per notificare a qualsiasi listener nell'ambiente, inclusi i **proprietà** finestra, della modifica. Fornisce inoltre l'accesso alle informazioni di gerarchia ed elemento correlate alla nuova selezione.  
  
3. La chiamata <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> e passando gli elementi della gerarchia selezionata nel `VSHPROPID_BrowseObject` parametro consente di popolare il <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto.  
  
4. Oggetto derivato dal [IDispatch Interface](http://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) viene restituita per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> per l'elemento richiesto e l'ambiente esegue il wrapping in un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (vedere il passaggio seguente). Se la chiamata non riesce, l'ambiente esegue una seconda chiamata a `IVsHierarchy::GetProperty`, passandolo al contenitore di selezioni <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> che specifichino l'elemento della gerarchia o gli elementi.  
  
    Il progetto VSPackage non viene creato <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché la finestra fornita dall'ambiente di VSPackage che implementa (ad esempio, **Esplora soluzioni**) costruisce <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per suo conto.  
  
5. L'ambiente chiama i metodi della <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per ottenere gli oggetti in base il `IDispatch` interfaccia per riempire il **proprietà** finestra.  
  
   Quando un valore nel **delle proprietà** finestra viene modificata, i pacchetti VSPackage implementare `IVsTrackSelectionEx::OnElementValueChangeEx` e `IVsTrackSelectionEx::OnSelectionChangeEx` per segnalare la modifica per il valore dell'elemento. Richiama quindi l'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> oppure <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> per mantenere le informazioni visualizzate nel **proprietà** finestra sincronizzati con i valori delle proprietà. Per altre informazioni, vedere [aggiornare i valori delle proprietà nella finestra proprietà](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Oltre a selezionare un altro elemento del progetto **Esplora soluzioni** per visualizzare le proprietà correlate a tale elemento, è anche possibile scegliere un oggetto diverso all'interno di una finestra del form o un documento utilizzando l'elenco a discesa disponibile nel **Proprietà** finestra. Per altre informazioni, vedere [elenco di oggetti finestra proprietà](../../extensibility/internals/properties-window-object-list.md).  
  
   È possibile modificare il modo in cui vengono visualizzate informazioni il **proprietà** griglia della finestra dall'ordine alfabetico per categoria, e, se disponibile, è anche possibile aprire una pagina delle proprietà dell'oggetto selezionato facendo clic sui pulsanti appropriati nel  **Proprietà** finestra. Per altre informazioni, vedere [pulsanti della finestra proprietà](../../extensibility/internals/properties-window-buttons.md) e [pagine delle proprietà](../../extensibility/internals/property-pages.md).  
  
   Infine, la parte inferiore della **delle proprietà** finestra contiene inoltre una descrizione del campo selezionato nel **proprietà** griglia della finestra. Per altre informazioni, vedere [recupero delle descrizioni dei campi dalla finestra delle proprietà](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
