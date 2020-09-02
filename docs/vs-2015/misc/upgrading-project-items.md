---
title: Aggiornamento degli elementi di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698692"
---
# <a name="upgrading-project-items"></a>Aggiornamento degli elementi di progetto
Se si aggiungono o gestiscono elementi all'interno di sistemi di progetto non implementati, potrebbe essere necessario partecipare al processo di aggiornamento del progetto. Crystal Reports è un esempio di elemento che può essere aggiunto al sistema del progetto.  
  
 In genere, gli implementatori di elementi di progetto vogliono sfruttare un progetto già completamente creato e aggiornato, perché devono conoscere quali sono i riferimenti al progetto e quali altre proprietà del progetto sono disponibili per prendere una decisione di aggiornamento.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Per ottenere la notifica di aggiornamento del progetto  
  
1. Impostare il <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flag (definito in vsshell80. idl) nell'implementazione dell'elemento del progetto. In questo modo, il pacchetto VSPackage dell'elemento del progetto viene caricato automaticamente quando la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shell determina che è in corso l'aggiornamento di un sistema di progetto.  
  
2. Consigliare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metodo.  
  
3. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia viene attivata dopo che l'implementazione del sistema del progetto ha completato le operazioni di aggiornamento e viene creato il nuovo progetto aggiornato. A seconda dello scenario, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia viene attivata dopo i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodi, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .  
  
### <a name="to-upgrade-the-project-item-files"></a>Per aggiornare i file degli elementi del progetto  
  
1. È necessario gestire con attenzione il processo di backup dei file nell'implementazione dell'elemento del progetto. Questo vale in particolare per un backup affiancato, in cui il `fUpgradeFlag` parametro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo è impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , in cui i file di cui è stato eseguito il backup vengono posizionati lungo i file laterali designati come ". old". I file di cui è stato eseguito il backup anteriori all'ora di sistema in cui è stato aggiornato il progetto possono essere designati come obsoleti. Inoltre, potrebbero essere sovrascritti a meno che non si intraprendano passaggi specifici per evitare questo problema.  
  
2. Quando l'elemento del progetto riceve una notifica dell'aggiornamento del progetto, viene ancora visualizzata la **conversione guidata di Visual Studio** . Pertanto, è necessario utilizzare i metodi dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfaccia per fornire messaggi di aggiornamento all'interfaccia utente della procedura guidata.  
  
## <a name="see-also"></a>Vedere anche  
 [Conversione guidata di Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Aggiornamento di progetti personalizzati](../misc/upgrading-custom-projects.md)