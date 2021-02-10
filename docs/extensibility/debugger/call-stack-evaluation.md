---
title: Valutazione dello stack di chiamate | Microsoft Docs
description: Informazioni sul metodo EnumFrameInfo e su come implementarlo per visualizzare gli stack frame dello stack di chiamate durante la modalità di rottura.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 223b1fff75c8fefdfed5bce5765d82fc5309738d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930733"
---
# <a name="call-stack-evaluation"></a>Valutazione dello stack di chiamate
Per visualizzare gli stack frame dello stack di chiamate durante la modalità di Breaking, è necessario implementare il metodo [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="methods-for-evaluation"></a>Metodi per la valutazione
 Per un semplice motore di debug (DE), potrebbe essere presente un solo stack frame. Per esaminare il stack frame durante la modalità di interruzioni, è necessario implementare i metodi di [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ottiene il contesto di codice per un stack frame. Il contesto di codice rappresenta il puntatore all'istruzione corrente in un stack frame.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto del documento per un stack frame. Il contesto del documento rappresenta la posizione corrente nel codice sorgente per un stack frame. Obbligatorio per la visualizzazione del codice sorgente quando si è arrestati in un programma.|

 Questi metodi richiedono l'implementazione di diverse interfacce e metodi correlati al contesto. Pertanto, è necessario implementare il metodo [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) e i metodi seguenti di [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Metodo|Descrizione|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo di istruzioni file di un contesto di documento.|

 Per enumerare i contesti di codice, è necessario implementare tutti i metodi di [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Vedi anche
- [Controllo di esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
