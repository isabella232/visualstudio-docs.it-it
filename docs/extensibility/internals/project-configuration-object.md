---
title: Oggetto configurazione progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725830"
---
# <a name="project-configuration-object"></a>Oggetto di configurazione del progetto
L'oggetto configurazione progetto gestisce la visualizzazione delle informazioni di configurazione nell'interfaccia utente.

 ![Configurazione del progetto di Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Pagine delle proprietà di configurazione del progetto

 Il provider di configurazione del progetto gestisce le configurazioni del progetto. L'ambiente e altri pacchetti, per ottenere l'accesso e recuperare informazioni sulle configurazioni di un progetto, chiamano le interfacce collegate all'oggetto provider di configurazione del progetto.

> [!NOTE]
> Non è possibile creare o modificare i file di configurazione della soluzione a livello di codice. È necessario utilizzare `DTE.SolutionBuilder`. Per ulteriori informazioni, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md) .

 Per pubblicare un nome visualizzato da usare nell'interfaccia utente di configurazione, il progetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, che restituisce un elenco di puntatori `IVsCfg` che è possibile usare per ottenere i nomi visualizzati per le informazioni di configurazione e piattaforma da elencare nell'interfaccia utente dell'ambiente. La configurazione e la piattaforma attive sono determinate dalla configurazione del progetto archiviata nella configurazione della soluzione attiva. Il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> può essere utilizzato per recuperare la configurazione del progetto attivo.

 L'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> può facoltativamente essere implementato nell'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> con l'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> per consentire il recupero di un oggetto `IVsProjectCfg2` basato sul nome della configurazione del progetto canonico.

 Un altro modo per fornire all'ambiente e altri progetti con accesso alle configurazioni di progetto è che i progetti forniscano un'implementazione del metodo `IVsCfgProvider2::GetCfgs` per restituire uno o più oggetti di configurazione. I progetti possono anche implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, che eredita da `IVsProjectCfg` e quindi da `IVsCfg`, per fornire informazioni specifiche della configurazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> supporta le piattaforme e le funzionalità per l'aggiunta, l'eliminazione e la ridenominazione delle configurazioni di progetto.

> [!NOTE]
> Poiché Visual Studio non è più limitato a due tipi di configurazione, il codice che elabora le configurazioni non deve essere scritto con presupposti sul numero di configurazioni, né deve essere scritto con il presupposto che un progetto con un solo la configurazione è necessariamente debug o al dettaglio. In questo modo l'uso di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleti.

 La chiamata di `QueryInterface` sull'oggetto restituito da `IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Se `IVsGetCfgProvider` non viene trovato chiamando `QueryInterface` nell'oggetto `IVsProject3` Project, è possibile accedere all'oggetto provider di configurazione chiamando `QueryInterface` nell'oggetto del browser radice della gerarchia per l'oggetto restituito per `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` o tramite un puntatore alla configurazione. provider restituito per `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 `IVsProjectCfg2` fornisce principalmente l'accesso agli oggetti di compilazione, debug e gestione della distribuzione e consente ai progetti di raggruppare gli output. I metodi di `IVsProjectCfg` e di `IVsProjectCfg2` possono essere utilizzati per implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> per gestire il processo di compilazione e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> i puntatori per i gruppi di output di una configurazione.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supportata anche se il numero di output contenuti in un gruppo può variare dalla configurazione alla configurazione. I gruppi devono avere anche le stesse informazioni sull'identificatore (nome canonico, nome visualizzato e informazioni sul gruppo) dalla configurazione alla configurazione all'interno di un progetto. Per altre informazioni, vedere [configurazione di progetto per l'output](../../extensibility/internals/project-configuration-for-output.md).

 Per abilitare il debug, le configurazioni devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` è un'interfaccia facoltativa implementata dai progetti per consentire al debugger di avviare una configurazione e viene implementata nell'oggetto di configurazione con `IVsCfg` e `IVsProjectCfg`. L'ambiente lo chiama quando l'utente sceglie di avviare il debugger premendo F5.

 `ISpecifyPropertyPages` e `IDispatch` vengono utilizzati in combinazione con le pagine delle proprietà per recuperare e visualizzare all'utente le informazioni dipendenti dalla configurazione. Per ulteriori informazioni, vedere [pagine delle proprietà](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)
- [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)