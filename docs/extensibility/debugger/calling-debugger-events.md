---
title: Chiamata di eventi del debugger | Microsoft Docs
description: Gli eventi nelle sessioni di debug si verificano in un ordine specifico. Questo articolo elenca l'ordine di chiamata degli eventi che si verificano in una tipica sessione di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8472be00d961d5532f3e4c86e5cf63c268fb6be0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709807"
---
# <a name="call-debugger-events"></a>Chiamare eventi del debugger
Gli eventi nelle sessioni di debug si verificano in un ordine specifico.

## <a name="discussion"></a>Discussione
 Per comprendere il modello di chiamate tra il motore di debug (DE) e la gestione del debug di sessione (SDM), di seguito è riportato l'ordine di chiamata degli eventi che si verificano in una tipica sessione di debug:

1. [Collegamento e disconnessione a un programma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Avvio del debugger](../../extensibility/debugger/launching-the-debugger.md)

3. [Chiusura di un programma](../../extensibility/debugger/terminating-a-program.md)

4. [Creazione di un punto di interruzione](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Quando un punto di interruzione viene associato o non associato](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Errori dei punti di interruzione](../../extensibility/debugger/breakpoint-errors.md)

7. [Raggiungere un punto di interruzione](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Eliminazione di un punto di interruzione](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Accesso alla modalità di interruzione](../../extensibility/debugger/entering-break-mode.md)

10. [Esecuzione di istruzioni in modalità di interruzione](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Valutazione delle espressioni in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Gestione delle eccezioni](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Vedi anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
