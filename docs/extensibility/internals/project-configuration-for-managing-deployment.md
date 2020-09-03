---
title: Configurazione del progetto per la gestione della distribuzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706705"
---
# <a name="project-configuration-for-managing-deployment"></a>Configurazione del progetto per la gestione della distribuzione
La distribuzione è l'azione di spostamento fisico degli elementi di output da un processo di compilazione al percorso previsto per il debug e l'installazione. Ad esempio, un'applicazione Web può essere compilata in un computer locale e quindi posizionata sul server.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due modalità di partecipazione ai progetti nella distribuzione:

- Come soggetto del processo di distribuzione.

- Come responsabile del processo di distribuzione.

  Prima di distribuire le soluzioni, è innanzitutto necessario aggiungere un progetto di distribuzione per configurare le opzioni di distribuzione. Se il progetto di distribuzione non esiste già, viene chiesto se si vuole crearne uno quando si seleziona **Distribuisci soluzione** dal menu **Compila** o si fa clic con il pulsante destro del mouse sulla soluzione. Se **si** fa clic su Sì, viene visualizzata la finestra di dialogo **Aggiungi nuovo progetto** con il progetto di **distribuzione guidata remoto** selezionato.

  La procedura guidata di distribuzione remota richiede il tipo di applicazione (Windows o Web), i gruppi di output del progetto da includere, i file aggiuntivi che si desidera includere e il computer remoto in cui si desidera eseguire la distribuzione. Nell'ultima pagina della procedura guidata viene visualizzato un riepilogo delle opzioni selezionate.

  I progetti che sono soggetti a un processo di distribuzione producono elementi di output che devono essere spostati in un ambiente alternativo. Questi elementi di output vengono descritti come parametri per l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfaccia, il cui scopo principale è quello di consentire ai progetti di raggruppare gli output. Per altre informazioni relative all'implementazione di `IVsProjectCfg2` , vedere [configurazione di progetto per l'output](../../extensibility/internals/project-configuration-for-output.md).

  I progetti di distribuzione, che gestiscono il processo di distribuzione, abilitano il comando Distribuisci e rispondono quando si seleziona questo comando. I progetti di distribuzione implementano l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia per eseguire la distribuzione ed effettuare chiamate all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfaccia per segnalare gli eventi di stato di distribuzione.

  Le configurazioni possono specificare dipendenze che influiscono sulle operazioni di compilazione o di distribuzione. Le dipendenze di compilazione o distribuzione sono progetti che devono essere compilati o distribuiti prima o dopo la compilazione o la distribuzione delle configurazioni stesse. Le dipendenze di compilazione tra i progetti sono descritte con l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfaccia e distribuiscono le dipendenze con l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaccia. Per ulteriori informazioni, vedere [configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
