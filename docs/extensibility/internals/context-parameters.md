---
title: Parametri di contesto | Microsoft Docs
description: Informazioni sui parametri di contesto nell Visual Studio ide (Integrated Development Environment) che definiscono lo stato di un progetto quando si aggiunge o implementa una procedura guidata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9b26006a7e178e5449825bb422be35ea2d83a392
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070143"
---
# <a name="context-parameters"></a>Parametri di contesto
Nell'ambiente di sviluppo integrato (IDE) è possibile aggiungere procedure guidate alle finestre di dialogo Nuovo Project , Aggiungi nuovo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **elementoo Aggiungi Project** secondario .  Le procedure guidate aggiunte sono disponibili nel menu **File** o facendo clic con il pulsante destro del mouse su un progetto in **Esplora soluzioni**. L'IDE passa i parametri di contesto all'implementazione della procedura guidata. I parametri di contesto definiscono lo stato del progetto quando l'IDE chiama la procedura guidata.

 L'IDE avvia le procedure guidate impostando il flag nella <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> chiamata dell'IDE al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodo per il progetto. Se impostato, il progetto deve fare in modo che il metodo sia eseguito usando il nome o il GUID della procedura guidata registrata e altri parametri di contesto passati `IVsExtensibility::RunWizardFile` dall'IDE.

## <a name="context-parameters-for-new-project"></a>Parametri di contesto per il nuovo progetto

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrata ( <xref:EnvDTE.Constants.vsWizardNewProject> ) o GUID che indica il tipo di procedura guidata. Nell'implementazione il GUID per la procedura guidata [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] univoco del progetto. |
| `LocalDirectory` | Percorso locale dei file di progetto di lavoro. |
| `InstallationDirectory` | Il percorso di directory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è l'installazione di . |
| `FExclusive` | Flag booleano che indica che il progetto deve chiudere le soluzioni aperte. |
| `SolutionName` | Nome del file della soluzione senza la parte della directory o *l'estensione sln.* Anche *il nome* del file con estensione suo viene creato usando `SolutionName` . Quando questo argomento non è una stringa vuota, la procedura guidata usa <xref:EnvDTE._Solution.Create%2A> prima di aggiungere il progetto con <xref:EnvDTE._Solution.AddFromTemplate%2A> . Se questo nome è una stringa vuota, usare <xref:EnvDTE._Solution.AddFromTemplate%2A> senza chiamare <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se **fosse stato fatto** clic su Fine ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Parametri di contesto per Aggiungi nuovo elemento

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrata ( <xref:EnvDTE.Constants.vsWizardAddItem> ) o GUID che indica il tipo di procedura guidata. Nell'implementazione il GUID per la procedura guidata [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] univoco del progetto. |
| `ProjectItems` | Percorso locale che contiene i file di progetto di lavoro. |
| `ItemName` | Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome del file che l'utente digitare nella **finestra di dialogo** Aggiungi elementi . Il nome è basato sui flag impostati nel file *con estensione vsdir.* Il nome può essere un valore Null. |
| `InstallationDirectory` | Il percorso di directory di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è l'installazione di . |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se **fosse stato fatto** clic su Fine ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Parametri di contesto per Add Sub Project

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrata ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) o GUID che indica il tipo di procedura guidata. Nell'implementazione il GUID per la procedura guidata [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] univoco del progetto. |
| `ProjectItems` | Puntatore alla `ProjectItems` raccolta sulla quale opera la procedura guidata. Questo puntatore viene passato alla procedura guidata in base alla selezione della gerarchia del progetto. Un utente seleziona in genere una cartella in cui inserire l'elemento e quindi chiama la finestra di dialogo Aggiungi **elemento** del progetto. |
| `LocalDirectory` | Percorso locale dei file di progetto di lavoro. |
| `ItemName` | Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome del file che l'utente digitare nella **finestra di dialogo** Aggiungi elementi . Il nome è basato sui flag impostati nel file *con estensione vsdir.* Il nome può essere un valore Null. |
| `InstallationDirectory` | Percorso della directory [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'installazione. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se **fosse stato fatto** clic su Fine ( `TRUE` ). |

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametri di contesto per l'avvio delle procedure guidate](/previous-versions/tz690efs(v=vs.140))