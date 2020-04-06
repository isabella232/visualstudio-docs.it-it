---
title: Filtraggio della finestra di dialogo AddItem per i progetti nidificati . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708388"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrare la finestra di dialogo AggiungiElemento per i progetti nidificati
Quando si visualizza una finestra di dialogo **AddItem** per un progetto annidato, il progetto padre può controllare quali elementi vengono visualizzati nella finestra di dialogo.

 L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> consente di filtrare i nodi che saranno in un **AddItem** finestra di dialogo. Quando il progetto figlio visualizza il **AddItem** la `IVsFilterAddProjectItemDlg` finestra di dialogo, l'elemento padre può implementare l'interfaccia e filtrare gli elementi che verrebbero altrimenti visualizzati nel progetto dell'elemento figlio.

 Quando i progetti vengono raggruppati per funzione `IVsFilterAddProjectItemDlg` in progetti padre specifici, è possibile implementare quando l'utente seleziona **Aggiungi elemento** di progetto nel menu di scelta rapida in un progetto annidato. Implementazione `IvsFilterAddProjectItemDlg displays` solo di elementi di progetto o file specifici per tale gruppo. Gli elementi di progetto per altri gruppi vengono filtrati dalla finestra di dialogo, anche se sono archiviati nella stessa directory.

 Quando un utente apre il **AddItem** la finestra di dialogo `IVsFilterAddProjectItemDlg` per l'elemento figlio, viene chiamata l'implementazione del progetto padre dell'interfaccia.

 L'interfaccia `IVsFilterAddProjectItemDlg` può anche implementare il filtro per categoria. Per ulteriori informazioni, vedere Aggiungere elementi alla finestra di [dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e Registra modelli di [progetto e elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrare modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Nidificare i progetti](../../extensibility/internals/nesting-projects.md)
