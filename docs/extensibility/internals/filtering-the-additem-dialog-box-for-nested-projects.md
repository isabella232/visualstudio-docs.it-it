---
title: Il filtro nella finestra di dialogo AddItem per i progetti annidati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38b56753bfc56a1143d8c5423ddf7714f0b2f21e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606030"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtra la finestra di dialogo AddItem per i progetti annidati
Quando si visualizza un' **AddItem** finestra di dialogo per un progetto annidato, il progetto padre è possibile controllare quali elementi vengono visualizzati nella finestra di dialogo.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaccia consente di filtrare i nodi che faranno un' **AddItem** nella finestra di dialogo. Quando il progetto figlio viene visualizzato il **AddItem** della finestra di dialogo in cui è possibile implementare l'elemento padre il `IVsFilterAddProjectItemDlg` interfaccia e filtrare gli elementi che verrebbero altrimenti visualizzati nel progetto e il suo.

 Quando i progetti vengono raggruppati dalla funzione con i progetti padre specifica, è possibile implementare `IVsFilterAddProjectItemDlg` quando l'utente seleziona **Aggiungi elementi di progetto** menu di scelta rapida in un progetto annidato. Implementazione `IvsFilterAddProjectItemDlg displays` solo il progetto elementi o i file specifico di tale gruppo. Elementi di progetto per gli altri gruppi vengono filtrati dalla finestra di dialogo, anche se sono archiviati nella stessa directory.

 Quando un utente apre la **AddItem** finestra di dialogo per l'elemento figlio, implementazione del progetto padre del `IVsFilterAddProjectItemDlg` interfaccia viene chiamata.

 Il `IVsFilterAddProjectItemDlg` interfaccia può implementare anche filtrare per categoria. Per altre informazioni, vedere [aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Progetti di annidamento](../../extensibility/internals/nesting-projects.md)