---
title: Implementazione della gestione dei comandi per i progetti annidati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2fbce80b2e8c337eddf0d34954a7fd70b895d891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839687"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementazione della gestione dei comandi per i progetti annidati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'IDE può passare i comandi passati attraverso il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> e le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfacce ai progetti annidati oppure i progetti padre possono filtrare o eseguire l'override dei comandi.  
  
> [!NOTE]
> È possibile filtrare solo i comandi normalmente gestiti dal progetto padre. Non è possibile filtrare i comandi come la **compilazione** e la **distribuzione** gestiti dall'IDE.  
  
 Nei passaggi seguenti viene descritto il processo di implementazione della gestione dei comandi.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-implement-command-handling"></a>Per implementare la gestione dei comandi  
  
1. Quando l'utente seleziona un progetto annidato o un nodo in un progetto annidato:  
  
   1. L'IDE chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo.  
  
      - o -  
  
   2. Se il comando ha avuto origine in una finestra della gerarchia, ad esempio un comando di menu di scelta rapida in Esplora soluzioni, l'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metodo nell'elemento padre del progetto.  
  
2. Il progetto padre può esaminare i parametri da passare a `QueryStatus` , ad esempio `pguidCmdGroup` e `prgCmds` , per determinare se il progetto padre deve filtrare i comandi. Se il progetto padre viene implementato per filtrare i comandi, deve impostare:  
  
   ```  
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
   // make sure it is disabled  
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
   ```  
  
    Il progetto padre deve quindi restituire `S_OK` .  
  
    Se il progetto padre non filtra il comando, dovrebbe solo restituire `S_OK` . In questo caso, l'IDE instrada automaticamente il comando al progetto figlio.  
  
    Il progetto padre non deve eseguire il routing del comando al progetto figlio. Questa attività viene eseguita dall'IDE.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
