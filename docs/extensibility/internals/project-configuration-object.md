---
title: Oggetto di configurazione del progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706649"
---
# <a name="project-configuration-object"></a>Oggetto di configurazione del progetto
L'oggetto di configurazione del progetto gestisce la visualizzazione delle informazioni di configurazione all'interfaccia utente.

 ![Configurazione del progetto di Visual StudioVisual Studio Project Configuration](../../extensibility/internals/media/vsprojectcfg.gif "VsProjectCfg (informazioni in base al taè") Pagine delle proprietà di configurazione del progettoProject configuration property pages

 Il provider di configurazione del progetto gestisce le configurazioni di progetto. L'ambiente e altri pacchetti, per ottenere l'accesso e recuperare informazioni sulle configurazioni di un progetto, chiamare le interfacce associate all'oggetto provider di configurazione del progetto.

> [!NOTE]
> Non è possibile creare o modificare i file di configurazione della soluzione a livello di codice. È necessario utilizzare `DTE.SolutionBuilder`. Per altre informazioni, vedere [Configurazione della soluzione.](../../extensibility/internals/solution-configuration.md)

 Per pubblicare un nome visualizzato da utilizzare nell'interfaccia utente di configurazione, il progetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. L'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>chiama , che `IVsCfg` restituisce un elenco di puntatori che è possibile utilizzare per ottenere i nomi visualizzati per le informazioni di configurazione e piattaforma da elencare nell'interfaccia utente dell'ambiente. La configurazione e la piattaforma attive sono determinate dalla configurazione del progetto archiviata nella configurazione della soluzione attiva. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> metodo può essere utilizzato per recuperare la configurazione attiva del progetto.

 L'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> può essere implementato <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> facoltativamente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> sull'oggetto con `IVsProjectCfg2` l'oggetto per consentire di recuperare un oggetto in base al nome di configurazione del progetto canonico.

 Un altro modo per fornire l'accesso alle configurazioni di progetto `IVsCfgProvider2::GetCfgs` nell'ambiente e in altri progetti consiste nel fornire ai progetti un'implementazione del metodo per restituire uno o più oggetti di configurazione. I progetti possono <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>anche implementare `IVsProjectCfg` , che `IVsCfg`eredita da e quindi da , per fornire informazioni specifiche della configurazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>supporta le piattaforme e le funzionalità per l'aggiunta, l'eliminazione e la ridenominazione delle configurazioni di progetto.

> [!NOTE]
> Poiché Visual Studio non è più limitato a due tipi di configurazione, il codice che elabora le configurazioni non deve essere scritto con presupposti sul numero di configurazioni, né deve essere scritto presupponendo che un progetto con una sola configurazione sia necessariamente Debug o Retail. Questo rende l'uso di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleto.

 La `QueryInterface` chiamata sull'oggetto`IVsGetCfgProvider::GetCfgProvider` restituito `IVsCfgProvider2`da recupera . Se `IVsGetCfgProvider` non viene `QueryInterface` trovato `IVsProject3` chiamando sull'oggetto del progetto, è `QueryInterface` possibile accedere all'oggetto provider di `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`configurazione chiamando l'oggetto browser radice `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`della gerarchia per l'oggetto restituito per , oppure tramite un puntatore al provider di configurazione restituito per .

 `IVsProjectCfg2`fornisce principalmente l'accesso agli oggetti di gestione di compilazione, debug e distribuzione e consente ai progetti la libertà di raggruppare gli output. I metodi `IVsProjectCfg` `IVsProjectCfg2` di e possono <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> essere utilizzati per <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> implementare per gestire il processo di compilazione e puntatori per i gruppi di output di una configurazione.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supportata anche se il numero di output contenuti in un gruppo può variare da configurazione a configurazione. I gruppi devono inoltre avere le stesse informazioni sull'identificatore (nome canonico, nome visualizzato e informazioni sul gruppo) dalla configurazione alla configurazione all'interno di un progetto. Per ulteriori informazioni, vedere [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md).

 Per abilitare il debug, le configurazioni devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg`è un'interfaccia facoltativa implementata dai progetti per consentire al debugger `IVsCfg` di `IVsProjectCfg`avviare una configurazione e viene implementata nell'oggetto di configurazione con e . L'ambiente chiama quando l'utente sceglie di avviare il debugger premendo F5.

 `ISpecifyPropertyPages`e `IDispatch` vengono utilizzati insieme alle pagine delle proprietà per recuperare e visualizzare informazioni dipendenti dalla configurazione per l'utente. Per ulteriori informazioni, consultate [Pagine delle proprietà.](../../extensibility/internals/property-pages.md)

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)
- [Configurazione soluzione](../../extensibility/internals/solution-configuration.md)
