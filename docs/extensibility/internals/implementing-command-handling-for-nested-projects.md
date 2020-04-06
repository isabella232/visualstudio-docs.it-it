---
title: Implementazione della gestione dei comandi per i progetti annidati. Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707604"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementazione della gestione dei comandi per i progetti annidati
L'IDE può passare i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> comandi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> che vengono passati tramite e le interfacce ai progetti annidati o i progetti padre possono filtrare o eseguire l'override dei comandi.

> [!NOTE]
> Solo i comandi normalmente gestiti dal progetto padre possono essere filtrati. I comandi, ad esempio **Compilazione** e **Distribuzione** gestiti dall'IDE, non possono essere filtrati.

 I passaggi seguenti descrivono il processo per l'implementazione della gestione dei comandi.

## <a name="procedures"></a>Procedure

#### <a name="to-implement-command-handling"></a>Per implementare la gestione dei comandi

1. Quando l'utente seleziona un progetto annidato o un nodo in un progetto annidato:When the user selects a nested project or a node in a nested project:

   1. L'IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiama il metodo.

      - o -

   2. Se il comando ha avuto origine in una finestra della gerarchia, ad <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> esempio un comando del menu di scelta rapida in Esplora soluzioni, l'IDE chiama il metodo sul padre del progetto.

2. Il progetto padre può esaminare `QueryStatus`i `pguidCmdGroup` parametri `prgCmds`da passare a , ad esempio e , per determinare se il progetto padre deve filtrare i comandi. Se il progetto padre viene implementato per filtrare i comandi, deve impostare:If the parent project is implemented to filter commands, it should set:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Quindi il progetto `S_OK`padre deve restituire .

    Se il progetto padre non filtra il `S_OK`comando, deve restituire . In questo caso, l'IDE instrada automaticamente il comando al progetto figlio.

    Il progetto padre non deve instradare il comando al progetto figlio. L'IDE esegue questa attività.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
