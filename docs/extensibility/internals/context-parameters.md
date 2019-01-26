---
title: I parametri di contesto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1290fe9aa9b8fc017856d776aa718ff3d1810df1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931674"
---
# <a name="context-parameters"></a>Parametri di contesto
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE), è possibile aggiungere le procedure guidate per il **nuovo progetto**, **Aggiungi nuovo elemento**, o **Aggiungi progetto Sub** finestre di dialogo. Le procedure guidate di aggiunta sono disponibili nel **File** dal menu o facendo clic su un progetto in **Esplora soluzioni**. L'IDE passa i parametri di contesto per l'implementazione della procedura guidata. I parametri di contesto definiscono lo stato del progetto quando l'IDE chiama la procedura guidata.  
  
 Procedure guidate di avvio dell'IDE, impostando il <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag nella chiamata dell'IDE per la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodo per il progetto. Se impostato, il progetto deve rendere la `IVsExtensibility::RunWizardFile` metodo da eseguire usando il nome della procedura guidata registrati o GUID e altri parametri di contesto che l'IDE passa a esso.  
  
## <a name="context-parameters-for-new-project"></a>Parametri di contesto per il nuovo progetto  
  
| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Creazione guidata tipo di registrazione (<xref:EnvDTE.Constants.vsWizardNewProject>) o il GUID che indica il tipo di procedura guidata. Nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione, il GUID per la procedura guidata è {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta l'oggetto univoco [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome del progetto. |
| `LocalDirectory` | Percorso locale di utilizzo file di progetto. |
| `InstallationDirectory` | Percorso della directory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è l'installazione. |
| `FExclusive` | Flag booleano che indica che il progetto deve chiudersi soluzioni aperte. |
| `SolutionName` | Nome del file della soluzione senza la parte di directory o la *sln* estensione. Il *suo* nome del file viene creato anche usando `SolutionName`. Quando questo argomento non è una stringa vuota, la procedura guidata Usa <xref:EnvDTE._Solution.Create%2A> prima di aggiungere il progetto con <xref:EnvDTE._Solution.AddFromTemplate%2A>. Se questo nome è una stringa vuota, utilizzare <xref:EnvDTE._Solution.AddFromTemplate%2A> senza chiamare <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguito automaticamente come se **Finish** visitati (`TRUE`). |
  
## <a name="context-parameters-for-add-new-item"></a>Parametri di contesto per Aggiungi nuovo elemento  
  
| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Creazione guidata tipo di registrazione (<xref:EnvDTE.Constants.vsWizardAddItem>) o il GUID che indica il tipo di procedura guidata. Nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione, il GUID per la procedura guidata è {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta l'oggetto univoco [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome del progetto. |
| `ProjectItems` | Percorso locale che contiene i file di progetto di lavoro. |
| `ItemName` | Nome dell'elemento che deve essere aggiunto. Questo nome è il nome file predefinito o il nome del file che l'utente digita dal **Aggiungi elementi** nella finestra di dialogo. Il nome è basato sui flag impostati nella *VSDIR* file. Il nome può essere un valore null. |
| `InstallationDirectory` | Percorso della directory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è l'installazione. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguito automaticamente come se **Finish** visitati (`TRUE`). |
  
## <a name="context-parameters-for-add-sub-project"></a>Parametri di contesto per aggiungere progetti Sub  
  
| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Creazione guidata tipo di registrazione (<xref:EnvDTE.Constants.vsWizardAddSubProject>) o il GUID che indica il tipo di procedura guidata. Nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione, il GUID per la procedura guidata è {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta l'oggetto univoco [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome del progetto. |
| `ProjectItems` | Puntatore al `ProjectItems` raccolta su cui opera la procedura guidata. Puntatore ' this ' viene passato alla procedura guidata in base alla selezione di gerarchia del progetto. Un utente seleziona in genere una cartella in cui inserire l'elemento e quindi chiama il progetto **Aggiungi elemento** nella finestra di dialogo. |
| `LocalDirectory` | Percorso locale di utilizzo file di progetto. |
| `ItemName` | Nome dell'elemento che deve essere aggiunto. Questo nome è il nome file predefinito o il nome del file che l'utente digita dal **Aggiungi elementi** nella finestra di dialogo. Il nome è basato sui flag impostati nella *VSDIR* file. Il nome può essere un valore null. |
| `InstallationDirectory` | Percorso della directory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installazione. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguito automaticamente come se **Finish** visitati (`TRUE`). |
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parametri di contesto per l'avvio di procedure guidate](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)