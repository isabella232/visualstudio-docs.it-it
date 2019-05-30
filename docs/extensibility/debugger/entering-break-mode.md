---
title: Modalità di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a57ec499941e8e07d93d1917b9d12f5dfd7aca79
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341566"
---
# <a name="enter-break-mode"></a>Modalità di interruzione
Le informazioni seguenti viene descritto il processo che si verifica quando viene rilevato un punto di interruzione dopo l'esecuzione di una funzione, l'esecuzione alla riga di codice sorgente che contiene il cursore di o in esecuzione in un punto di interruzione.

## <a name="break-mode-process"></a>Processo della modalità di interruzione

1. Il motore di debug (DE) Invia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), o qualsiasi altro evento di arresto per causare l'IDE attivare la modalità di interruzione.

2. Il modello SDM Ottiene le informazioni sullo stack di chiamata dal thread, come indicato di seguito:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere le informazioni sul codice sorgente

    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) per ottenere il nome del file

    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) per ottenere l'intervallo di istruzioni

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) per ottenere informazioni sulla memoria

## <a name="see-also"></a>Vedere anche
- [La chiamata a eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)