---
title: Proprietà Threads . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712483"
---
# <a name="threads"></a>Threads
Nell'architettura del debugger, un *thread*:

- È l'unità fondamentale di calcolo. Un thread esegue in sequenza le istruzioni nel contesto di un singolo stack di chiamate, passando da un contesto di codice a quello successivo.

- Può identificare se stesso e il programma in cui è in esecuzione. I thread possono essere denominati, sospesi e ripresi. Un thread può anche enumerare gli stack frame associati e, in alcune condizioni, può essere spostato in un altro stack frame. Dato il contesto di uno stack frame, un thread può restituire il thread logico associato, se presente. Un thread dispone di proprietà, ad esempio un conteggio di sospensione, che possono essere visualizzate nella finestra **Thread** dell'IDE.

- È rappresentato da un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaccia, in genere creato da un motore di debug (DE) o macchina virtuale come conseguenza dell'esecuzione di un programma.

## <a name="see-also"></a>Vedere anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md)
- [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md)
