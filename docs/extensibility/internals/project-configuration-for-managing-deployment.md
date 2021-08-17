---
title: Project Configurazione per la gestione delle risorse di | Microsoft Docs
description: Informazioni sulla distribuzione nel percorso previsto per il debug e l'installazione e sui due modi Visual Studio supportano i progetti che supportano la distribuzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: aa66bd9e4760c060082c07d72a90f853bf47dbda3604016b8786fb105fbaac4d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375701"
---
# <a name="project-configuration-for-managing-deployment"></a>Configurazione del progetto per la gestione della distribuzione
La distribuzione è l'azione di spostare fisicamente gli elementi di output da un processo di compilazione al percorso previsto per il debug e l'installazione. Ad esempio, un'applicazione Web potrebbe essere compilata in un computer locale e quindi inserita nel server.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due modi in cui i progetti possono essere coinvolti nella distribuzione:

- Come oggetto del processo di distribuzione.

- Come responsabile del processo di distribuzione.

  Prima di distribuire le soluzioni, è necessario aggiungere un progetto di distribuzione per configurare le opzioni di distribuzione. Se il progetto di distribuzione non esiste già, viene chiesto  se si vuole crearne uno quando si sceglie Distribuisci soluzione dal **menu** Compila o si fa clic con il pulsante destro del mouse sulla soluzione. Se **si fa** clic su **Sì, viene visualizzata Project** finestra di dialogo Aggiungi nuovo progetto con il progetto **distribuzione** guidata remoto selezionato.

  La Distribuzione guidata remota richiede il tipo di applicazione (Windows o Web), i gruppi di output del progetto da includere, eventuali file aggiuntivi da includere e il computer remoto in cui si vuole eseguire la distribuzione. Nell'ultima pagina della procedura guidata viene visualizzato un riepilogo delle opzioni selezionate.

  I progetti oggetto di un processo di distribuzione producono elementi di output che devono essere spostati in un ambiente alternativo. Questi elementi di output vengono descritti come parametri per l'interfaccia , il cui <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> scopo principale è consentire ai progetti di raggruppare gli output. Per altre informazioni relative all'implementazione di `IVsProjectCfg2` , vedere Project Configuration for [Output.](../../extensibility/internals/project-configuration-for-output.md)

  I progetti di distribuzione, che gestiscono il processo di distribuzione, abilitano il comando Distribuisci e rispondono quando questo comando è selezionato. I progetti di distribuzione <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> implementano l'interfaccia per eseguire la distribuzione ed effettuare chiamate <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> all'interfaccia per segnalare gli eventi di stato della distribuzione.

  Le configurazioni possono specificare dipendenze che influiscono sulle operazioni di compilazione o distribuzione. Le dipendenze di compilazione o distribuzione sono progetti che devono essere compilati o distribuiti prima o dopo la compilazione o la distribuzione delle configurazioni stesse. Le dipendenze di compilazione tra progetti vengono descritte con <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> l'interfaccia e distribuiscono le dipendenze con <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> l'interfaccia . Per altre informazioni, vedere [Project Configuration for Building](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
