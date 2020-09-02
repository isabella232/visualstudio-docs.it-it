---
title: Filtrare la finestra di dialogo AddItem per i progetti annidati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538096"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Applicazione di un filtro nella finestra di dialogo AddItem per i progetti annidati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si visualizza una finestra di dialogo **AddItem** per un progetto annidato, il progetto padre può controllare quali elementi vengono visualizzati nella finestra di dialogo.  
  
 L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaccia consente di filtrare i nodi che si troveranno in una finestra di dialogo **AddItem** . Quando il progetto figlio Visualizza la finestra di dialogo **AddItem** , l'elemento padre può implementare l' `IVsFilterAddProjectItemDlg` interfaccia e filtrare gli elementi che verrebbero altrimenti visualizzati nel progetto figlio.  
  
 Quando i progetti vengono raggruppati per funzione in progetti padre specifici, è possibile implementare `IVsFilterAddProjectItemDlg` quando l'utente seleziona **Aggiungi elemento di progetto** dal menu di scelta rapida in un progetto annidato. Implementazione `IvsFilterAddProjectItemDlg displays` solo di elementi di progetto o file specifici di tale gruppo. Gli elementi di progetto per altri gruppi vengono esclusi dalla finestra di dialogo, anche se vengono archiviati nella stessa directory.  
  
 Quando un utente apre la finestra di dialogo **AddItem** per l'elemento figlio, viene chiamata l'implementazione del progetto padre dell' `IVsFilterAddProjectItemDlg` interfaccia.  
  
 L' `IVsFilterAddProjectItemDlg` interfaccia può inoltre implementare il filtraggio per categoria. Per ulteriori informazioni, vedere [aggiunta di elementi alle finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrazione dei modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Aggiunta di elementi alle finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrazione di modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
