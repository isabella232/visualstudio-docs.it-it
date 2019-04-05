---
title: Oggetto di configurazione di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d84dd905c09b0bcc19833198b925f66dea245b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966912"
---
# <a name="project-configuration-object"></a>Oggetto di configurazione del progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'oggetto di configurazione di progetto gestisce la visualizzazione delle informazioni di configurazione per l'interfaccia utente.  
  
 ![Configurazione del progetto di Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Pagine delle proprietà di configurazione di progetto  
  
 Il Provider di configurazione di progetto gestisce le configurazioni di progetto. L'ambiente e altri pacchetti, per accedere e recuperare informazioni sulle configurazioni di un progetto, chiamare le interfacce collegate all'oggetto Provider di configurazione di progetto.  
  
> [!NOTE]
>  È possibile creare o modificare i file di configurazione di soluzione a livello di codice. È necessario usare `DTE.SolutionBuilder`. Visualizzare [configurazione della soluzione](../../extensibility/internals/solution-configuration.md) per altre informazioni.  
  
 Per pubblicare un nome visualizzato da usare nella configurazione dell'interfaccia utente, è necessario implementare il progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, che restituisce un elenco di `IVsCfg` puntatori che è possibile usare per ottenere i nomi visualizzati per le informazioni di configurazione e la piattaforma da elencare nell'interfaccia utente dell'ambiente. La configurazione attiva e la piattaforma dipendono dalla configurazione del progetto nella configurazione soluzione attiva. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> metodo può essere utilizzato per recuperare la configurazione di progetto attivo.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> oggetto facoltativamente può essere implementato nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> dell'oggetto con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> oggetto per consentire di recuperare un `IVsProjectCfg2` oggetto basato sul nome di configurazione del progetto canonico.  
  
 Un altro modo per fornire accesso alle configurazioni di progetto l'ambiente e altri progetti sia per i progetti fornire un'implementazione del `IVsCfgProvider2::GetCfgs` per restituire uno o più oggetti di configurazione. I progetti possono anche implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, che eredita da `IVsProjectCfg` e quindi da `IVsCfg`, per fornire informazioni specifiche della configurazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> supporta le piattaforme e le funzionalità per l'aggiunta, eliminazione e ridenominazione di configurazioni di progetto.  
  
> [!NOTE]
>  Poiché Visual Studio non è più limitato a due tipi di configurazione, il codice che elabora le configurazioni non deve essere scritta con presupposti sul numero di configurazioni, né deve essere scritto partendo dal presupposto che un progetto che ha un unico configurazione è necessariamente Debug o vendita al dettaglio. In questo modo l'utilizzo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleto.  
  
 La chiamata `QueryInterface` sull'oggetto restituito da`IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Se `IVsGetCfgProvider` non viene trovato chiamando `QueryInterface` nel `IVsProject3` oggetto progetto, è possibile accedere all'oggetto provider di configurazione chiamando `QueryInterface` sull'oggetto gerarchia radice browser per l'oggetto restituito per `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, o tramite un puntatore al provider di configurazione restituito per `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` principalmente fornisce l'accesso per compilare, eseguire il debug e distribuzione di oggetti di gestione e consente ai progetti la libertà necessaria per raggruppare gli output. I metodi della `IVsProjectCfg` e `IVsProjectCfg2` può essere utilizzato per implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> per gestire il processo di compilazione e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> puntatori per i gruppi di output di una configurazione.  
  
 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione che supporta anche se il numero degli output contenute all'interno di un gruppo può variare da una configurazione alla configurazione. I gruppi di devono anche avere le stesse informazioni di identificatore (nome canonico, nome visualizzato e le informazioni sui gruppi) dalla configurazione alla configurazione all'interno di un progetto. Per altre informazioni, vedere [configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md).  
  
 Per abilitare il debug, è consigliabile implementare le configurazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` è un'interfaccia opzionale implementata dai progetti per consentire al debugger di avviare una configurazione e viene implementata nell'oggetto di configurazione con `IVsCfg` e `IVsProjectCfg`. L'ambiente viene chiamato quando l'utente decide di avviare il debugger premendo F5.  
  
 `ISpecifyPropertyPages` e `IDispatch` vengono utilizzati in combinazione con le pagine delle proprietà per recuperare e visualizzare all'utente informazioni dipendenti dalla configurazione. Per altre informazioni, vedere [pagine delle proprietà](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md)   
 [Pagine delle proprietà](../../extensibility/internals/property-pages.md)   
 [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)
