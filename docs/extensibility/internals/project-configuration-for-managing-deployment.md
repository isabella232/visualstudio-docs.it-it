---
title: Project Configurazione per la gestione della distribuzione | Microsoft Docs
description: Informazioni sulla distribuzione nel percorso previsto per il debug e l'installazione e sui due modi Visual Studio i progetti che supportano la distribuzione.
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
ms.openlocfilehash: fdd15349522c1bf49f379551825a773b676f6196
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094646"
---
# <a name="project-configuration-for-managing-deployment"></a>Configurazione del progetto per la gestione della distribuzione
La distribuzione è l'atto di spostare fisicamente gli elementi di output da un processo di compilazione al percorso previsto per il debug e l'installazione. Ad esempio, un'applicazione Web potrebbe essere compilata in un computer locale e quindi inserita nel server.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due modi in cui i progetti possono essere coinvolti nella distribuzione:

- Come oggetto del processo di distribuzione.

- Come responsabile del processo di distribuzione.

  Prima di poter distribuire le soluzioni, è necessario aggiungere un progetto di distribuzione per configurare le opzioni di distribuzione. Se il progetto di distribuzione non esiste già, viene chiesto  se si vuole crearne uno quando si sceglie Distribuisci soluzione dal **menu** Compila o si fa clic con il pulsante destro del mouse sulla soluzione. Facendo **clic su Sì** si apre la finestra di dialogo Aggiungi nuovo **Project** con il progetto Distribuzione **guidata** remota selezionato.

  La Distribuzione guidata remota richiede il tipo di applicazione (Windows o Web), i gruppi di output del progetto da includere, eventuali file aggiuntivi da includere e il computer remoto in cui si vuole eseguire la distribuzione. Nell'ultima pagina della procedura guidata viene visualizzato un riepilogo delle opzioni selezionate.

  I progetti oggetto di un processo di distribuzione producono elementi di output che devono essere spostati in un ambiente alternativo. Questi elementi di output vengono descritti come parametri per l'interfaccia , il cui scopo principale è consentire <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> ai progetti di raggruppare gli output. Per altre informazioni sull'implementazione di , vedere `IVsProjectCfg2` Project Configuration for [Output](../../extensibility/internals/project-configuration-for-output.md).

  I progetti di distribuzione, che gestiscono il processo di distribuzione, abilitano il comando Distribuisci e rispondono quando questo comando è selezionato. I progetti di distribuzione <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> implementano l'interfaccia per eseguire la distribuzione ed effettuare chiamate <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> all'interfaccia per segnalare gli eventi di stato della distribuzione.

  Le configurazioni possono specificare dipendenze che influiscono sulle operazioni di compilazione o distribuzione. Le dipendenze di compilazione o distribuzione sono progetti che devono essere compilati o distribuiti prima o dopo la compilazione o la distribuzione delle configurazioni stesse. Le dipendenze di compilazione tra i progetti sono descritte con <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> l'interfaccia e distribuiscono le dipendenze con l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> . Per altre informazioni, vedere Configurazione [Project per la compilazione](../../extensibility/internals/project-configuration-for-building.md)di .

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
