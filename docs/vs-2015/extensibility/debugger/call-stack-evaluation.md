---
title: Valutazione dello stack di chiamate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15fecbc61fec8ba7aa62ca7d79cf11c56b7ce938
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146408"
---
# <a name="call-stack-evaluation"></a>Valutazione dello stack di chiamate
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
