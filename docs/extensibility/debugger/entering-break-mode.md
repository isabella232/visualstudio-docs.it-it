---
title: Entrare in modalità di interruzione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738887"
---
# <a name="enter-break-mode"></a>Attivare la modalità di interruzione
Le informazioni seguenti descrivono il processo che si verifica quando viene rilevato un punto di interruzione dopo l'esecuzione di un'istruzione in una funzione, l'esecuzione nella riga di codice sorgente che contiene il cursore o l'esecuzione fino a un punto di interruzione.

## <a name="break-mode-process"></a>Processo della modalità di interruzione

1. Il motore di debug (DE) invia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)o qualsiasi altro evento di arresto per fare in modo che l'IDE entri in modalità di interruzione.

2. Il modello SDM ottiene le informazioni sullo stack di chiamate dal thread, come indicato di seguito:The SDM gets the call stack information from the thread, as follows:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere le informazioni sul codice sorgente

    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) per ottenere il nome del file

    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) per ottenere l'intervallo di istruzioniIDebugDocumentContext2::GetStatementRange to get the statement range

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) per ottenere informazioni sulla memoria

## <a name="see-also"></a>Vedere anche
- [Chiamata agli eventi del debuggerCalling debugger events](../../extensibility/debugger/calling-debugger-events.md)
