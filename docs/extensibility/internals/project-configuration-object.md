---
title: Oggetto configurazione progetto | Microsoft Docs
description: Informazioni sul modo in cui l'oggetto di configurazione del progetto gestisce la visualizzazione delle informazioni di configurazione nell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a17d5ed54e74b5632d02f8f8013a9098aaab0a49
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062902"
---
# <a name="project-configuration-object"></a>Oggetto di configurazione del progetto
L'oggetto configurazione progetto gestisce la visualizzazione delle informazioni di configurazione nell'interfaccia utente.

 ![Configurazione del progetto di Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Pagine delle proprietà di configurazione del progetto

 Il provider di configurazione del progetto gestisce le configurazioni del progetto. L'ambiente e altri pacchetti, per ottenere l'accesso e recuperare informazioni sulle configurazioni di un progetto, chiamano le interfacce collegate all'oggetto provider di configurazione del progetto.

> [!NOTE]
> Non è possibile creare o modificare i file di configurazione della soluzione a livello di codice. È necessario utilizzare `DTE.SolutionBuilder`. Per ulteriori informazioni, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md) .

 Per pubblicare un nome visualizzato da usare nell'interfaccia utente di configurazione, il progetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , che restituisce un elenco di `IVsCfg` puntatori che è possibile usare per ottenere i nomi visualizzati per la configurazione e le informazioni della piattaforma da elencare nell'interfaccia utente dell'ambiente. La configurazione e la piattaforma attive sono determinate dalla configurazione del progetto archiviata nella configurazione della soluzione attiva. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> metodo può essere utilizzato per recuperare la configurazione del progetto attivo.

 L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> oggetto può facoltativamente essere implementato nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> oggetto con l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> oggetto per consentire il recupero di un `IVsProjectCfg2` oggetto in base al nome canonico della configurazione del progetto.

 Un altro modo per fornire all'ambiente e altri progetti con accesso alle configurazioni di progetto è che i progetti forniscano un'implementazione del `IVsCfgProvider2::GetCfgs` metodo per restituire uno o più oggetti di configurazione. I progetti possono anche implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , che eredita da `IVsProjectCfg` e quindi da `IVsCfg` , per fornire informazioni specifiche della configurazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> supporta le piattaforme e le funzionalità per l'aggiunta, l'eliminazione e la ridenominazione delle configurazioni di progetto.

> [!NOTE]
> Poiché Visual Studio non è più limitato a due tipi di configurazione, il codice che elabora le configurazioni non deve essere scritto con presupposti sul numero di configurazioni, né deve essere scritto con il presupposto che un progetto con una sola configurazione sia necessariamente debug o al dettaglio. In questo modo viene utilizzato <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleto.

 Chiamata all' `QueryInterface` oggetto restituito da `IVsGetCfgProvider::GetCfgProvider` retrieves `IVsCfgProvider2` . Se `IVsGetCfgProvider` non viene trovato chiamando `QueryInterface` sull'oggetto del `IVsProject3` progetto, è possibile accedere all'oggetto provider di configurazione chiamando `QueryInterface` sull'oggetto del browser radice della gerarchia per l'oggetto restituito per `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` oppure tramite un puntatore al provider di configurazione restituito per `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` fornisce principalmente l'accesso agli oggetti di compilazione, debug e gestione della distribuzione e consente ai progetti di raggruppare gli output. I metodi di `IVsProjectCfg` e `IVsProjectCfg2` possono essere usati per implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> per gestire il processo di compilazione e i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> puntatori per i gruppi di output di una configurazione.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supportata anche se il numero di output contenuti in un gruppo può variare dalla configurazione alla configurazione. I gruppi devono avere anche le stesse informazioni sull'identificatore (nome canonico, nome visualizzato e informazioni sul gruppo) dalla configurazione alla configurazione all'interno di un progetto. Per altre informazioni, vedere [configurazione di progetto per l'output](../../extensibility/internals/project-configuration-for-output.md).

 Per abilitare il debug, le configurazioni devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` è un'interfaccia facoltativa implementata dai progetti per consentire al debugger di avviare una configurazione e viene implementata nell'oggetto di configurazione con `IVsCfg` e `IVsProjectCfg` . L'ambiente lo chiama quando l'utente sceglie di avviare il debugger premendo F5.

 `ISpecifyPropertyPages` e `IDispatch` vengono utilizzati in combinazione con le pagine delle proprietà per recuperare e visualizzare le informazioni dipendenti dalla configurazione per l'utente. Per ulteriori informazioni, vedere [pagine delle proprietà](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
