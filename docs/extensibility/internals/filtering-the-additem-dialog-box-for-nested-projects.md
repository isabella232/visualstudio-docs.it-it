---
title: Filtrare la finestra di dialogo AddItem per i progetti annidati | Microsoft Docs
description: Informazioni su come filtrare la finestra di dialogo AddItem per un progetto annidato in Visual Studio implementando l'interfaccia IVsFilterAddProjectItemDlg del progetto padre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 59ae3c229ba359af0349ad93edc75e53c2cc3557
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069582"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrare la finestra di dialogo AddItem per i progetti annidati
Quando si visualizza una finestra di dialogo **AddItem** per un progetto annidato, il progetto padre può controllare quali elementi vengono visualizzati nella finestra di dialogo.

 L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaccia consente di filtrare i nodi che si troveranno in una finestra di dialogo **AddItem** . Quando il progetto figlio Visualizza la finestra di dialogo **AddItem** , l'elemento padre può implementare l' `IVsFilterAddProjectItemDlg` interfaccia e filtrare gli elementi che verrebbero altrimenti visualizzati nel progetto figlio.

 Quando i progetti vengono raggruppati per funzione in progetti padre specifici, è possibile implementare `IVsFilterAddProjectItemDlg` quando l'utente seleziona **Aggiungi elemento di progetto** dal menu di scelta rapida in un progetto annidato. Implementazione `IvsFilterAddProjectItemDlg displays` solo di elementi di progetto o file specifici di tale gruppo. Gli elementi di progetto per altri gruppi vengono esclusi dalla finestra di dialogo, anche se vengono archiviati nella stessa directory.

 Quando un utente apre la finestra di dialogo **AddItem** per l'elemento figlio, viene chiamata l'implementazione del progetto padre dell' `IVsFilterAddProjectItemDlg` interfaccia.

 L' `IVsFilterAddProjectItemDlg` interfaccia può inoltre implementare il filtraggio per categoria. Per altre informazioni, vedere [aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrare i modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Aggiungi elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrare modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)
- [Annida progetti](../../extensibility/internals/nesting-projects.md)
