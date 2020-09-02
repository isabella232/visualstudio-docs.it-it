---
title: Campi e interfacce della finestra Proprietà | Microsoft Docs
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
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700816"
---
# <a name="properties-window-fields-and-interfaces"></a>Campi e interfacce della finestra Proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il modello per la selezione per determinare quali informazioni vengono visualizzate nella finestra **Proprietà** è basato sulla finestra con lo stato attivo nell'IDE. Ogni finestra e oggetto all'interno della finestra selezionata può avere un oggetto contesto di selezione inserito nel contesto di selezione globale. L'ambiente aggiorna il contesto di selezione globale con i valori da una cornice della finestra quando tale finestra ha lo stato attivo. Quando lo stato attivo cambia, il contesto di selezione.  
  
## <a name="tracking-selection-in-the-ide"></a>Rilevamento della selezione nell'IDE  
 Al frame o al sito della finestra, di proprietà dell'IDE, è associato un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Nei passaggi seguenti viene illustrato come una modifica in una selezione, causata dall'utente che imposta lo stato attivo su un'altra finestra aperta o selezionando un elemento di progetto diverso in **Esplora soluzioni**, viene implementata per modificare il contenuto visualizzato nella finestra **Proprietà** .  
  
1. L'oggetto creato dal pacchetto VSPackage che è presente nella finestra selezionata chiama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> per avere <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Il contenitore di selezione, fornito dalla finestra selezionata, crea il proprio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto. Quando la selezione viene modificata, il pacchetto VSPackage chiama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> per notificare a tutti i listener nell'ambiente, inclusa la finestra **Proprietà** , della modifica. Fornisce inoltre l'accesso alle informazioni sulla gerarchia e sugli elementi correlati alla nuova selezione.  
  
3. La chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> e il passaggio degli elementi della gerarchia selezionati nel `VSHPROPID_BrowseObject` parametro compilerà l' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto.  
  
4. Viene restituito un oggetto derivato dall' [interfaccia IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> l'elemento richiesto e l'ambiente ne esegue il wrapping in un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (vedere il passaggio successivo). Se la chiamata ha esito negativo, l'ambiente esegue una seconda chiamata a `IVsHierarchy::GetProperty` , passando al contenitore di selezione <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> fornito dall'elemento o dagli elementi della gerarchia.  
  
    Il pacchetto VSPackage del progetto non viene creato <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché il pacchetto VSPackage della finestra fornito dall'ambiente che lo implementa (ad esempio, **Esplora soluzioni**) costrutti per <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> suo conto.  
  
5. L'ambiente richiama i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per ottenere gli oggetti in base all' `IDispatch` interfaccia da compilare nella finestra **proprietà** .  
  
   Quando viene modificato un valore nella finestra **Proprietà** , i pacchetti VSPackage implementano `IVsTrackSelectionEx::OnElementValueChangeEx` e `IVsTrackSelectionEx::OnSelectionChangeEx` per segnalare la modifica al valore dell'elemento. L'ambiente richiama quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> per salvare le informazioni visualizzate nella finestra **proprietà** sincronizzate con i valori delle proprietà. Per ulteriori informazioni, vedere [aggiornamento dei valori delle proprietà nella finestra Proprietà](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Oltre a selezionare un elemento di progetto diverso in **Esplora soluzioni** per visualizzare le proprietà correlate a tale elemento, è anche possibile scegliere un oggetto diverso in un form o in una finestra del documento utilizzando l'elenco a discesa disponibile nella finestra **Proprietà** . Per ulteriori informazioni, vedere [elenco di oggetti finestra Proprietà](../../extensibility/internals/properties-window-object-list.md).  
  
   È possibile modificare il modo in cui le informazioni vengono visualizzate nella griglia della finestra **Proprietà** da alfabetico a categorico e, se disponibile, è anche possibile aprire una pagina delle proprietà per un oggetto selezionato facendo clic sui pulsanti appropriati nella finestra **Proprietà** . Per ulteriori informazioni, vedere [pulsanti della finestra Proprietà](../../extensibility/internals/properties-window-buttons.md) e [pagine delle proprietà](../../extensibility/internals/property-pages.md).  
  
   Infine, nella parte inferiore della finestra **Proprietà** è inclusa anche una descrizione del campo selezionato nella griglia della finestra **Proprietà** . Per ulteriori informazioni, vedere [recupero delle descrizioni dei campi nella finestra Proprietà](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
