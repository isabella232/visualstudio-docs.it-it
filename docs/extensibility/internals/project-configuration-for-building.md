---
title: Project Configurazione per la compilazione | Microsoft Docs
description: Informazioni su come un elenco di configurazioni di soluzione per una determinata soluzione viene gestito dalla finestra di dialogo Configurazioni soluzione in un nuovo tipo di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 07112d61162f4007db1581c75188295e152e809cd733ff6b3220c5ed1ca742b3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401545"
---
# <a name="project-configuration-for-building"></a>Configurazione del progetto per la compilazione
L'elenco delle configurazioni di soluzione per una determinata soluzione viene gestito dalla finestra di dialogo Configurazioni soluzione .

 Un utente può creare configurazioni di soluzione aggiuntive, ognuna con il proprio nome univoco. Quando l'utente crea una nuova configurazione di soluzione, per impostazione predefinita l'IDE viene utilizzato il nome di configurazione corrispondente nei progetti oppure Debug se non esiste alcun nome corrispondente. Se necessario, l'utente può modificare la selezione per soddisfare requisiti specifici. L'unica eccezione a questo comportamento è quando il progetto supporta una configurazione che corrisponde al nome della nuova configurazione della soluzione. Si supponga, ad esempio, che una soluzione contenga Project1 e Project2. Project1 ha configurazioni di progetto Debug, Retail e MyConfig1. Project2 include configurazioni di progetto Debug, Retail e MyConfig2.

 Se l'utente crea una nuova configurazione di soluzione denominata MyConfig2, Project1 associa la configurazione di debug alla configurazione della soluzione per impostazione predefinita. Project2 associa anche la configurazione MyConfig2 alla configurazione della soluzione per impostazione predefinita.

> [!NOTE]
> L'associazione non fa distinzione tra maiuscole e minuscole.

 Quando l'utente seleziona **l'elemento** Selezione multipla nell'elenco a discesa di configurazione, l'ambiente visualizza una finestra di dialogo che fornisce l'elenco delle configurazioni disponibili.

 ![Più configurazioni](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Più configurazioni

 In questa finestra di dialogo l'utente può selezionare una o più configurazioni. Una volta selezionati, i valori delle proprietà visualizzati nella finestra di dialogo pagine delle proprietà riflettono l'intersezione dei valori per le configurazioni selezionate.

 Vedere [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md) per informazioni relative all'aggiunta e alla ridenominazione di configurazioni per soluzioni e progetti.

 Project dipendenze e l'ordine di compilazione sono indipendenti dalla configurazione della soluzione, ad esempio è possibile configurare un solo albero delle dipendenze per tutti i progetti nella soluzione. Facendo clic con il pulsante destro del mouse sulla  soluzione o sul progetto e selezionando l'opzione Project **Dipendenze** o ordine di compilazione Project si apre la finestra di dialogo Project **dipendenze.** Può anche essere aperto dal menu **Project.**

 ![Project dipendenze Project](../../extensibility/internals/media/vsprojdependencies.gif "Dipendenze vsProjDependencies") dipendenze

 Project dipendenze determinano l'ordine di compilazione dei progetti. Usare la scheda Ordine di compilazione nella finestra di dialogo per visualizzare l'ordine esatto in cui verranno compilati i progetti all'interno di una soluzione e usare la scheda Dipendenze per modificare l'ordine di compilazione.

> [!NOTE]
> I progetti nell'elenco con le relative caselle di controllo selezionate ma visualizzate in grigio sono stati aggiunti dall'ambiente a causa di dipendenze esplicite specificate dalle interfacce o e non possono essere <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> modificati. Ad esempio, l'aggiunta di un riferimento al progetto da un progetto a un altro progetto aggiunge automaticamente una dipendenza di compilazione che può essere rimossa solo [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] eliminando il riferimento. I progetti le cui caselle di controllo sono deselezionate e visualizzate in grigio non possono essere selezionati perché in questo modo viene creato un ciclo di dipendenze (ad esempio, Project1 dipende da Project2 e Project2 dipende da Project1), che blocca la compilazione.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] I processi di compilazione includono le tipiche operazioni di compilazione e collegamento che vengono richiamate con un singolo comando di compilazione. Possono essere supportati anche altri due processi di compilazione: un'operazione pulita per eliminare tutti gli elementi di output da una compilazione precedente e un controllo aggiornato per determinare se un elemento di output in una configurazione è stato modificato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Gli oggetti restituiscono un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> oggetto corrispondente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> (restituito da ) per gestire i processi di compilazione. Per segnalare lo stato di un'operazione di compilazione mentre è in corso, le configurazioni effettuano chiamate a , un'interfaccia implementata dall'ambiente e qualsiasi altro oggetto interessato agli eventi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> di stato della compilazione.

 Una volta compilate, le impostazioni di configurazione possono essere usate per determinare se possono essere eseguite o meno sotto il controllo del debugger. Le configurazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> implementano per supportare il debug.

 Dopo aver implementato le dipendenze del progetto, è possibile modificare le dipendenze a livello di codice tramite il modello di automazione. Chiamare nel <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> modello di automazione. Non sono disponibili interfacce a livello di API VSIP che consentono la modifica diretta delle configurazioni di Gestione compilazione soluzioni e delle relative proprietà.

 È anche possibile specificare una griglia nella finestra delle dipendenze del progetto. Per altre informazioni, vedere [Griglia di visualizzazione delle proprietà.](../../extensibility/internals/properties-display-grid.md)

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
