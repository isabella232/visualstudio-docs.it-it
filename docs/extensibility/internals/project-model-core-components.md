---
title: Componenti di base del modello di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d6940db78b1b3f358387651acff6f3a9f098b62
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957587"
---
# <a name="project-model-core-components"></a>Componenti di base del modello di progetto
Espandono le tabelle seguenti nel modello di progetto. Le tabelle presentano una breve descrizione di interfacce e servizi identificati nel modello e le interfacce e i servizi associati a oggetti specifici. Inoltre, le tabelle in dettaglio le altre interfacce facoltative la creazione del progetto e di manutenzione a seconda dei requisiti del tipo di progetto specifico.  
  
 Per altre informazioni, vedere [strumenti di esplorazione che supportano simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Oggetto del pacchetto  
  
|Interfaccia|Commenti|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inizializza un pacchetto VSPackage nell'ambiente IDE e rende disponibili i servizi all'IDE.|  
  
### <a name="project-factory-object"></a>Oggetto Factory di progetto  
  
|Interfaccia|Commenti|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gestisce la creazione di nuovi progetti e aprire progetti esistenti.|  
  
### <a name="project-objects"></a>Oggetti del progetto  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gestisce l'aggiunta e rimozione di elementi del progetto, consente di aprire gli editor e gestisce i mapping tra ogni moniker del documento e `VSITEMID`. Eredita da `IVsProject` e `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gestisce le proprietà di navigazione e la visualizzazione e fornisce gli eventi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Abilita esecuzione simile a quella del comando `IOleCommandTarget` per i comandi, ad esempio le operazioni Taglia e ridenominazione che si applicano solo quando lo stato attivo è in Esplora soluzioni.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Funge da interfaccia destinazione comando principale per una gerarchia del progetto. È l'interfaccia standard per eseguire query sugli oggetti per i comandi di stato o dello stato e l'esecuzione di comandi. Disponibile quando non si seleziona nella finestra del progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistenza dello stato del progetto. In genere, lo stato del progetto viene archiviato come un file di progetto, ma può essere adattato per sistemi di archiviazione che non sono basati su file.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Consente al progetto gestire tutti gli aspetti della persistenza per i relativi elementi del progetto, come file su disco o oggetti in altri sistemi di archiviazione. Il `IVsPersistHierarchyItem2` interfaccia viene utilizzata per gli elementi che non implementano la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina le interazioni con controllo del codice sorgente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Consente ai progetti di gestire le informazioni di configurazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gestisce gli oggetti di configurazione di progetto, come le configurazioni di Debug/rilascio. Compilare, distribuire ed eseguire il debug operazioni sono coordinate tramite gli oggetti di configurazione di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementata da gerarchie per controllare l'eliminazione (distruttiva) o rimuovere le opzioni (non distruttiva) per gli elementi della gerarchia. Chiamare l'interfaccia di Query sul `IVsHierarchyDeleteHandler` dell'interfaccia dal `IVsHierarchy` interfaccia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Offre la possibilità di implementazione di modo che l'oggetto che supporta il `IVsCfgProvider2` interfaccia su un'identità COM diversa da quello dell'oggetto di progetto che implementa il `IVsHierarchy` interfaccia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaccia opzionale implementata per rendere estensibile il progetto da altri sviluppatori. Il `IVsProjectStartupServices` interfaccia consente a un VSPackage di terze parti di registrare un GUID che rendono persistenti nel file di progetto in modo che ogni volta che viene caricato il progetto, si carica il GUID del servizio di terze parti nel file di progetto e chiamare `QueryService` per tale GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementata da gerarchie di origine in un `UIHierarchy` finestra per coordinare le operazioni degli Appunti, ad esempio Taglia, copia e Incolla. Usare il `AdviseClipboardHelperEvents` interfaccia per registrare gli eventi negli Appunti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornisce informazioni su un elemento trascinato rispetto alla relativa origine dati durante un'operazione di trascinamento e rilascio in una finestra della gerarchia dell'interfaccia utente. Chiamato dal `IVsHierarchy` interfaccia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornisce informazioni su un elemento trascinato rispetto alla destinazione di rilascio durante un'operazione di trascinamento e rilascio in una finestra della gerarchia dell'interfaccia utente. Chiamato dal `IVsHierarchy` interfaccia.|  
  
### <a name="configuration-object"></a>Oggetto di configurazione  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fornisce informazioni su una configurazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Consente ai progetti di gestire le informazioni di configurazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Consente a un progetto essere eseguito sotto il controllo del debugger.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementata dai progetti di distribuzione che eseguono operazioni di distribuzione per gli altri progetti.|  
  
### <a name="configuration-builder-object"></a>Oggetto generatore di configurazione  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gestisce l'operazione di compilazione di una configurazione di progetto.|  
  
### <a name="additional-project-objects"></a>Altri oggetti del progetto  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Consente di visualizzare le proprietà degli elementi di **proprietà** finestra.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Visualizza gli output per la distribuzione.|  
  
 La tabella seguente presenta una breve descrizione dei servizi identificati nel modello di progetto.  
  
### <a name="services"></a>Servizi  
  
|Service|Commenti|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilizzato dai VSPackages che implementano i tipi di progetto per registrare che esista la factory del progetto con l'IDE. Il pacchetto VSPackage deve chiamare `QueryService` per il servizio e registrare la factory del progetto quando `IVsPackage::SetSite` viene chiamato il metodo. Se il `SetSite` non viene chiamato, il progetto non viene creata un'istanza.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce l'accesso al concetto di interni e predefinito dell'IDE della soluzione corrente, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti, tenere conto di modifiche del progetto e così via.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chiamato dai progetti per partecipare a controllo del codice sorgente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Gestisce una tabella dei documenti aperti per determinare se uno o più elementi del progetto sono già aperto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene le interfacce e metodi chiamati per aprire un elemento del progetto mediante l'editor standard o un editor specifico.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Deve essere chiamato da tutti i progetti durante l'aggiunta, rimuovere o rinominare i rispettivi elementi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gestisce le modifiche apportate a un file o directory e notifica ai client quando i file selezionati sono stati modificati sul disco.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Deve essere chiamato da tutti i progetti ed editor prima di essere dirty elementi o salvarli.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gestisce l'ordine delle operazioni di compilazione e distribuzione per le configurazioni di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornisce accesso ai servizi di debugger di basso livello usati per la maggior parte dei controlli di debug.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Consente l'accesso a pacchetti VSPackage per informazioni sulla selezione corrente e consente la comunicazione con il **proprietà** finestra.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità di base dell'IDE legate all'interfaccia utente, ad esempio la capacità per creare ed enumerare finestre degli strumenti o finestre dei documenti o per segnalare un errore all'utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fornisce l'accesso alla barra di stato dell'IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Usato per implementare il modello di automazione. Nel modello di progetto restituirà un oggetto di proprietà che consente di crea un'istanza di tale oggetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Usato per implementare eventi per gli Appunti per l'oggetto di progetto nella gerarchia. `SVsUIHierWinClipboardHelper` Consente di correttamente handle Taglia, copia e Incolla operazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Non incluso nella Build: Uso delle classi progetto HierUtil7 per implementare un tipo di progetto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Supporto di strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)