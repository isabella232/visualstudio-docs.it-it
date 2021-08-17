---
title: Immissione della modalità di interruzione | Microsoft Docs
description: Informazioni sul processo che si verifica per un punto di interruzione rilevato in una funzione, sull'esecuzione fino alla riga di codice sorgente in corrispondenza del cursore o sull'esecuzione fino a un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 79e864849059e7d3e3543dbe2df6c2b79c720d7730e45431cfaa4ec8a4d26dca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342986"
---
# <a name="enter-break-mode"></a>Entrare in modalità di interruzione
Nelle informazioni seguenti viene descritto il processo che si verifica quando viene rilevato un punto di interruzione dopo l'esecuzione di un'istruzione in una funzione, l'esecuzione fino alla riga di codice sorgente che contiene il cursore o l'esecuzione fino a un punto di interruzione.

## <a name="break-mode-process"></a>Processo in modalità di interruzione

1. Il motore di debug invia [IDebugBreakpointEvent2,](../../extensibility/debugger/reference/idebugbreakpointevent2.md) [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)o qualsiasi altro evento di arresto per far sì che l'IDE entri in modalità di interruzione.

2. SDM ottiene le informazioni sullo stack di chiamate dal thread, come indicato di seguito:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere le informazioni sul codice sorgente

    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) per ottenere il nome del file

    - [IDebugDocumentContext2::GetStatementRange per](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) ottenere l'intervallo di istruzioni

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) per ottenere informazioni sulla memoria

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
