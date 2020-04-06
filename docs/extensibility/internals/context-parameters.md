---
title: Parametri di contesto . Documenti Microsoft
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
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709301"
---
# <a name="context-parameters"></a>Parametri di contesto
Nell'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE), è possibile aggiungere procedure guidate alle finestre di dialogo **Nuovo progetto**, Aggiungi nuovo **elemento**o Aggiungi **progetto secondario** . Le procedure guidate aggiunte sono disponibili nel menu File o facendo clic **con** il pulsante destro del mouse su un progetto in **Esplora soluzioni**. L'IDE passa i parametri di contesto all'implementazione della procedura guidata. I parametri di contesto definiscono lo stato del progetto quando l'IDE chiama la procedura guidata.

 L'IDE avvia le <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> procedure guidate impostando il flag <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> nella chiamata dell'IDE al metodo per il progetto. Quando è impostato, il `IVsExtensibility::RunWizardFile` progetto deve causare il metodo da eseguire utilizzando il nome della procedura guidata registrato o GUID e altri parametri di contesto che l'IDE passa a esso.

## <a name="context-parameters-for-new-project"></a>Parametri di contesto per il nuovo progetto

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di<xref:EnvDTE.Constants.vsWizardNewProject>procedura guidata registrato ( ) o GUID che indica il tipo di procedura guidata. Nell'implementazione, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] il GUID per la procedura guidata è .0F90E1D0-4999-11D1-B6D1-00A0C90F2744. |
| `ProjectName` | Stringa che è [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il nome univoco del progetto. |
| `LocalDirectory` | Percorso locale dei file di progetto di lavoro. |
| `InstallationDirectory` | Percorso della [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory dell'installazione. |
| `FExclusive` | Flag booleano che indica che il progetto deve chiudere le soluzioni aperte. |
| `SolutionName` | Nome del file di soluzione senza la parte della directory o l'estensione *sln.* Il nome del file *.suo* viene creato anche utilizzando `SolutionName`. Quando questo argomento non è una <xref:EnvDTE._Solution.Create%2A> stringa vuota, <xref:EnvDTE._Solution.AddFromTemplate%2A>la procedura guidata viene utilizzata prima di aggiungere il progetto con . Se questo nome è una <xref:EnvDTE._Solution.AddFromTemplate%2A> stringa <xref:EnvDTE._Solution.Create%2A>vuota, utilizzare senza chiamare . |
| `Silent` | Valore booleano che indica se la procedura guidata deve`TRUE`essere eseguita automaticamente come se si facesse clic su **Fine** ( ). |

## <a name="context-parameters-for-add-new-item"></a>Parametri di contesto per Aggiungi nuovo elemento

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di<xref:EnvDTE.Constants.vsWizardAddItem>procedura guidata registrato ( ) o GUID che indica il tipo di procedura guidata. Nell'implementazione, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] il GUID per la procedura guidata è "0F90E1D1-4999-11D1-B6D1-00A0C90F2744". |
| `ProjectName` | Stringa che è [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il nome univoco del progetto. |
| `ProjectItems` | Percorso locale che contiene i file di progetto di lavoro. |
| `ItemName` | Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome file digitato dall'utente dalla finestra di dialogo **Aggiungi elementi.** Il nome è basato sui flag impostati nel file *VSDIR.* Il nome può essere un valore null. |
| `InstallationDirectory` | Percorso della [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory dell'installazione. |
| `Silent` | Valore booleano che indica se la procedura guidata deve`TRUE`essere eseguita automaticamente come se si facesse clic su **Fine** ( ). |

## <a name="context-parameters-for-add-sub-project"></a>Parametri di contesto per Aggiungi progetto secondario

| Parametro | Descrizione |
|-------------------------| - |
| `WizardType` | Tipo di<xref:EnvDTE.Constants.vsWizardAddSubProject>procedura guidata registrato ( ) o GUID che indica il tipo di procedura guidata. Nell'implementazione, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] il GUID per la procedura guidata è "0F90E1D2-4999-11D1-B6D1-00A0C90F2744". |
| `ProjectName` | Stringa che è [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il nome univoco del progetto. |
| `ProjectItems` | Puntatore `ProjectItems` alla raccolta in cui opera la procedura guidata. Questo puntatore viene passato alla procedura guidata in base alla selezione della gerarchia del progetto. Un utente in genere seleziona una cartella in cui inserire l'elemento e quindi chiama il progetto **Aggiungi elemento** la finestra di dialogo. |
| `LocalDirectory` | Percorso locale dei file di progetto di lavoro. |
| `ItemName` | Nome dell'elemento da aggiungere. Questo nome è il nome file predefinito o il nome file digitato dall'utente dalla finestra di dialogo **Aggiungi elementi.** Il nome è basato sui flag impostati nel file *VSDIR.* Il nome può essere un valore null. |
| `InstallationDirectory` | Percorso della [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory dell'installazione. |
| `Silent` | Valore booleano che indica se la procedura guidata deve`TRUE`essere eseguita automaticamente come se si facesse clic su **Fine** ( ). |

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File della procedura guidata (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametri di contesto per l'avvio di procedure guidateContext parameters for launching wizards](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
