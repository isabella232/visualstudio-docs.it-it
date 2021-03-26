---
title: Implementazione della gestione dei comandi per i progetti annidati | Microsoft Docs
description: Informazioni su come implementare la gestione dei comandi per i progetti annidati in Visual Studio Integrated Development Environment (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fad154fd3739369b0ccf7e5d896d1b9f1728c68e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085780"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementazione della gestione dei comandi per i progetti annidati
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

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
