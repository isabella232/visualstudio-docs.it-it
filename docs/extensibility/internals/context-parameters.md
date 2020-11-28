---
title: Parametri di contesto | Microsoft Docs
description: Informazioni sui parametri di contesto nel Integrated Development Environment di Visual Studio (IDE) che definiscono lo stato di un progetto quando si aggiunge o si implementa una procedura guidata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 654ebf68efebaa44766079c172e87396134805e3
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304713"
---
# <a name="context-parameters"></a>Parametri di contesto
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE), è possibile aggiungere le procedure guidate alle finestre di dialogo **nuovo progetto**, **Aggiungi nuovo elemento** o **Aggiungi progetto secondario** . Le procedure guidate aggiunte sono disponibili nel menu **file** o facendo clic con il pulsante destro del mouse su un progetto in **Esplora soluzioni**. L'IDE passa i parametri di contesto all'implementazione della procedura guidata. I parametri di contesto definiscono lo stato del progetto quando l'IDE chiama la procedura guidata.

 L'IDE avvia le procedure guidate impostando il <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag nella chiamata dell'IDE al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodo per il progetto. Se impostata, il progetto deve causare l' `IVsExtensibility::RunWizardFile` esecuzione del metodo usando il nome o il GUID della procedura guidata registrata e altri parametri di contesto che l'IDE passa a tale metodo.

## <a name="context-parameters-for-new-project"></a>Parametri di contesto per il nuovo progetto

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrato ( <xref:EnvDTE.Constants.vsWizardNewProject> ) o GUID che indica il tipo di procedura guidata. Nell' [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione il GUID della procedura guidata è {0F90E1D0-4999-11D1-b6d1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome univoco del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto. |
| `LocalDirectory` | Percorso locale dei file di progetto in esecuzione. |
| `InstallationDirectory` | Il percorso della directory del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è installazione. |
| `FExclusive` | Flag booleano che indica che il progetto deve chiudere le soluzioni aperte. |
| `SolutionName` | Nome del file di soluzione senza la parte della directory o estensione *sln* . Il nome del file con estensione *suo* viene creato anche usando `SolutionName` . Quando questo argomento non è una stringa vuota, la procedura guidata USA <xref:EnvDTE._Solution.Create%2A> prima di aggiungere il progetto con <xref:EnvDTE._Solution.AddFromTemplate%2A> . Se il nome è una stringa vuota, usare <xref:EnvDTE._Solution.AddFromTemplate%2A> senza chiamare <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Parametri di contesto per Aggiungi nuovo elemento

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrato ( <xref:EnvDTE.Constants.vsWizardAddItem> ) o GUID che indica il tipo di procedura guidata. Nell' [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione il GUID della procedura guidata è {0F90E1D1-4999-11D1-b6d1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome univoco del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto. |
| `ProjectItems` | Percorso locale che contiene i file del progetto funzionante. |
| `ItemName` | Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome del file che l'utente digita dalla finestra di dialogo **Aggiungi elementi** . Il nome è basato sui flag impostati nel file con *estensione VSDIR* . Il nome può essere un valore null. |
| `InstallationDirectory` | Il percorso della directory del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è installazione. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Parametri di contesto per Aggiungi progetto secondario

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrato ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) o GUID che indica il tipo di procedura guidata. Nell' [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementazione il GUID della procedura guidata è {0F90E1D2-4999-11D1-b6d1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome univoco del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto. |
| `ProjectItems` | Puntatore alla `ProjectItems` raccolta in cui opera la procedura guidata. Questo puntatore viene passato alla procedura guidata in base alla selezione della gerarchia del progetto. Un utente in genere seleziona una cartella in cui inserire l'elemento e quindi chiama la finestra di dialogo **Aggiungi elemento** del progetto. |
| `LocalDirectory` | Percorso locale dei file di progetto in esecuzione. |
| `ItemName` | Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome del file che l'utente digita dalla finestra di dialogo **Aggiungi elementi** . Il nome è basato sui flag impostati nel file con *estensione VSDIR* . Il nome può essere un valore null. |
| `InstallationDirectory` | Percorso della directory dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installazione. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** ( `TRUE` ). |

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File della procedura guidata (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametri di contesto per l'avvio delle procedure guidate](/previous-versions/tz690efs(v=vs.140))