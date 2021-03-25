---
title: Componenti di base del modello di progetto | Microsoft Docs
description: Questo articolo contiene le descrizioni delle interfacce e dei servizi identificati nel nucleo del modello di progetto e le interfacce e i servizi associati agli oggetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ae01d149611afe5bf75a6952f19baff7d70f6210
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062811"
---
# <a name="project-model-core-components"></a>Componenti di base del modello di progetto
Le tabelle seguenti si espandono sul modello di progetto. Le tabelle presentano brevi descrizioni delle interfacce e dei servizi identificati nel modello e delle interfacce e dei servizi associati a oggetti specifici. Inoltre, le tabelle illustrano in dettaglio altre interfacce facoltative per la creazione e la manutenzione di progetti, a seconda dei requisiti del tipo di progetto specifico.

 Per ulteriori informazioni, vedere [supporto di Symbol-Browsing Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Oggetto Package

|Interfaccia|Commenti|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inizializza un VSPackage nell'IDE e rende disponibili i relativi servizi per l'IDE.|

### <a name="project-factory-object"></a>Oggetto Factory progetto

|Interfaccia|Commenti|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gestisce la creazione di nuovi progetti e l'apertura di progetti esistenti.|

### <a name="project-objects"></a>Oggetti progetto

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gestisce l'aggiunta e la rimozione di elementi di progetto, apre gli editor e mantiene il mapping tra ogni moniker di documento e `VSITEMID` . Eredita da `IVsProject` e `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gestisce le proprietà di navigazione e visualizzazione e fornisce gli eventi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Consente l'esecuzione del comando in modo analogo a quella di `IOleCommandTarget` per i comandi come taglia e Rinomina che si applicano solo quando lo stato attivo è in Esplora soluzioni.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Funge da interfaccia di destinazione principale del comando per una gerarchia del progetto. Si tratta dell'interfaccia standard per eseguire query sugli oggetti per lo stato dei comandi o lo stato e i comandi in esecuzione. Disponibile quando non si è nello stato attivo nella finestra del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistenza dello stato del progetto. In genere, lo stato del progetto viene archiviato come file di progetto, ma può essere adattato ai sistemi di archiviazione che non sono basati su file.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Consente al progetto di gestire tutti gli aspetti di persistenza per gli elementi del progetto, come file su disco o oggetti in altri sistemi di archiviazione. L' `IVsPersistHierarchyItem2` interfaccia viene utilizzata per gli elementi che non implementano l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina le interazioni con il controllo del codice sorgente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Consente ai progetti di gestire le informazioni di configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gestisce gli oggetti di configurazione del progetto, ad esempio le configurazioni di debug/rilascio. Le operazioni di compilazione, distribuzione e debug sono coordinate tramite oggetti di configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementato dalle gerarchie per controllare le opzioni Delete (distruttive) o Remove (non distruttive) per gli elementi della gerarchia. Chiamare l'interfaccia di query sull' `IVsHierarchyDeleteHandler` interfaccia dall' `IVsHierarchy` interfaccia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fornisce l'opzione di implementazione di con l'oggetto che supporta l' `IVsCfgProvider2` interfaccia su un'identità com diversa rispetto all'oggetto progetto che implementa l' `IVsHierarchy` interfaccia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaccia facoltativa implementata per rendere il progetto estendibile da altri sviluppatori. L' `IVsProjectStartupServices` interfaccia consente a un VSPackage di terze parti di registrare un GUID che viene mantenuto nel file di progetto in modo che ogni volta che il progetto viene caricato, caricare il GUID del servizio di terze parti nel file di progetto e chiamare `QueryService` per tale GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementato dalle gerarchie di origine in una `UIHierarchy` finestra per coordinare le operazioni degli Appunti, ad esempio taglia, copia e incolla. Utilizzare l' `AdviseClipboardHelperEvents` interfaccia per registrare gli eventi degli Appunti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornisce informazioni su un elemento trascinato relativo alla relativa origine dati durante un'operazione di trascinamento della selezione in una finestra della gerarchia dell'interfaccia utente. Chiamato dall' `IVsHierarchy` interfaccia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornisce informazioni su un elemento trascinato relativo alla destinazione di rilascio durante un'operazione di trascinamento della selezione in una finestra della gerarchia dell'interfaccia utente. Chiamato dall' `IVsHierarchy` interfaccia.|

### <a name="configuration-object"></a>oggetto di configurazione

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fornisce informazioni su una configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Consente ai progetti di gestire le informazioni di configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Consente l'esecuzione di un progetto sotto il controllo del debugger.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementata dai progetti di distribuzione che eseguono operazioni di distribuzione per altri progetti.|

### <a name="configuration-builder-object"></a>Oggetto generatore di configurazione

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gestisce l'operazione di compilazione di una configurazione di progetto.|

### <a name="additional-project-objects"></a>Oggetti di progetto aggiuntivi

|Interfacce|Commenti|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Consente di visualizzare le proprietà dell'elemento nella finestra **Proprietà** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Visualizza gli output per la distribuzione.|

 Nella tabella seguente vengono presentate brevi descrizioni dei servizi identificati nel modello di progetto.

### <a name="services"></a>Servizi

|Servizio|Commenti|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Usato da VSPackage che implementano i tipi di progetto per registrare che la relativa factory di progetto esiste con l'IDE. Il pacchetto VSPackage deve chiamare `QueryService` per questo servizio e registrare la factory del progetto quando `IVsPackage::SetSite` viene chiamato il metodo. Se il `SetSite` metodo non viene chiamato, non viene creata un'istanza del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce l'accesso alla nozione interna incorporata dell'IDE della soluzione corrente, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti, prendere nota delle modifiche del progetto e così via.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chiamato dai progetti che desiderano partecipare al controllo del codice sorgente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantiene una tabella di documenti aperti per determinare se uno o più elementi del progetto sono già aperti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene le interfacce e i metodi chiamati per aprire effettivamente un elemento del progetto utilizzando l'editor standard o un editor specifico.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Deve essere chiamato da tutti i progetti quando aggiungono, rimuovono o rinominano gli elementi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gestisce le modifiche apportate a un file o a una directory e invia una notifica ai client quando i file selezionati sono stati modificati su disco.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Deve essere chiamato da tutti i progetti e gli editor prima che vengano modificati o salvati.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gestisce l'ordine delle operazioni di compilazione e distribuzione per le configurazioni di progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornisce l'accesso ai servizi del debugger di basso livello utilizzati per la maggior parte dei controlli di debug.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Consente ai VSPackage di accedere alle informazioni sulle selezioni correnti e Abilita la comunicazione con la finestra **Proprietà** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità di base dell'IDE correlate all'interfaccia utente, ad esempio la possibilità di creare ed enumerare finestre degli strumenti o finestre dei documenti o di segnalare un errore all'utente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fornisce l'accesso alla barra di stato dell'IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Utilizzato per implementare il modello di automazione. Nel modello di progetto verrà restituito un oggetto Properties che consente di creare un'istanza di tale oggetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Utilizzato per implementare gli eventi degli Appunti nell'oggetto progetto nella gerarchia. `SVsUIHierWinClipboardHelper` consente di gestire correttamente le operazioni Taglia, copia e incolla.|

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Not in Build: uso delle classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](/previous-versions/bb166212(v=vs.100))
- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)