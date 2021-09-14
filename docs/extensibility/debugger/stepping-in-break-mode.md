---
title: Esecuzione di istruzioni in modalità di interruzione | Microsoft Docs
description: Informazioni sul processo che si verifica quando il debugger è in modalità di interruzione. Il debugger deve quindi eseguire il codice un'istruzione alla pagina.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 928340634c7b34e5f731704961803b4cab85db21
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626429"
---
# <a name="stepping-in-break-mode"></a>Esecuzione di istruzioni in modalità di interruzione
Nella sezione seguente viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire il codice un'istruzione alla volta:

## <a name="stepping-process"></a>Processo di esecuzione istruzione per istruzione

1. Chiamare [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con [gli argomenti STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) per eseguire un passaggio.

2. Al termine del passaggio, inviare un [oggetto IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) come evento di arresto.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
