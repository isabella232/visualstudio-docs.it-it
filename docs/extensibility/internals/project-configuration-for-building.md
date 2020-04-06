---
title: Configurazione del progetto per la costruzione Documenti Microsoft
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
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706736"
---
# <a name="project-configuration-for-building"></a>Configurazione del progetto per la compilazione
L'elenco delle configurazioni di soluzione per una determinata soluzione è gestito dalla finestra di dialogo Configurazioni soluzione.

 Un utente può creare configurazioni di soluzione aggiuntive, ognuna con il proprio nome univoco. Quando l'utente crea una nuova configurazione di soluzione, l'IDE per impostazione predefinita il nome di configurazione corrispondente nei progetti o Debug se non esiste alcun nome corrispondente. L'utente può modificare la selezione per soddisfare requisiti specifici, se necessario. L'unica eccezione a questo comportamento è quando il progetto supporta una configurazione che corrisponde al nome della nuova configurazione di soluzione. Si supponga, ad esempio, che una soluzione contenga Project1 e Project2. Project1 include configurazioni di progetto Debug, Vendita al dettaglio e MyConfig1. Project2 include configurazioni di progetto Debug, Retail e MyConfig2.

 Se l'utente crea una nuova configurazione di soluzione denominata MyConfig2, Project1 associa la configurazione di Debug alla configurazione della soluzione per impostazione predefinita. Project2 associa anche la configurazione MyConfig2 alla configurazione della soluzione per impostazione predefinita.

> [!NOTE]
> L'associazione non fa distinzione tra maiuscole e minuscole.

 Quando l'utente seleziona l'elemento **Selezione multipla** nell'elenco a discesa di configurazione, nell'ambiente viene visualizzata una finestra di dialogo che fornisce l'elenco delle configurazioni disponibili.

 ![Configurazioni multiple](../../extensibility/internals/media/vsmultiplecfgs.gif "VsMultipleCfgs (informazioni in cui sono stati risbiti") Configurazioni multiple

 All'interno di questa finestra di dialogo, l'utente può selezionare una o più configurazioni. Una volta selezionati, i valori delle proprietà visualizzati nella finestra di dialogo delle pagine delle proprietà riflettono l'intersezione dei valori per le configurazioni selezionate.

 Vedere [Configurazione soluzione](../../extensibility/internals/solution-configuration.md) per informazioni sull'aggiunta e la ridenominazione di configurazioni per soluzioni e progetti.

 Le dipendenze di progetto e l'ordine di compilazione sono indipendenti dalla configurazione della soluzione: è possibile impostare un solo albero delle dipendenze per tutti i progetti nella soluzione. Fare clic con il pulsante destro del mouse sulla soluzione o sul progetto e selezionando l'opzione **Dipendenze progetto** o **Ordine di compilazione progetto** per aprire la finestra di dialogo **Dipendenze progetto.** Può anche essere aperto dal menu **Progetto.**

 ![Dipendenze del progetto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Dipendenze del progetto

 Le dipendenze di progetto determinano l'ordine di compilazione dei progetti. Utilizzare la scheda Ordine di compilazione nella finestra di dialogo per visualizzare l'ordine esatto in cui verranno compilati i progetti all'interno di una soluzione e utilizzare la scheda Dipendenze per modificare l'ordine di compilazione.

> [!NOTE]
> I progetti nell'elenco che hanno le caselle di controllo selezionate ma visualizzate in <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> grigio <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> sono stati aggiunti dall'ambiente a causa di dipendenze esplicite specificate dalle interfacce o e non possono essere modificate. Ad esempio, l'aggiunta [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] di un riferimento al progetto da un progetto a un altro progetto aggiunge automaticamente una dipendenza di compilazione che può essere rimossa solo eliminando il riferimento. I progetti le cui caselle di controllo sono deselezionate e visualizzate in grigio non possono essere selezionate perché in questo modo si creerebbe un ciclo di dipendenze (ad esempio, Project1 dipenderebbe da Project2 e Project2 dipenderebbe da Project1), che blocca la compilazione.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]I processi di compilazione includono le tipiche operazioni di compilazione e collegamento richiamate con un singolo comando Build. Possono essere supportati anche altri due processi di compilazione: un'operazione pulita per eliminare tutti gli elementi di output da una compilazione precedente e un controllo aggiornato per determinare se un elemento di output in una configurazione è stato modificato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>gli oggetti <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> restituiscono un <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>oggetto corrispondente (restituito da ) per gestire i processi di compilazione. Per segnalare lo stato di un'operazione di compilazione mentre si verifica, le configurazioni effettuano chiamate a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, un'interfaccia implementata dall'ambiente e qualsiasi altro oggetto interessato agli eventi di stato di compilazione.

 Una volta compilate, le impostazioni di configurazione possono essere utilizzate per determinare se possono essere eseguite o meno sotto il controllo del debugger. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> configurazioni implementano per supportare il debug.

 Dopo aver implementato le dipendenze del progetto, è possibile modificare le dipendenze a livello di codice tramite il modello di automazione. Chiamare <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> il modello di automazione. Non sono disponibili interfacce a livello di API VSIP che consentono la modifica diretta delle configurazioni del gestore di compilazione della soluzione e delle relative proprietà.

 Inoltre, è possibile fornire una griglia nella finestra delle dipendenze del progetto. Per ulteriori informazioni, vedere [Griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
