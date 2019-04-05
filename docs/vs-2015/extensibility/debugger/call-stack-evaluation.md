---
title: Valutazione dello Stack di chiamate | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964416"
---
# <a name="call-stack-evaluation"></a>Valutazione dello stack di chiamate
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per visualizzare gli stack frame dello stack di chiamate durante la modalità di interruzione, è necessario implementare il [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) (metodo).  
  
## <a name="methods-for-evaluation"></a>Metodi per la valutazione  
 Per un motore di debug semplici (DE), potrebbe esserci un solo frame dello stack. Per esaminare lo stack frame in modalità di interruzione, è necessario implementare i metodi seguenti della [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ottiene il contesto del codice per uno stack frame. Il contesto del codice rappresenta il puntatore all'istruzione corrente in uno stack frame.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto del documento per uno stack frame. Il contesto del documento rappresenta la posizione corrente nel codice sorgente di uno stack frame. Obbligatorio per la visualizzazione del codice sorgente quando si è interrotto in un programma.|  
  
 Questi metodi richiedono l'implementazione dei diversi metodi e interfacce relative al contesto. Di conseguenza, è necessario implementare il [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) metodo e i metodi seguenti della [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo di istruzioni di file di un contesto di documento.|  
  
 Per enumerare i contesti di codice, è necessario implementare tutti i metodi del [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
