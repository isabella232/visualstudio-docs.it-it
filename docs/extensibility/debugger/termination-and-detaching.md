---
title: Terminazione e scollegamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8aafb94e0a07462d93cc77a34f7199f61f944d0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333718"
---
# <a name="termination-and-detaching"></a>Terminazione e scollegamento
La sezione seguente descrive terminazione normale.

## <a name="discussion"></a>Discussione
 Dopo il [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oppure [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfaccia continua, se non esistono punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione da sottoporre a debug, il programma in fase di debug viene eseguito fino al completamento. Questo processo è terminazione normale.

 È necessario inviare un' [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) implementare terminazione normale. Terminazione normale richiede l'esecuzione di [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)