---
title: Passo in modalità di interruzione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712851"
---
# <a name="stepping-in-break-mode"></a>Passaggio in modalità di interruzioneStepping in break mode
Nella sezione seguente viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire il codice un'istruzione alla volta:The following section describes the process that occurs when the debugger is in break mode and must step through code:

## <a name="stepping-process"></a>Processo di stepping

1. Chiamare [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con gli argomenti [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) per eseguire un passaggio.

2. Al termine del passaggio, inviare un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) come evento di arresto.

## <a name="see-also"></a>Vedere anche
- [Chiamata agli eventi del debuggerCalling debugger events](../../extensibility/debugger/calling-debugger-events.md)
