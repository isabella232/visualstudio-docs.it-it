---
title: Project Componenti di base del modello | Microsoft Docs
description: Questo articolo contiene descrizioni delle interfacce e dei servizi identificati nel core del modello di progetto e delle interfacce e dei servizi associati agli oggetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8a0993a35a9de27ddbfe03ae25e47cdb74af2429
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063005"
---
# <a name="project-model-core-components"></a>Componenti di base del modello di progetto
Le tabelle seguenti si espandono nel modello di progetto. Le tabelle presentano brevi descrizioni delle interfacce e dei servizi identificati nel modello e delle interfacce e dei servizi associati a oggetti specifici. Inoltre, le tabelle dettaglino altre interfacce facoltative nella creazione e nella manutenzione del progetto a seconda dei requisiti del tipo di progetto specifico.

 Per altre informazioni, vedere [Supporting Symbol-Browsing Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Oggetto package

|Interfaccia|Commenti|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inizializza un VSPackage nell'IDE e rende i relativi servizi disponibili per l'IDE.|

### <a name="project-factory-object"></a>Project Oggetto factory

|Interfaccia|Commenti|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gestisce la creazione di nuovi progetti e l'apertura di progetti esistenti.|

### <a name="project-objects"></a>Project oggetti

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gestisce l'aggiunta e la rimozione di elementi di progetto, apre gli editor e mantiene il mapping tra ogni moniker di documento e `VSITEMID` . Eredita da `IVsProject` e `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gestisce le proprietà di navigazione e visualizzazione e fornisce eventi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Abilita l'esecuzione dei comandi simile a quella di per comandi come Taglia e Rinomina che si applicano solo quando lo stato attivo è `IOleCommandTarget` Esplora soluzioni.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Funge da interfaccia di destinazione del comando principale per una gerarchia di progetto. È l'interfaccia standard per l'esecuzione di query sugli oggetti per lo stato o lo stato del comando e per l'esecuzione di comandi. Disponibile quando non si ha lo stato attivo nella Project.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistenza dello stato del progetto. In genere, lo stato del progetto viene archiviato come file di progetto, ma può essere adattato ai sistemi di archiviazione che non sono basati su file.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Consente al progetto di gestire tutti gli aspetti della persistenza per gli elementi del progetto, come file su disco o oggetti in altri sistemi di archiviazione. `IVsPersistHierarchyItem2`L'interfaccia viene usata per gli elementi che non implementano l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina le interazioni con il controllo del codice sorgente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Consente ai progetti di gestire le informazioni di configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gestisce gli oggetti di configurazione del progetto, ad esempio le configurazioni di debug/rilascio. Le operazioni di compilazione, distribuzione ed debug vengono coordinate tramite oggetti di configurazione del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementato dalle gerarchie per controllare le opzioni di eliminazione (distruttive) o di rimozione (non distruttive) per gli elementi della gerarchia. Chiamare Query Interface `IVsHierarchyDeleteHandler` sull'interfaccia `IVsHierarchy` dall'interfaccia .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fornisce l'opzione di implementazione dell'oggetto che supporta l'interfaccia su un'identità COM diversa rispetto all'oggetto di progetto `IVsCfgProvider2` che implementa `IVsHierarchy` l'interfaccia .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaccia facoltativa implementata per rendere il progetto estendibile da altri sviluppatori. L'interfaccia consente a un VSPackage di terze parti di registrare un GUID persistente nel file di progetto in modo che ogni volta che il progetto viene caricato, si carica il GUID del servizio di terze parti nel file di progetto e si chiama per tale `IVsProjectStartupServices` `QueryService` GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementato dalle gerarchie di origine in una finestra per coordinare le operazioni degli Appunti, ad esempio `UIHierarchy` taglia, copia e incolla. Usare `AdviseClipboardHelperEvents` l'interfaccia per registrare gli eventi degli Appunti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornisce informazioni su un elemento trascinato relativo all'origine dati durante un'operazione di trascinamento della selezione in una finestra della gerarchia dell'interfaccia utente. Chiamato `IVsHierarchy` dall'interfaccia .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornisce informazioni su un elemento trascinato relativo alla relativa destinazione di rilascio durante un'operazione di trascinamento della selezione in una finestra della gerarchia dell'interfaccia utente. Chiamato `IVsHierarchy` dall'interfaccia .|

### <a name="configuration-object"></a>oggetto di configurazione

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fornisce informazioni su una configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Consente ai progetti di gestire le informazioni di configurazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Consente l'esecuzione di un progetto sotto il controllo del debugger.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementato da progetti di distribuzione che eseguono operazioni di distribuzione per altri progetti.|

### <a name="configuration-builder-object"></a>Oggetto di Configuration Builder

|Interfacce|Commenti|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gestisce l'operazione di compilazione di una configurazione di progetto.|

### <a name="additional-project-objects"></a>Oggetti Project aggiuntivi

|Interfacce|Commenti|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Visualizza le proprietà dell'elemento **nella finestra** Proprietà.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Visualizza gli output per la distribuzione.|

 La tabella seguente presenta brevi descrizioni dei servizi identificati nel modello di progetto.

### <a name="services"></a>Servizi

|Servizio|Commenti|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Usato da VSPackage che implementano tipi di progetto per registrare che la factory del progetto esiste con l'IDE. Il pacchetto VSPackage deve `QueryService` chiamare per questo servizio e registrare la factory del progetto quando viene chiamato il metodo `IVsPackage::SetSite` . Se il `SetSite` metodo non viene chiamato, non viene creata un'istanza del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce l'accesso alla nozione interna e incorporata dell'IDE della soluzione corrente, ad esempio la possibilità di enumerare progetti, creare nuovi progetti, prendere nota delle modifiche del progetto e così via.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chiamato dai progetti che vogliono partecipare al controllo del codice sorgente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Gestisce una tabella di documenti aperti per determinare se uno o più elementi del progetto sono già aperti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene le interfacce e i metodi chiamati per aprire effettivamente un elemento di progetto usando l'editor standard o un editor specifico.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Deve essere chiamato da tutti i progetti quando aggiungono, rimuovono o rinominano gli elementi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gestisce le modifiche apportate a un file o a una directory e invia una notifica ai client quando i file selezionati sono stati modificati su disco.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Deve essere chiamato da tutti i progetti e gli editor prima di eseguire lo dirty degli elementi o salvarli.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gestisce l'ordine delle operazioni di compilazione e distribuzione per le configurazioni del progetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornisce l'accesso ai servizi debugger di basso livello usati per la maggior parte dei controlli di debug.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Consente ai pacchetti VSPackage di accedere alle informazioni sulle selezioni correnti e consente la comunicazione con la **finestra** Proprietà.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità IDE correlate all'interfaccia utente di base, ad esempio la possibilità di creare ed enumerare finestre degli strumenti o finestre del documento o di segnalare un errore all'utente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fornisce l'accesso alla barra di stato dell'IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Usato per implementare il modello di automazione. Nel modello di progetto si restituirà un oggetto proprietà che consente di creare un'istanza di tale oggetto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Usato per implementare gli eventi degli Appunti nell'oggetto progetto nella gerarchia. `SVsUIHierWinClipboardHelper` consente di gestire correttamente le operazioni taglia, copia e incolla.|

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Non in compilazione: uso di hierUtil7 Project classi per implementare un Project tipo (C++)](/previous-versions/bb166212(v=vs.100))
- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)