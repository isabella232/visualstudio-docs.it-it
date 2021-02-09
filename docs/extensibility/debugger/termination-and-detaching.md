---
title: Terminazione e scollegamento | Microsoft Docs
description: La terminazione normale indica che un programma di cui è in corso il debug viene eseguito fino al completamento senza punti di interruzione, eccezioni, errori di run-time o cicli infiniti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ac3e8517ee99dcd52261eb87b6cee3954793d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895895"
---
# <a name="termination-and-detaching"></a>Terminazione e scollegamento
Nella sezione seguente viene descritta la chiusura normale.

## <a name="discussion"></a>Discussione
 Quando l'interfaccia [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continua, se non sono presenti punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione di cui è in corso il debug, il programma di cui viene eseguito il debug viene eseguito fino al completamento. Questo processo è una chiusura normale.

 Per implementare la terminazione normale è necessario inviare un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Per la terminazione normale è necessario eseguire il metodo [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Vedi anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
