---
title: Configurazione del progetto per gestire la distribuzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5b16c3392e9432ba540130d45f6907de15b51ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969010"
---
# <a name="project-configuration-for-managing-deployment"></a>Configurazione del progetto per la gestione della distribuzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La distribuzione è l'atto di spostano fisicamente gli elementi di output da un processo di compilazione nella posizione prevista per il debug e l'installazione. Ad esempio, un'applicazione Web potrebbe essere compilata in un computer locale e quindi inserita nel server.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta due metodi che proietta può essere coinvolto nella distribuzione:  
  
- L'oggetto del processo di distribuzione.  
  
- Come la gestione del processo di distribuzione.  
  
  Prima di poter distribuire soluzioni, è necessario aggiungere innanzitutto un progetto di distribuzione per configurare le opzioni di distribuzione. Se il progetto di distribuzione non esiste già, viene chiesto se si vuole crearne uno quando si seleziona **Distribuisci soluzione** dalle **compilazione** menu o la scelta della soluzione. Facendo clic su **Yes** apre il **Aggiungi nuovo progetto** finestra di dialogo con il **remoto distribuzione guidata del** progetto selezionato.  
  
  Distribuzione remota guidata viene richiesto per il tipo di applicazione (Windows o Web), i gruppi di output del progetto da includere, eventuali file aggiuntivi da includere e si desidera distribuire in computer remoto. L'ultima pagina della procedura guidata visualizza un riepilogo delle opzioni selezionate.  
  
  I progetti che sono oggetto di un processo di distribuzione producono gli elementi di output che devono essere spostati in un ambiente alternativo. Questi output vengono descritti gli elementi come parametri per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfaccia, il cui primaria allo scopo se consentire o meno i progetti di raggruppare gli output. Per altre informazioni sull'implementazione di `IVsProjectCfg2`, vedere [configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md).  
  
  Progetti di distribuzione, che gestiscono il processo di distribuzione, abilitare il comando Distribuisci e rispondono quando si seleziona questo comando. Implementano progetti di distribuzione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia per eseguire la distribuzione e di effettuare chiamate al <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> eventi dello stato di distribuzione di interfaccia al report.  
  
  Le configurazioni è possono specificare le dipendenze che interessano le relative operazioni di compilazione o distribuzione. Compilare o distribuire le dipendenze sono progetti che devono essere compilati o distribuiti prima o dopo le configurazioni vengono compilate o distribuite. Vengono descritte le dipendenze di compilazione tra i progetti con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> l'interfaccia e distribuire le dipendenze con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaccia. Per altre informazioni, vedere [configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)
