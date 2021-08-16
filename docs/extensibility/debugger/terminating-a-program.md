---
title: Chiusura di un programma | Microsoft Docs
description: Questo articolo descrive come l'IDE usa il motore di debug per terminare un singolo programma con un singolo thread.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bbfe64c5f08cdf82001d1a7df0a80fbc3269c79de895ec499c49d8b5248532a6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306088"
---
# <a name="terminating-a-program"></a>Chiusura di un programma
La sezione seguente descrive la terminazione di un singolo programma con un thread.

## <a name="termination-process"></a>Processo di terminazione

1. Il de invia un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un [IDebugThread2 valido.](../../extensibility/debugger/reference/idebugthread2.md)

2. Il de invia un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un [IDebugProgram2 valido.](../../extensibility/debugger/reference/idebugprogram2.md)

   L'IDE passa alla modalità progettazione. Il motore di debug o l'ambiente di runtime chiama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) per rimuovere il programma dalla porta.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
