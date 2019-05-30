---
title: Terminazione di un programma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f82a8238b542ce9aa9f5489df38553410e1326d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331355"
---
# <a name="terminating-a-program"></a>Terminazione di un programma
La sezione seguente descrive la chiusura di un singolo programma con un solo thread.

## <a name="termination-process"></a>Processo di terminazione

1. L'invio di DE un' [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un valore valido [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. L'invio di DE un' [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un valore valido [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   L'IDE passa alla modalità progettazione. Il motore di debug o di un ambiente di runtime chiama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) per rimuovere il programma dalla porta.

## <a name="see-also"></a>Vedere anche
- [La chiamata a eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)