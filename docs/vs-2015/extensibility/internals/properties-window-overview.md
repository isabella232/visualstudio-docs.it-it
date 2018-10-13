---
title: Panoramica della finestra proprietà | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de60ed84abf4d4d2e01838140301919e13468239
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188708"
---
# <a name="properties-window-overview"></a>Panoramica della finestra Proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il **delle proprietà** finestra viene utilizzata per visualizzare le proprietà di oggetti selezionati nei due tipi principali di windows disponibile nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE). Questi due tipi di windows sono:  
  
-   Finestre degli strumenti, ad esempio browser Esplora soluzioni, Visualizzazione classi e oggetti  
  
-   Finestre dei documenti che contiene tali editor e finestre di progettazione di progettazione form, editor XML ed editor HTML  
  
## <a name="using-the-properties-window"></a>Usando la finestra proprietà  
 Il **proprietà** finestra vengono visualizzate le proprietà di uno o più elementi selezionati. Se sono selezionati più elementi, viene visualizzato l'intersezione di tutte le proprietà per tutti gli oggetti selezionati.  
  
 Eventi correlati a un oggetto selezionato all'interno di una finestra di progettazione di form o editor HTML utilizzando i metadati di COM+ vengono visualizzati nei **proprietà** finestra. Ad esempio, è possibile selezionare un pulsante e visualizzare gli eventi associati, ad esempio un `OnClick` evento, che può essere collegato al pulsante.  
  
 Gli eventi visualizzati nei **proprietà** finestra vengono utilizzate principalmente con gli oggetti associati al codice. Se si sta modificando un formato di file che non ha nulla a che fare con il codice, non si intende disporre di tutti gli eventi. Gli eventi vengono visualizzati solo nel **proprietà** finestra quando è presente un'associazione tra l'esecuzione di codice e alcuni eventi associati agli oggetti specifici. Un esempio di questo sarebbe code-behind di un oggetto selezionato viene eseguito quando viene attivato tale oggetto.  
  
 La tabella seguente elenca le interfacce principali utilizzate dai **proprietà** finestra.  
  
|Nome dell'interfaccia|Descrizione|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornisce un elenco di categorie per il **proprietà** finestra ed esegue il mapping di ogni proprietà a una categoria.|  
|[Interfaccia IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Espone metodi e proprietà per la programmazione di strumenti e altre applicazioni che supportano l'automazione di un oggetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Sono disponibili i pulsanti di puntini di sospensione (...) denominati *generatori* che aprire finestre di dialogo modale implementate dall'oggetto stesso. Utilizzato quando un valore non è tipizzato con facilità dall'utente in un campo di testo. Ad esempio, potrebbe essere utilizzato per aprire un selettore di colore che determina il valore RGB per l'utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornisce l'accesso agli oggetti utilizzati per aggiornare le informazioni visualizzate nel **proprietà** finestra. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene implementata dai pacchetti VSPackage per ogni finestra che contiene oggetti selezionabili con le proprietà correlate da visualizzare.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornisce informazioni sul tipo di oggetto, ad esempio i metodi di un'interfaccia e i campi di una struttura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Consente ai package VS di ricevere la notifica degli eventi di selezione e recuperare informazioni sulla gerarchia del progetto corrente, elemento, valore dell'elemento e contesto dell'interfaccia utente del comando.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornisce l'ambiente con accesso a più selezioni.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Utilizzato per fornire nomi localizzati in alcune proprietà visualizzate nel **proprietà** finestra.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica ai pacchetti VSPackage registrati le modifiche alla selezione corrente, valore dell'elemento o nel contesto dell'interfaccia utente del comando.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica all'ambiente una modifica nella selezione corrente e fornisce l'accesso alle informazioni di gerarchia ed elemento relative alla nuova selezione.|  
  
 Per altre informazioni su `IDispatch`, consultare la MSDN library.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)   
 [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)

