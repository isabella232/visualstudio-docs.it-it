---
title: Esecuzione in modalità di interruzioni | Microsoft Docs
description: Informazioni sul processo che si verifica quando il debugger è in modalità di interruzione. Il debugger deve quindi eseguire il codice istruzione per istruzione.
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
ms.workload:
- vssdk
ms.openlocfilehash: 0ed11d05e4351ac6ba76bc9aa10531a8a96ddf23
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075406"
---
# <a name="stepping-in-break-mode"></a>Esecuzione in modalità di interruzioni
Nella sezione seguente viene descritto il processo che si verifica quando il debugger è in modalità di interruzione ed è necessario eseguire il codice un'istruzione alla volta:

## <a name="stepping-process"></a>Esecuzione di un processo

1. Chiamare [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con gli argomenti [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) per eseguire un passaggio.

2. Al termine del passaggio, inviare un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) come evento di arresto.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
