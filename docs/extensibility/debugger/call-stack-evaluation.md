---
title: Valutazione dello stack di chiamate | Microsoft Docs
description: Informazioni sul metodo EnumFrameInfo e su come implementarlo per visualizzare gli stack frame dello stack di chiamate durante la modalità di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a196560a3b0ee2fc10733b112540b1f9ff619e67
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709808"
---
# <a name="call-stack-evaluation"></a>Valutazione dello stack di chiamate
Per visualizzare gli stack frame dello stack di chiamate durante la modalità di interruzione, è necessario implementare il [metodo EnumFrameInfo.](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="methods-for-evaluation"></a>Metodi per la valutazione
 Per un motore di debug semplice , potrebbe essere presente un solo stack frame. Per esaminare il stack frame durante la modalità di interruzione, è necessario implementare i metodi seguenti di [IDebugStackFrame2.](../../extensibility/debugger/reference/idebugstackframe2.md)

|Metodo|Descrizione|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ottiene il contesto del codice per un stack frame. Il contesto del codice rappresenta il puntatore all'istruzione corrente in un stack frame.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto del documento per un stack frame. Il contesto del documento rappresenta la posizione corrente nel codice sorgente per un stack frame. Obbligatorio per la visualizzazione del codice sorgente quando si è arrestati in un programma.|

 Questi metodi richiedono l'implementazione di diversi metodi e interfacce correlati al contesto. È quindi necessario implementare il [metodo GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) e i metodi seguenti di [IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

|Metodo|Descrizione|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo di istruzioni file di un contesto di documento.|

 Per enumerare i contesti di codice, è necessario implementare tutti i metodi di [IEnumDebugCodeContexts2.](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)

## <a name="see-also"></a>Vedi anche
- [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
