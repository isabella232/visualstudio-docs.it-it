---
title: Project Oggetto configuration | Microsoft Docs
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
ms.openlocfilehash: a84f6d8f635698ac02b05efac9fa3e3110d2e293f6e5ba5a3c7e3f96fe2a703c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321272"
---
# <a name="project-configuration-object"></a>Oggetto di configurazione del progetto
L'oggetto di configurazione del progetto gestisce la visualizzazione delle informazioni di configurazione nell'interfaccia utente.

 ![Visual Studio Project configuration Project](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") delle proprietà di configurazione

 Il Project configuration provider gestisce le configurazioni del progetto. L'ambiente e altri pacchetti, per ottenere l'accesso e recuperare informazioni sulle configurazioni di un progetto, chiamare le interfacce associate Project oggetto provider di configurazione.

> [!NOTE]
> Non è possibile creare o modificare i file di configurazione della soluzione a livello di codice. È necessario utilizzare `DTE.SolutionBuilder`. Per [altre informazioni, vedere](../../extensibility/internals/solution-configuration.md) Configurazione della soluzione.

 Per pubblicare un nome visualizzato da usare nell'interfaccia utente di configurazione, il progetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . L'ambiente chiama , che restituisce un elenco di puntatori che è possibile usare per ottenere i nomi visualizzati per le informazioni di configurazione e piattaforma da elencare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> `IVsCfg` nell'interfaccia utente dell'ambiente. La configurazione e la piattaforma attive sono determinate dalla configurazione del progetto archiviata nella configurazione della soluzione attiva. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> metodo può essere usato per recuperare la configurazione del progetto attivo.

 Facoltativamente, l'oggetto può essere implementato nell'oggetto con l'oggetto per consentire di recuperare un oggetto in base al nome di configurazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> `IVsProjectCfg2` canonico del progetto.

 Un altro modo per fornire all'ambiente e ad altri progetti l'accesso alle configurazioni di progetto è consentire ai progetti di fornire un'implementazione del metodo per restituire uno o `IVsCfgProvider2::GetCfgs` più oggetti di configurazione. I progetti possono anche implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , che eredita da e quindi da , per fornire informazioni specifiche della `IVsProjectCfg` `IVsCfg` configurazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> supporta piattaforme e funzionalità per l'aggiunta, l'eliminazione e la ridenominazione delle configurazioni di progetto.

> [!NOTE]
> Poiché Visual Studio non è più limitato a due tipi di configurazione, il codice che elabora le configurazioni non deve essere scritto con presupposti sul numero di configurazioni, né deve essere scritto presupponendo che un progetto con una sola configurazione sia necessariamente Debug o Retail. Questo rende obsoleto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> l'uso di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> e .

 La `QueryInterface` chiamata all'oggetto restituito `IVsGetCfgProvider::GetCfgProvider` da recupera `IVsCfgProvider2` . Se non viene trovato chiamando sull'oggetto del progetto, è possibile accedere all'oggetto provider di configurazione chiamando sull'oggetto browser radice della gerarchia per l'oggetto restituito per o tramite un puntatore al provider di configurazione restituito `IVsGetCfgProvider` `QueryInterface` per `IVsProject3` `QueryInterface` `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` fornisce principalmente l'accesso agli oggetti di gestione della compilazione, del debug e della distribuzione e consente ai progetti di raggruppare gli output. I metodi di e possono essere usati per implementare per gestire il processo di compilazione e i puntatori `IVsProjectCfg` per i gruppi di output di una `IVsProjectCfg2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> configurazione.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione che supporta anche se il numero di output contenuti in un gruppo può variare da una configurazione all'altro. I gruppi devono inoltre avere le stesse informazioni sull'identificatore (nome canonico, nome visualizzato e informazioni sui gruppi) dalla configurazione alla configurazione all'interno di un progetto. Per altre informazioni, vedere [Configurazione Project per l'output.](../../extensibility/internals/project-configuration-for-output.md)

 Per abilitare il debug, le configurazioni devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` è un'interfaccia facoltativa implementata dai progetti per consentire al debugger di avviare una configurazione e viene implementata nell'oggetto di configurazione con `IVsCfg` e `IVsProjectCfg` . L'ambiente lo chiama quando l'utente sceglie di avviare il debugger premendo F5.

 `ISpecifyPropertyPages` e vengono usati insieme alle pagine delle proprietà per recuperare e visualizzare all'utente informazioni dipendenti `IDispatch` dalla configurazione. Per altre informazioni, vedere [Pagine delle proprietà.](../../extensibility/internals/property-pages.md)

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
