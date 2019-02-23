---
title: La chiamata a eventi del Debugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27792aa1a8ca9edf1a85f4d607bbef926fb69027
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719024"
---
# <a name="call-debugger-events"></a>Chiamare gli eventi del debugger
Gli eventi nella sessione di debug e si verificano in un ordine specifico.

## <a name="discussion"></a>Discussione
 Per comprendere il criterio di chiamate tra il motore di debug (DE) e la gestione di debug di sessione (SDM), di seguito rappresenta l'ordine di chiamata degli eventi che si verificano durante una normale sessione di debug:

1.  [Collegamento e scollegamento da un programma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2.  [L'avvio del debugger](../../extensibility/debugger/launching-the-debugger.md)

3.  [Terminazione di un programma](../../extensibility/debugger/terminating-a-program.md)

4.  [Creazione di un punto di interruzione](../../extensibility/debugger/creating-a-breakpoint.md)

5.  [Quando si associa un punto di interruzione o diventare non associato](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6.  [Errori di punto di interruzione](../../extensibility/debugger/breakpoint-errors.md)

7.  [Raggiungere un punto di interruzione](../../extensibility/debugger/hitting-a-breakpoint.md)

8.  [L'eliminazione di un punto di interruzione](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Modalità di interruzione](../../extensibility/debugger/entering-break-mode.md)

10. [Esecuzione di istruzioni in modalità di interruzione](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Valutazione dell'espressione in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Gestione delle eccezioni](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Vedere anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)