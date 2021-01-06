---
title: Configurazione del progetto per la compilazione | Microsoft Docs
description: Informazioni su come un elenco di configurazioni della soluzione per una particolare soluzione viene gestito dalla finestra di dialogo Configurazioni soluzione in un nuovo tipo di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7768de1b57142e201c4108f5ef0c0768c57a8639
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878001"
---
# <a name="project-configuration-for-building"></a>Configurazione del progetto per la compilazione
L'elenco delle configurazioni della soluzione per una determinata soluzione è gestito dalla finestra di dialogo Configurazioni soluzione.

 Un utente può creare configurazioni di soluzione aggiuntive, ciascuna con il proprio nome univoco. Quando l'utente crea una nuova configurazione di soluzione, per impostazione predefinita l'IDE è il nome della configurazione corrispondente nei progetti oppure esegue il debug se non esiste alcun nome corrispondente. Se necessario, l'utente può modificare la selezione per soddisfare requisiti specifici. L'unica eccezione a questo comportamento è quando il progetto supporta una configurazione che corrisponde al nome della nuova configurazione della soluzione. Si supponga, ad esempio, che una soluzione includa Project1 e Progetto2. Project1 dispone di configurazioni di progetto debug, retail e MyConfig1. Progetto2 dispone di configurazioni di progetto debug, retail e MyConfig2.

 Se l'utente crea una nuova configurazione di soluzione denominata MyConfig2, Project1 associa la configurazione di debug alla configurazione della soluzione per impostazione predefinita. Per impostazione predefinita, Progetto2 associa anche la configurazione di MyConfig2 alla configurazione della soluzione.

> [!NOTE]
> Il binding non fa distinzione tra maiuscole e minuscole.

 Quando l'utente seleziona l'elemento **selezione multipla** nell'elenco a discesa configurazione, nell'ambiente viene visualizzata una finestra di dialogo che fornisce l'elenco delle configurazioni disponibili.

 ![Configurazioni multiple](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Configurazioni multiple

 All'interno di questa finestra di dialogo, l'utente può selezionare una o più configurazioni. Una volta selezionata, i valori delle proprietà visualizzati nella finestra di dialogo Pagine delle proprietà riflettono l'intersezione dei valori per le configurazioni selezionate.

 Per informazioni relative all'aggiunta e alla ridenominazione di configurazioni per soluzioni e progetti, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md) .

 Le dipendenze del progetto e l'ordine di compilazione sono indipendenti dalla configurazione della soluzione, ovvero è possibile configurare un solo albero delle dipendenze per tutti i progetti nella soluzione. Facendo clic con il pulsante destro del mouse sulla soluzione o sul progetto e selezionando l'opzione **Dipendenze progetto** o **ordine di compilazione progetto** verrà visualizzata la finestra di dialogo **dipendenze** progetto. Può anche essere aperto dal menu **progetto** .

 ![Dipendenze progetto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Dipendenze progetto

 Le dipendenze del progetto determinano l'ordine di compilazione dei progetti. Utilizzare la scheda ordine di compilazione della finestra di dialogo per visualizzare l'ordine esatto in cui i progetti in una soluzione vengono compilati e utilizzare la scheda dipendenze per modificare l'ordine di compilazione.

> [!NOTE]
> I progetti nell'elenco con le relative caselle di controllo selezionate ma visualizzati in grigio sono stati aggiunti dall'ambiente a causa di dipendenze esplicite specificate dalle <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfacce o e non possono essere modificate. Ad esempio, l'aggiunta di un riferimento al progetto da un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto a un altro progetto aggiunge automaticamente una dipendenza di compilazione che può essere rimossa solo eliminando il riferimento. I progetti le cui caselle di controllo sono chiare e visualizzate in grigio non possono essere selezionati perché in questo modo si creerebbe un ciclo di dipendenze (ad esempio, Project1 dipendono da Progetto2 e Progetto2 dipendono da Project1) che blocca la compilazione.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i processi di compilazione includono le tipiche operazioni di compilazione e collegamento richiamate con un singolo comando di compilazione. È anche possibile supportare altri due processi di compilazione: un'operazione di pulizia per eliminare tutti gli elementi di output da una compilazione precedente e un controllo di aggiornamento per determinare se un elemento di output in una configurazione è stato modificato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> gli oggetti restituiscono un oggetto corrispondente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (restituito da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ) per gestire i processi di compilazione. Per segnalare lo stato di un'operazione di compilazione mentre è in corso, le configurazioni effettuano chiamate a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> , un'interfaccia implementata dall'ambiente e qualsiasi altro oggetto interessato dagli eventi dello stato di compilazione.

 Una volta compilate, è possibile usare le impostazioni di configurazione per determinare se possono essere eseguite o meno sotto il controllo del debugger. Le configurazioni implementano <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> per supportare il debug.

 Una volta implementate le dipendenze del progetto, è possibile modificare a livello di codice le dipendenze tramite il modello di automazione. Viene chiamato <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> nel modello di automazione. Non sono disponibili interfacce a livello API VSIP che consentono la manipolazione diretta delle configurazioni del gestore di compilazione della soluzione e delle rispettive proprietà.

 Inoltre, è possibile specificare una griglia nella finestra Dipendenze progetto. Per altre informazioni, vedere [griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
