---
title: Terminazione di un programma | Microsoft Docs
description: Questo articolo descrive come l'IDE usa il motore di debug per terminare un singolo programma con un singolo thread.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b2b883611d5479f0febc169b32f7f378230be4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995980"
---
# <a name="terminating-a-program"></a>Terminazione di un programma
Nella sezione seguente viene descritta la chiusura di un singolo programma con un solo thread.

## <a name="termination-process"></a>Processo di terminazione

1. Il DE Invia un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)valido.

2. Il DE Invia un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)valido.

   L'IDE passa alla modalità progettazione. Il motore di debug o l'ambiente di run-time chiama [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) per rimuovere il programma dalla porta.

## <a name="see-also"></a>Vedere anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
