---
title: Esecuzione di istruzioni in modalità di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3a8688f32a97d27ee6f6e2d18fcea8e25feaac2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348540"
---
# <a name="stepping-in-break-mode"></a>Esecuzione di istruzioni in modalità di interruzione
La sezione seguente descrive il processo che si verifica quando il debugger è in modalità di interruzione e deve esaminare il codice:

## <a name="stepping-process"></a>Processo di debug passo a passo

1. Chiamare [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argomenti per eseguire un passaggio.

2. Quando viene completato il passaggio, inviare un' [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) come un evento di arresto.

## <a name="see-also"></a>Vedere anche
- [La chiamata a eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)