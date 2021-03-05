---
description: Questa interfaccia rappresenta la posizione iniziale di un'istruzione di codice.
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 228b6e84ca2f85803c4a248b966698b822bb572f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164097"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Questa interfaccia rappresenta la posizione iniziale di un'istruzione di codice. Per la maggior parte delle architetture di runtime oggi, un contesto di codice può essere considerato come un indirizzo nel flusso di esecuzione di un programma.

## <a name="syntax"></a>Sintassi

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per correlare la posizione di un'istruzione del codice a una posizione del documento.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi su molte interfacce restituiscono questa interfaccia, in genere [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Viene anche usato ampiamente con l'interfaccia [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) , oltre che con le informazioni di risoluzione del punto di interruzione.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi sull'interfaccia [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ottiene il contesto del documento che corrisponde al contesto del codice attivo.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ottiene le informazioni sulla lingua per questo contesto del codice.|

## <a name="remarks"></a>Commenti
 La differenza principale tra un' `IDebugCodeContext2` interfaccia e un'interfaccia [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) è che un `IDebugCodeContext2` è sempre allineato all'istruzione. Ciò significa che un oggetto `IDebugCodeContext2` sta sempre puntando all'inizio di un'istruzione, mentre un `IDebugMemoryContext2` può puntare a qualsiasi byte di memoria nell'architettura di run-time. `IDebugCodeContext2` viene incrementato in base alle istruzioni anziché alle dimensioni di archiviazione di base (in genere byte).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
