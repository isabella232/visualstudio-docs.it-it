---
title: Terminazione e disconnessione | Microsoft Docs
description: La terminazione normale indica che un programma in fase di debug viene eseguito fino al completamento senza punti di interruzione, eccezioni, errori di runtime o cicli infiniti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 40a559a110792e5c010d37164ab1db96277ca544
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626364"
---
# <a name="termination-and-detaching"></a>Terminazione e disconnessione
La sezione seguente descrive la terminazione normale.

## <a name="discussion"></a>Discussione
 Dopo che [l'interfaccia IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continua, se non sono presenti punti di interruzione, eccezioni, errori di runtime o cicli infiniti nell'applicazione di cui eseguire il debug, il programma in fase di debug viene eseguito fino al completamento. Si tratta di un processo di terminazione normale.

 È necessario inviare [un oggetto IDebugProgramDestroyEvent2 per](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) implementare la terminazione normale. La terminazione normale richiede l'esecuzione [del metodo IDebugProgramDestroyEvent2::GetExitCode.](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)

## <a name="see-also"></a>Vedi anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
