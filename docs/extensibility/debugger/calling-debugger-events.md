---
title: Chiamata di eventi del debugger | Microsoft Docs
description: Gli eventi nelle sessioni di debug si verificano in un ordine specifico. Questo articolo elenca l'ordine di chiamata degli eventi che si verificano in una tipica sessione di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 832b42e62731a087048b4aa50e19b74c408343c5
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914388"
---
# <a name="call-debugger-events"></a>Chiama eventi del debugger
Gli eventi nelle sessioni di debug si verificano in un ordine specifico.

## <a name="discussion"></a>Discussione
 Per comprendere il modello di chiamate tra il motore di debug (DE) e la gestione del debug della sessione (SDM), l'esempio seguente rappresenta l'ordine chiamante degli eventi che si verificano in una sessione di debug tipica:

1. [Collegamento e scollegamento di un programma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Avvio del debugger](../../extensibility/debugger/launching-the-debugger.md)

3. [Terminazione di un programma](../../extensibility/debugger/terminating-a-program.md)

4. [Creazione di un punto di interruzione](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Quando un punto di interruzione viene associato o diventa non associato](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Errori del punto di interruzione](../../extensibility/debugger/breakpoint-errors.md)

7. [Raggiungimento di un punto di interruzione](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Eliminazione di un punto di interruzione](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Immissione della modalità di interruzioni](../../extensibility/debugger/entering-break-mode.md)

10. [Esecuzione in modalità di interruzioni](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Valutazione delle espressioni in modalità di interruzioni](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Gestione delle eccezioni](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Vedi anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
