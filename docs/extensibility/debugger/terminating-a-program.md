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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ccc94c0466f02c402271952b76f8b1e42a265983
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125205"
---
# <a name="terminating-a-program"></a>Terminazione di un programma
La sezione seguente descrive la terminazione di un singolo programma con un thread.

## <a name="termination-process"></a>Processo di terminazione

1. DE invia un [oggetto IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un [oggetto IDebugThread2 valido.](../../extensibility/debugger/reference/idebugthread2.md)

2. DE invia un [oggetto IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un [oggetto IDebugProgram2 valido.](../../extensibility/debugger/reference/idebugprogram2.md)

   L'IDE passa alla modalità progettazione. Il motore di debug o l'ambiente di runtime chiama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) per rimuovere il programma dalla porta.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
