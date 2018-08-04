---
title: Il filtro nella finestra di dialogo AddItem per i progetti annidati | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61a51c69857f9bd8f5b2ad84448b0170b809c18a
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497079"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtra la finestra di dialogo AddItem per i progetti annidati
Quando si visualizza un' **AddItem** finestra di dialogo per un progetto annidato, il progetto padre è possibile controllare quali elementi vengono visualizzati nella finestra di dialogo.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaccia consente di filtrare i nodi che faranno un' **AddItem** nella finestra di dialogo. Quando il progetto figlio viene visualizzato il **AddItem** della finestra di dialogo in cui è possibile implementare l'elemento padre il `IVsFilterAddProjectItemDlg` interfaccia e filtrare gli elementi che verrebbero altrimenti visualizzati nel progetto e il suo.  
  
 Quando i progetti vengono raggruppati dalla funzione con i progetti padre specifica, è possibile implementare `IVsFilterAddProjectItemDlg` quando l'utente seleziona **Aggiungi elementi di progetto** menu di scelta rapida in un progetto annidato. Implementazione `IvsFilterAddProjectItemDlg displays` solo il progetto elementi o i file specifico di tale gruppo. Elementi di progetto per gli altri gruppi vengono filtrati dalla finestra di dialogo, anche se sono archiviati nella stessa directory.  
  
 Quando un utente apre la **AddItem** finestra di dialogo per l'elemento figlio, implementazione del progetto padre del `IVsFilterAddProjectItemDlg` interfaccia viene chiamata.  
  
 Il `IVsFilterAddProjectItemDlg` interfaccia può implementare anche filtrare per categoria. Per altre informazioni, vedere [aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Progetti di annidamento](../../extensibility/internals/nesting-projects.md)