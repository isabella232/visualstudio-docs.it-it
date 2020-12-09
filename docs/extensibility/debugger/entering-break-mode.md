---
title: Immissione della modalità di interruzioni | Microsoft Docs
description: Informazioni sul processo che si verifica per un punto di interruzione rilevato in una funzione, in esecuzione fino alla riga del codice sorgente in corrispondenza del cursore o in esecuzione fino a un punto di interruzione.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e73c64d17aee48cdb67a110e93aa556f112a1014
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915232"
---
# <a name="enter-break-mode"></a>Immettere la modalità di interruzioni
Le informazioni seguenti descrivono il processo che si verifica quando viene rilevato un punto di interruzione dopo l'esecuzione di un'istruzione in una funzione, l'esecuzione fino alla riga del codice sorgente in cui è presente il cursore o l'esecuzione fino a un punto di interruzione.

## <a name="break-mode-process"></a>Processo in modalità di interruzioni

1. Il motore di debug (DE) Invia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)o qualsiasi altro evento di arresto per far sì che l'IDE entri in modalità di interruzione.

2. SDM ottiene le informazioni sullo stack di chiamate dal thread, come indicato di seguito:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere le informazioni sul codice sorgente

    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) per ottenere il nome del file

    - [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) per ottenere l'intervallo di istruzioni

    - [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) per ottenere informazioni sulla memoria

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
