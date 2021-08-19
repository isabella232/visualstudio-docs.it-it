---
title: Implementazione della gestione dei comandi per i progetti annidati | Microsoft Docs
description: Informazioni su come implementare la gestione dei comandi per i progetti annidati nell Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9489f37fff9fe1e798a42825a29cf59ec49336e2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042322"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementazione della gestione dei comandi per i progetti annidati
L'IDE può passare i comandi passati tramite le interfacce e ai progetti annidati oppure i progetti padre possono <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> filtrare o eseguire l'override dei comandi.

> [!NOTE]
> È possibile filtrare solo i comandi normalmente gestiti dal progetto padre. Non è possibile **filtrare** comandi come **Compila** e Distribuisci gestiti dall'IDE.

 La procedura seguente descrive il processo di implementazione della gestione dei comandi.

## <a name="procedures"></a>Procedure

#### <a name="to-implement-command-handling"></a>Per implementare la gestione dei comandi

1. Quando l'utente seleziona un progetto annidato o un nodo in un progetto annidato:

   1. L'IDE chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo .

      - o -

   2. Se il comando ha origine in una finestra della gerarchia, ad esempio un comando di menu di scelta rapida in Esplora soluzioni, l'IDE chiama il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> sull'elemento padre del progetto.

2. Il progetto padre può esaminare i parametri da passare a , ad esempio e , per determinare se il `QueryStatus` `pguidCmdGroup` progetto padre deve `prgCmds` filtrare i comandi. Se il progetto padre viene implementato per filtrare i comandi, deve impostare:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Il progetto padre deve quindi restituire `S_OK` .

    Se il progetto padre non filtra il comando, deve restituire solo `S_OK` . In questo caso, l'IDE indirizza automaticamente il comando al progetto figlio.

    Il progetto padre non deve instradare il comando al progetto figlio. L'IDE esegue questa attività.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
