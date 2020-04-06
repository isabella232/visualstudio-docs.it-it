---
title: Chiamata agli eventi del debugger Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739172"
---
# <a name="call-debugger-events"></a>Chiamare eventi del debuggerCall debugger events
Gli eventi nelle sessioni di debug si verificano in un ordine specifico.

## <a name="discussion"></a>Discussione
 Per comprendere il modello di chiamate tra il motore di debug (DE) e il gestore di debug di sessione (SDM), quanto segue rappresenta l'ordine di chiamata degli eventi che si verificano in una sessione di debug tipica:

1. [Associazione e disconnessione a un programma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Avvio del debugger](../../extensibility/debugger/launching-the-debugger.md)

3. [Interruzione di un programma](../../extensibility/debugger/terminating-a-program.md)

4. [Creazione di un punto di interruzioneCreating a breakpoint](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Quando un punto di interruzione viene associato o diventa non associatoWhen a breakpoint binds or becoming unbound](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Errori dei punti di interruzione](../../extensibility/debugger/breakpoint-errors.md)

7. [Raggiungimento di un punto di interruzione](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Eliminazione di un punto di interruzione](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Entrare in modalità di interruzione](../../extensibility/debugger/entering-break-mode.md)

10. [Passaggio in modalità di interruzioneStepping in break mode](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Valutazione dell'espressione in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Gestione delle eccezioni](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Vedere anche
- [Creazione di un motore di debug personalizzatoCreating a custom debug engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
