---
title: Valutazione dello stack di chiamate Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739185"
---
# <a name="call-stack-evaluation"></a>Valutazione dello stack di chiamate
Per visualizzare gli stack frame dello stack di chiamate durante la modalità di interruzione, è necessario implementare il [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metodo.

## <a name="methods-for-evaluation"></a>Metodi di valutazione
 Per un motore di debug semplice (DE), potrebbe essere presente un solo stack frame. Per esaminare lo stack frame durante la modalità di interruzione, è necessario implementare i seguenti metodi di [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Metodo|Descrizione|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ottiene il contesto del codice per uno stack frame. Il contesto di codice rappresenta il puntatore all'istruzione corrente in uno stack frame.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto del documento per uno stack frame. Il contesto del documento rappresenta la posizione corrente nel codice sorgente per uno stack frame. Obbligatorio per la visualizzazione del codice sorgente quando si è arrestati in un programma.|

 Questi metodi richiedono l'implementazione di diverse interfacce e metodi correlati al contesto. Pertanto, è necessario implementare il [metodo GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) e i seguenti metodi di [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Metodo|Descrizione|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo di istruzioni del file di un contesto del documento.|

 Per enumerare i contesti di codice, è necessario implementare tutti i metodi di [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
