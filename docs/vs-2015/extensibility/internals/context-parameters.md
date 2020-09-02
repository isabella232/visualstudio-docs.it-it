---
title: Parametri di contesto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 679bf567d2f44564d31d70b62c8663e665e1ea65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697279"
---
# <a name="context-parameters"></a>Parametri di contesto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE), è possibile aggiungere le procedure guidate alle finestre di dialogo **nuovo progetto**, **Aggiungi nuovo elemento**o **Aggiungi progetto secondario** . Le procedure guidate aggiunte sono disponibili nel menu **file** o facendo clic con il pulsante destro del mouse su un progetto in **Esplora soluzioni**. L'IDE passa i parametri di contesto all'implementazione della procedura guidata. I parametri di contesto definiscono lo stato del progetto quando l'IDE chiama la procedura guidata.  
  
 L'IDE avvia le procedure guidate impostando il <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag nella chiamata dell'IDE al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodo per il progetto. Se impostata, il progetto deve causare l' `IVsExtensibility::RunWizardFile` esecuzione del metodo usando il nome o il GUID della procedura guidata registrata e altri parametri di contesto che l'IDE passa a tale metodo.  
  
## <a name="context-parameters-for-new-project"></a>Parametri di contesto per il nuovo progetto  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WizardType`|Tipo di procedura guidata registrato ( <xref:EnvDTE.Constants.vsWizardNewProject> ) o GUID che indica il tipo di procedura guidata. Nell' [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implementazione il GUID della procedura guidata è {0F90E1D0-4999-11D1-b6d1-00A0C90F2744}.|  
|`ProjectName`|Stringa che rappresenta il nome univoco del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto.|  
|`LocalDirectory`|Percorso locale dei file di progetto in esecuzione.|  
|`InstallationDirectory`|Il percorso della directory del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è installazione.|  
|`FExclusive`|Flag booleano che indica che il progetto deve chiudere le soluzioni aperte.|  
|`SolutionName`|Nome del file di soluzione senza la parte della directory o estensione sln. Il nome del file con estensione suo viene creato anche usando `SolutionName` . Quando questo argomento non è una stringa vuota, la procedura guidata USA <xref:EnvDTE._Solution.Create%2A> prima di aggiungere il progetto con <xref:EnvDTE._Solution.AddFromTemplate%2A> . Se il nome è una stringa vuota, usare <xref:EnvDTE._Solution.AddFromTemplate%2A> senza chiamare <xref:EnvDTE._Solution.Create%2A> .|  
|`Silent`|Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** ( `TRUE` ).|  
  
## <a name="context-parameters-for-add-new-item"></a>Parametri di contesto per Aggiungi nuovo elemento  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WizardType`|Tipo di procedura guidata registrato ( <xref:EnvDTE.Constants.vsWizardAddItem> ) o GUID che indica il tipo di procedura guidata. Nell' [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implementazione il GUID della procedura guidata è {0F90E1D1-4999-11D1-b6d1-00A0C90F2744}.|  
|`ProjectName`|Stringa che rappresenta il nome univoco del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto.|  
|`ProjectItems`|Percorso locale che contiene i file del progetto funzionante.|  
|`ItemName`|Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome del file che l'utente digita dalla finestra di dialogo **Aggiungi elementi** . Il nome è basato sui flag impostati nel file con estensione VSDIR. Il nome può essere un valore null.|  
|`InstallationDirectory`|Il percorso della directory del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è installazione.|  
|`Silent`|Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** ( `TRUE` ).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Parametri di contesto per Aggiungi progetto secondario  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WizardType`|Tipo di procedura guidata registrato ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) o GUID che indica il tipo di procedura guidata. Nell' [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implementazione il GUID della procedura guidata è {0F90E1D2-4999-11D1-b6d1-00A0C90F2744}.|  
|`ProjectName`|Stringa che rappresenta il nome univoco del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto.|  
|`ProjectItems`|Puntatore alla `ProjectItems` raccolta in cui opera la procedura guidata. Questo puntatore viene passato alla procedura guidata in base alla selezione della gerarchia del progetto. Un utente in genere seleziona una cartella in cui inserire l'elemento e quindi chiama la finestra di dialogo **Aggiungi elemento** del progetto.|  
|`LocalDirectory`|Percorso locale dei file di progetto in esecuzione.|  
|`ItemName`|Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome del file che l'utente digita dalla finestra di dialogo **Aggiungi elementi** . Il nome è basato sui flag impostati nel file con estensione VSDIR. Il nome può essere un valore null.|  
|`InstallationDirectory`|Il percorso della directory del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è installazione.|  
|`Silent`|Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** ( `TRUE` ).|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [Procedura guidata (. File vsz](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parametri di contesto per l'avvio delle procedure guidate](https://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)
