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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698692"
---
# <a name="upgrading-project-items"></a>Aggiornamento degli elementi di progetto
Se si aggiungono o gestire gli elementi all'interno di sistemi di progetto non viene implementato, devi partecipare al processo di aggiornamento del progetto. Crystal Reports è un esempio di un elemento che è possibile aggiungere al sistema del progetto.  
  
 In genere, gli implementatori di elemento di progetto vuole sfruttare un progetto già completamente un'istanza e l'aggiornamento perché è necessario conoscere il progetto sono riferimenti e quali altre proprietà del progetto sono presenti per prendere una decisione di aggiornamento.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Per ricevere le notifiche di aggiornamento progetto  
  
1. Impostare il <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flag (definito in vsshell80.idl) nell'implementazione dell'elemento di progetto. In questo modo l'elemento di progetto VSPackage su auto caricamento quando il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell determina che un sistema di progetto è in corso l'aggiornamento.  
  
2. Consigliare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> (metodo).  
  
3. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia viene generata dopo che l'implementazione di sistema di progetto completamento delle operazioni di aggiornamento e viene creato il nuovo progetto aggiornato. A seconda dello scenario, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia viene attivata dopo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metodi.  
  
### <a name="to-upgrade-the-project-item-files"></a>Per aggiornare i file di elemento di progetto  
  
1. È necessario gestire attentamente il processo di backup di file nell'implementazione dell'elemento di progetto. Questo vale in particolare per il backup side-by-side, in cui il `fUpgradeFlag` parametro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo è impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, in cui vengono inseriti i file che erano stato eseguito il backup insieme file lato designati come "old". I file di backup meno recenti rispetto all'ora di sistema quando il progetto è stato aggiornato possono essere designati come obsoleti. Inoltre, potrebbe essere sovrascritto a meno che non si accettano i passaggi dettagliati per evitare questo problema.  
  
2. Al momento l'elemento di progetto riceve una notifica di aggiornamento del progetto, il **conversione guidata di Visual Studio** continuerà a essere visualizzato. Pertanto, è necessario utilizzare i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfaccia per fornire messaggi di aggiornamento per la procedura guidata dell'interfaccia utente.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Conversion Wizard](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Aggiornamento di progetti personalizzati](../misc/upgrading-custom-projects.md)