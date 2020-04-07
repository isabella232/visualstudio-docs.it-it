---
title: Componenti di base del modello di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706532"
---
# <a name="project-model-core-components"></a>Componenti di base del modello di progetto
Le tabelle seguenti si espandono nel modello di progetto. Le tabelle presentano brevi descrizioni delle interfacce e dei servizi identificati nel modello, none delle interfacce e dei servizi associati a oggetti specifici. Inoltre, nelle tabelle vengono descritte in dettaglio altre interfacce facoltative nella creazione e manutenzione del progetto a seconda dei requisiti del tipo di progetto specifico.

 Per ulteriori informazioni, vedere Supporto degli strumenti di [esplorazione](../../extensibility/internals/supporting-symbol-browsing-tools.md)dei simboli .

### <a name="package-object"></a>Oggetto Package

|Interfaccia|Commenti|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inizializza un pacchetto VSPackage nell'IDE e rende i servizi disponibili per l'IDE.|

### <a name="project-factory-object"></a>Oggetto Factory del progetto

|Interfaccia|Commenti|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gestisce la creazione di nuovi progetti e l'apertura di progetti esistenti.|

### <a name="project-objects"></a>Oggetti di progetto

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gestisce l'aggiunta e la rimozione di elementi di progetto, apre gli `VSITEMID`editor e gestisce il mapping tra ogni moniker del documento e il file . Eredita da `IVsProject` `IVsProject2`e .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gestisce le proprietà di navigazione e visualizzazione e fornisce eventi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Abilita l'esecuzione di `IOleCommandTarget` comandi simile a quella di per i comandi, ad esempio Taglia e Rinomina, che si applicano solo quando lo stato attivo è in Esplora soluzioni.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Funge da interfaccia di destinazione del comando principale per una gerarchia di progetto. È l'interfaccia standard per l'esecuzione di query sugli oggetti per lo stato o lo stato dei comandi e l'esecuzione dei comandi. Disponibile quando non si è concentrati nella finestra progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistenza dello stato del progetto. In genere, lo stato del progetto viene archiviato come file di progetto, ma può essere adattato a sistemi di archiviazione che non sono basati su file.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Consente al progetto di gestire tutti gli aspetti della persistenza per i relativi elementi di progetto, come file su disco o oggetti in altri sistemi di archiviazione. L'interfaccia `IVsPersistHierarchyItem2` viene utilizzata per gli <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> elementi che non implementano l'interfaccia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina le interazioni con il controllo del codice sorgente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Consente ai progetti di gestire le informazioni di configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gestisce gli oggetti di configurazione del progetto, ad esempio le configurazioni Debug/Release. Le operazioni di compilazione, distribuzione e debug vengono coordinate tramite gli oggetti di configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementato da gerarchie per controllare le opzioni di eliminazione (distruttiva) o rimozione (non distruttive) per gli elementi della gerarchia. Chiamare query Interface `IVsHierarchyDeleteHandler` sull'interfaccia dall'interfaccia. `IVsHierarchy`|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fornisce l'opzione di implementazione che `IVsCfgProvider2` consente di disporre dell'oggetto che `IVsHierarchy` supporta l'interfaccia su un'identità COM diversa rispetto all'oggetto di progetto che implementa l'interfaccia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaccia opzionale implementata per rendere il progetto estensibile da altri sviluppatori. L'interfaccia `IVsProjectStartupServices` consente a un VSPackage di terze parti per registrare un GUID che si mantiene nel file di progetto `QueryService` in modo che ogni volta che il progetto viene caricato, si carica il GUID del servizio di terze parti nel file di progetto e chiamare per tale GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementato dalle gerarchie `UIHierarchy` di origine in una finestra per coordinare le operazioni degli Appunti, ad esempio taglia, copia e Incolla. Utilizzare `AdviseClipboardHelperEvents` l'interfaccia per registrare gli eventi degli Appunti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornisce informazioni su un elemento trascinato rispetto alla relativa origine dati durante un'operazione di trascinamento della selezione in una finestra della gerarchia dell'interfaccia utente. Chiamato dall'interfaccia. `IVsHierarchy`|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornisce informazioni su un elemento trascinato rispetto alla relativa destinazione di rilascio durante un'operazione di trascinamento della selezione in una finestra della gerarchia dell'interfaccia utente. Chiamato dall'interfaccia. `IVsHierarchy`|

### <a name="configuration-object"></a>oggetto di configurazione

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fornisce informazioni su una configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Consente ai progetti di gestire le informazioni di configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Consente l'esecuzione di un progetto sotto il controllo del debugger.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementato dai progetti di distribuzione che eseguono operazioni di distribuzione per altri progetti.|

### <a name="configuration-builder-object"></a>Oggetto Configuration Builder

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gestisce l'operazione di compilazione di una configurazione di progetto.|

### <a name="additional-project-objects"></a>Oggetti Project aggiuntivi

|Interfacce|Commenti|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Visualizza le proprietà dell'elemento nella finestra **Proprietà.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Visualizza gli output per la distribuzione.|

 Nella tabella seguente vengono presentate brevi descrizioni dei servizi identificati nel modello di progetto.

### <a name="services"></a>Servizi

|Service|Commenti|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilizzato da VSPackage che implementano i tipi di progetto per registrare che la factory del progetto esiste con l'IDE. Il pacchetto VSPackage deve chiamare `QueryService` per questo `IVsPackage::SetSite` servizio e registrare la factory del progetto quando viene chiamato il metodo. Se `SetSite` il metodo non viene chiamato, non viene creata un'istanza del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce l'accesso alla nozione interna dell'IDE e incorporata della soluzione corrente, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti, prendere nota delle modifiche al progetto e così via.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chiamato da progetti che desiderano partecipare al controllo del codice sorgente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Gestisce una tabella di documenti aperti per determinare se uno o più elementi di progetto sono già aperti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene le interfacce e i metodi chiamati per aprire effettivamente un elemento di progetto utilizzando l'editor standard o un editor specifico.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Obbligatorio per essere chiamato da tutti i progetti quando aggiungono, rimuovono o rinominano i relativi elementi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gestisce le modifiche apportate a un file o a una directory e notifica ai client quando i file selezionati sono stati modificati su disco.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Necessario per essere chiamato da tutti i progetti e gli editor prima di sporcare gli elementi o salvarli.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gestisce l'ordine delle operazioni di compilazione e distribuzione per le configurazioni di progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornisce l'accesso ai servizi del debugger di basso livello utilizzati per la maggior parte dei controlli di debug.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Abilita VSPackage l'accesso alle informazioni sulle selezioni correnti e consente la comunicazione con il **proprietà** finestra.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità IDE di base correlate all'interfaccia utente, ad esempio la possibilità di creare ed enumerare finestre degli strumenti o finestre di documento o di segnalare un errore all'utente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fornisce l'accesso alla barra di stato dell'IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Utilizzato per implementare il modello di automazione. Nel modello di progetto verrà restituito un oggetto properties che consente di creare un'istanza di tale oggetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Utilizzato per implementare gli eventi degli Appunti sull'oggetto di progetto nella gerarchia. `SVsUIHierWinClipboardHelper`consente di gestire correttamente le operazioni di taglio, copia e incolla.|

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Non in compilazione: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto (c ')](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)
