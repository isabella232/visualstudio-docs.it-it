---
title: Thread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d931568258099fa4a8fe8f3b82d3fe50d5a3e35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912713"
---
# <a name="threads"></a>Thread
Nell'architettura di debugger, un *thread*:

- È l'unità fondamentale di calcolo. Un thread viene eseguito in modo sequenziale le proprie istruzioni all'interno del contesto di uno stack di chiamate singolo, lo spostamento dal contesto di un codice a quella successiva.

- Possibile identificare se stesso e il programma in che è in esecuzione. Thread può essere denominato, sospesa e ripresa. Un thread può inoltre enumerare relativo frame dello stack associata e, in alcune condizioni, può essere spostato in un altro stack frame. Dato il contesto di un frame dello stack, un thread può restituire il thread logico associato, se presente. Un thread dispone di proprietà, ad esempio un conteggio di sospensione, che possono essere visualizzati nei **thread** finestra dell'IDE.

- È rappresentato da un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaccia, in genere creato da un motore di debug (DE) o una macchina virtuale di conseguenza l'esecuzione di un programma.

## <a name="see-also"></a>Vedere anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Gestione del debug della sessione](../../extensibility/debugger/session-debug-manager.md)