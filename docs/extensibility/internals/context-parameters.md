---
title: Parametri di contesto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ea38b79be362f78fcc34161a480597fb0ecce40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727554"
---
# <a name="context-parameters"></a>Parametri di contesto
Nel Integrated Development Environment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) è possibile aggiungere le procedure guidate alle finestre di dialogo **nuovo progetto**, **Aggiungi nuovo elemento**o **Aggiungi progetto secondario** . Le procedure guidate aggiunte sono disponibili nel menu **file** o facendo clic con il pulsante destro del mouse su un progetto in **Esplora soluzioni**. L'IDE passa i parametri di contesto all'implementazione della procedura guidata. I parametri di contesto definiscono lo stato del progetto quando l'IDE chiama la procedura guidata.

 L'IDE avvia le procedure guidate impostando il flag <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> nella chiamata dell'IDE al metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> per il progetto. Quando è impostato, il progetto deve causare l'esecuzione del metodo `IVsExtensibility::RunWizardFile` usando il nome o il GUID della procedura guidata registrata e altri parametri di contesto che l'IDE passa a tale metodo.

## <a name="context-parameters-for-new-project"></a>Parametri di contesto per il nuovo progetto

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrato (<xref:EnvDTE.Constants.vsWizardNewProject>) o GUID che indica il tipo di procedura guidata. Nell'implementazione [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] il GUID della procedura guidata è {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome univoco del progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `LocalDirectory` | Percorso locale dei file di progetto in esecuzione. |
| `InstallationDirectory` | Il percorso della directory del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è installazione. |
| `FExclusive` | Flag booleano che indica che il progetto deve chiudere le soluzioni aperte. |
| `SolutionName` | Nome del file di soluzione senza la parte della directory o estensione *sln* . Il nome del file con *estensione suo* viene creato anche usando `SolutionName`. Quando questo argomento non è una stringa vuota, la procedura guidata USA <xref:EnvDTE._Solution.Create%2A> prima di aggiungere il progetto con <xref:EnvDTE._Solution.AddFromTemplate%2A>. Se il nome è una stringa vuota, utilizzare <xref:EnvDTE._Solution.AddFromTemplate%2A> senza chiamare <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** (`TRUE`). |

## <a name="context-parameters-for-add-new-item"></a>Parametri di contesto per Aggiungi nuovo elemento

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrato (<xref:EnvDTE.Constants.vsWizardAddItem>) o GUID che indica il tipo di procedura guidata. Nell'implementazione [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] il GUID della procedura guidata è {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome univoco del progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `ProjectItems` | Percorso locale che contiene i file del progetto funzionante. |
| `ItemName` | Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome del file che l'utente digita dalla finestra di dialogo **Aggiungi elementi** . Il nome è basato sui flag impostati nel file con *estensione VSDIR* . Il nome può essere un valore null. |
| `InstallationDirectory` | Il percorso della directory del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è installazione. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** (`TRUE`). |

## <a name="context-parameters-for-add-sub-project"></a>Parametri di contesto per Aggiungi progetto secondario

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di procedura guidata registrato (<xref:EnvDTE.Constants.vsWizardAddSubProject>) o GUID che indica il tipo di procedura guidata. Nell'implementazione [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] il GUID della procedura guidata è {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Stringa che rappresenta il nome univoco del progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `ProjectItems` | Puntatore alla raccolta di `ProjectItems` su cui opera la procedura guidata. Questo puntatore viene passato alla procedura guidata in base alla selezione della gerarchia del progetto. Un utente in genere seleziona una cartella in cui inserire l'elemento e quindi chiama la finestra di dialogo **Aggiungi elemento** del progetto. |
| `LocalDirectory` | Percorso locale dei file di progetto in esecuzione. |
| `ItemName` | Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome del file che l'utente digita dalla finestra di dialogo **Aggiungi elementi** . Il nome è basato sui flag impostati nel file con *estensione VSDIR* . Il nome può essere un valore null. |
| `InstallationDirectory` | Percorso della directory dell'installazione del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `Silent` | Valore booleano che indica se la procedura guidata deve essere eseguita automaticamente come se fosse stato fatto clic su **fine** (`TRUE`). |

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File della procedura guidata (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametri di contesto per l'avvio delle procedure guidate](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)