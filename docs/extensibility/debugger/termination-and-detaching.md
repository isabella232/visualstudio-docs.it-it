---
title: Terminazione e disconnessione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712486"
---
# <a name="termination-and-detaching"></a>Terminazione e disconnessione
Nella sezione seguente viene descritta la terminazione normale.

## <a name="discussion"></a>Discussione
 Dopo il [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfaccia continua, se non sono presenti punti di interruzione, eccezioni, errori di runtime o cicli infiniti nell'applicazione da sottoporre a debug, il programma in fase di debug viene eseguito fino al completamento. Questo processo è terminazione normale.

 È necessario inviare un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) per implementare la terminazione normale. La terminazione normale richiede l'esecuzione del metodo [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Vedere anche
- [Creazione di un motore di debug personalizzatoCreating a custom debug engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
