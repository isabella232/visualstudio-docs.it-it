---
title: Il filtro nella finestra di dialogo AddItem per i progetti annidati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c007a2aa0895460f539acb50f49844f8ec158fa7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529354"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Applicazione di un filtro nella finestra di dialogo AddItem per i progetti annidati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [filtro nella finestra di dialogo AddItem per i progetti annidati](https://docs.microsoft.com/visualstudio/extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects).  
  
Quando si visualizza un' **AddItem** finestra di dialogo per un progetto annidato, il progetto padre è possibile controllare quali elementi vengono visualizzati nella finestra di dialogo.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaccia consente di filtrare i nodi che faranno un' **AddItem** nella finestra di dialogo. Quando il progetto figlio viene visualizzato il **AddItem** della finestra di dialogo in cui è possibile implementare l'elemento padre il `IVsFilterAddProjectItemDlg` interfaccia e filtrare gli elementi che verrebbero altrimenti visualizzati nel progetto e il suo.  
  
 Quando i progetti vengono raggruppati dalla funzione con i progetti padre specifica, è possibile implementare `IVsFilterAddProjectItemDlg` quando l'utente seleziona **Aggiungi elementi di progetto** menu di scelta rapida in un progetto annidato. Implementazione `IvsFilterAddProjectItemDlg displays` solo il progetto elementi o i file specifico di tale gruppo. Elementi di progetto per gli altri gruppi vengono filtrati dalla finestra di dialogo, anche se sono archiviati nella stessa directory.  
  
 Quando un utente apre la **AddItem** finestra di dialogo per l'elemento figlio, implementazione del progetto padre del `IVsFilterAddProjectItemDlg` interfaccia viene chiamata.  
  
 Il `IVsFilterAddProjectItemDlg` interfaccia può implementare anche filtrare per categoria. Per altre informazioni, vedere [aggiunta di elementi finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrazione di Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)

