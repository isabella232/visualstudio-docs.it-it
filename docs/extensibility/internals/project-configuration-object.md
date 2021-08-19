---
title: Project Oggetto di configurazione | Microsoft Docs
description: Informazioni su come l'oggetto di configurazione del progetto gestisce la visualizzazione delle informazioni di configurazione nell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b20d476f322a3240313ef6a851bef39f6c169623
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152419"
---
# <a name="project-configuration-object"></a>Oggetto di configurazione del progetto
L'oggetto di configurazione del progetto gestisce la visualizzazione delle informazioni di configurazione nell'interfaccia utente.

 ![Visual Studio Project configurazione Project](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") delle proprietà di configurazione

 Il Project configuration provider gestisce le configurazioni del progetto. L'ambiente e altri pacchetti, per ottenere l'accesso e recuperare informazioni sulle configurazioni di un progetto, chiamare le interfacce associate all'Project provider di configurazione.

> [!NOTE]
> Non è possibile creare o modificare i file di configurazione della soluzione a livello di codice. È necessario utilizzare `DTE.SolutionBuilder`. Per [altre informazioni, vedere Configurazione](../../extensibility/internals/solution-configuration.md) della soluzione.

 Per pubblicare un nome visualizzato da usare nell'interfaccia utente di configurazione, il progetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . L'ambiente chiama , che restituisce un elenco di puntatori che è possibile usare per ottenere i nomi visualizzati per le informazioni di configurazione e piattaforma da elencare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> `IVsCfg` nell'interfaccia utente dell'ambiente. La configurazione e la piattaforma attive sono determinate dalla configurazione del progetto archiviata nella configurazione della soluzione attiva. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> metodo può essere usato per recuperare la configurazione del progetto attivo.

 L'oggetto può essere implementato facoltativamente nell'oggetto con l'oggetto per consentire di recuperare un oggetto in base al nome di configurazione del progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> `IVsProjectCfg2` canonico.

 Un altro modo per fornire all'ambiente e ad altri progetti l'accesso alle configurazioni di progetto è che i progetti forniranno un'implementazione del metodo per `IVsCfgProvider2::GetCfgs` restituire uno o più oggetti di configurazione. I progetti possono anche implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , che eredita da e quindi da , per fornire informazioni specifiche della `IVsProjectCfg` `IVsCfg` configurazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> supporta le piattaforme e le funzionalità per l'aggiunta, l'eliminazione e la ridenominazione delle configurazioni di progetto.

> [!NOTE]
> Poiché Visual Studio non è più limitato a due tipi di configurazione, il codice che elabora le configurazioni non deve essere scritto con presupposti sul numero di configurazioni, né deve essere scritto con il presupposto che un progetto con una sola configurazione sia necessariamente Debug o Vendita al dettaglio. In questo modo viene utilizzato e <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleto.

 La `QueryInterface` chiamata sull'oggetto restituito `IVsGetCfgProvider::GetCfgProvider` da recupera `IVsCfgProvider2` . Se non viene trovato chiamando sull'oggetto progetto, è possibile accedere all'oggetto provider di configurazione chiamando sull'oggetto browser radice della gerarchia per l'oggetto restituito per o tramite un puntatore al provider di configurazione restituito per `IVsGetCfgProvider` `QueryInterface` `IVsProject3` `QueryInterface` `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` fornisce principalmente l'accesso agli oggetti di gestione di compilazione, debug e distribuzione e consente ai progetti la libertà di raggruppare gli output. I metodi di e possono essere usati per implementare per gestire il processo di compilazione e puntatori `IVsProjectCfg` per i gruppi di output di una `IVsProjectCfg2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> configurazione.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione che supporta anche se il numero di output contenuti in un gruppo può variare da configurazione a configurazione. I gruppi devono avere anche le stesse informazioni sull'identificatore (nome canonico, nome visualizzato e informazioni sul gruppo) dalla configurazione alla configurazione all'interno di un progetto. Per altre informazioni, vedere Configurazione [Project per Output](../../extensibility/internals/project-configuration-for-output.md).

 Per abilitare il debug, le configurazioni devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` è un'interfaccia facoltativa implementata dai progetti per consentire al debugger di avviare una configurazione e viene implementata nell'oggetto di configurazione con `IVsCfg` e `IVsProjectCfg` . L'ambiente lo chiama quando l'utente sceglie di avviare il debugger premendo F5.

 `ISpecifyPropertyPages` e vengono utilizzati insieme alle pagine delle proprietà per recuperare e visualizzare le informazioni dipendenti dalla `IDispatch` configurazione all'utente. Per altre informazioni, vedere [Pagine delle proprietà](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
