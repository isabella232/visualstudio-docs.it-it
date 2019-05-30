---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59573736ca3cd0768d3383e5621d96dffdea9746
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338886"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Questa interfaccia rappresenta la posizione iniziale di un'istruzione di codice. Per la maggior parte delle architetture di run-time oggi, un contesto del codice può essere considerato come un indirizzo nel flusso di esecuzione del programma.

## <a name="syntax"></a>Sintassi

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per correlare la posizione di un'istruzione di codice in una posizione del documento.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi sul numero di interfacce restituiscono più di frequente, questa interfaccia, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Viene anche usato spesso con la [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interfaccia anche come informazioni di risoluzione del punto di interruzione.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nel [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaccia, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ottiene il contesto del documento che corrisponde al contesto di codice attivo.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ottiene le informazioni sulla lingua per il contesto di codice.|

## <a name="remarks"></a>Note
 La differenza principale tra un' `IDebugCodeContext2` interfaccia e un' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaccia è che un `IDebugCodeContext2` è sempre istruzione allineato. Ciò significa che un' `IDebugCodeContext2` fa sempre riferimento all'inizio di un'istruzione, mentre un `IDebugMemoryContext2` può puntare a qualsiasi byte di memoria nell'architettura di runtime. `IDebugCodeContext2` viene incrementato per le istruzioni non per le dimensioni di archiviazione di base (in genere byte).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [avanti](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)