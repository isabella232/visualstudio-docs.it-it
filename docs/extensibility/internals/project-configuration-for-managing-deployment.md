---
title: Configurazione del progetto per la gestione della distribuzione Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706705"
---
# <a name="project-configuration-for-managing-deployment"></a>Configurazione del progetto per la gestione della distribuzione
La distribuzione è l'atto di spostare fisicamente gli elementi di output da un processo di compilazione nel percorso previsto per il debug e l'installazione. Ad esempio, un'applicazione Web potrebbe essere compilata in un computer locale e quindi inserita nel server.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta due modi in cui i progetti possono essere coinvolti nella distribuzione:

- Come oggetto del processo di distribuzione.

- In qualità di responsabile del processo di distribuzione.

  Prima di poter distribuire le soluzioni, è necessario aggiungere un progetto di distribuzione per configurare le opzioni di distribuzione. Se il progetto di distribuzione non esiste già, viene chiesto se si desidera crearne uno quando si seleziona **Distribuisci soluzione** dal menu **Compila** o si fa clic con il pulsante destro del mouse sulla soluzione. Facendo clic su **Sì** si apre la finestra di dialogo **Aggiungi nuovo progetto** con il progetto Distribuzione guidata **remota** selezionato.

  La Distribuzione guidata remota richiede il tipo di applicazione (Windows o Web), i gruppi di output del progetto da includere, gli eventuali file aggiuntivi che si desidera includere e il computer remoto in cui si desidera eseguire la distribuzione. Nell'ultima pagina della procedura guidata viene visualizzato un riepilogo delle opzioni selezionate.

  I progetti oggetto di un processo di distribuzione producono elementi di output che devono essere spostati in un ambiente alternativo. Questi elementi di output vengono <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> descritti come parametri per l'interfaccia, il cui scopo principale se consentire ai progetti di raggruppare gli output. Per ulteriori informazioni sull'implementazione di , vedere Configurazione `IVsProjectCfg2` [del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md).

  I progetti di distribuzione, che gestiscono il processo di distribuzione, abilitano il comando Distribuisci e rispondono quando questo comando è selezionato. I progetti <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> di distribuzione implementano l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> per eseguire la distribuzione ed effettuare chiamate all'interfaccia per segnalare gli eventi di stato di distribuzione.

  Le configurazioni possono specificare dipendenze che influiscono sulle operazioni di compilazione o distribuzione. Le dipendenze di compilazione o distribuzione sono progetti che devono essere compilati o distribuiti prima o dopo la compilazione o la distribuzione delle configurazioni stesse. Le dipendenze di compilazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> tra progetti vengono <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> descritte con l'interfaccia e distribuiscono le dipendenze con l'interfaccia . Per ulteriori informazioni, vedere Configurazione del progetto per la [compilazione](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
