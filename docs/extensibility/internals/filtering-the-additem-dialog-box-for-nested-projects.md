---
title: Applicazione di filtri alla finestra di dialogo AddItem per i progetti annidati | Microsoft Docs
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5bb4a9a76cc4ca074051ccb7ad48ae70b0e29e92
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636196"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrare la finestra di dialogo AddItem per i progetti annidati
Quando si visualizza una **finestra di dialogo AddItem** per un progetto annidato, il progetto padre può controllare quali elementi vengono visualizzati nella finestra di dialogo.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>L'interfaccia consente di filtrare i nodi che saranno in una **finestra di dialogo AddItem.** Quando il progetto figlio visualizza la finestra di dialogo **AddItem,** il padre può implementare l'interfaccia e filtrare gli elementi che altrimenti verrebbero visualizzati nel `IVsFilterAddProjectItemDlg` progetto del figlio.

 Quando i progetti vengono raggruppati per funzione in progetti padre specifici, è possibile implementare quando l'utente seleziona Aggiungi elemento Project nel menu di scelta rapida `IVsFilterAddProjectItemDlg` in un progetto annidato.  Implementazione `IvsFilterAddProjectItemDlg displays` solo di elementi di progetto o file specifici di tale gruppo. Project elementi per altri gruppi vengono filtrati dalla finestra di dialogo, anche se sono archiviati nella stessa directory.

 Quando un utente apre la **finestra di dialogo AddItem** per l'elemento figlio, viene chiamata l'implementazione dell'interfaccia del `IVsFilterAddProjectItemDlg` progetto padre.

 `IVsFilterAddProjectItemDlg`L'interfaccia può anche implementare il filtro in base alla categoria. Per altre informazioni, vedere [Aggiungere elementi alla finestra di](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) dialogo Aggiungi nuovo elemento e [Registrare modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrare i modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Annidare i progetti](../../extensibility/internals/nesting-projects.md)
