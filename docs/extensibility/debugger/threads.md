---
title: Thread | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712483"
---
# <a name="threads"></a>Threads
Nell'architettura del debugger, un *thread*:

- È l'unità di calcolo fondamentale. Un thread esegue in modo sequenziale le istruzioni all'interno del contesto di un singolo stack di chiamate, passando da un contesto di codice a quello successivo.

- Consente di identificare se stesso e il programma in cui è in esecuzione. I thread possono essere denominati, sospesi e ripresi. Un thread può anche enumerare gli stack frame associati e, in alcune condizioni, può essere spostato in un altro stack frame. Dato il contesto di un stack frame, un thread può restituire il thread logico associato, se presente. Un thread ha proprietà, ad esempio un conteggio di sospensione, che possono essere visualizzate nella finestra **thread** dell'IDE.

- È rappresentato da un'interfaccia [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , in genere creata da un motore di debug (de) o da una macchina virtuale come conseguenza dell'esecuzione di un programma.

## <a name="see-also"></a>Vedere anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md)
