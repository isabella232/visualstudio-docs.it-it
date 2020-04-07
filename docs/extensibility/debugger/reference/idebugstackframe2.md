---
title: Proprietà IDebugStackFrame2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719506"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Questa interfaccia rappresenta un singolo stack frame in uno stack di chiamate in un thread specifico.

## <a name="syntax"></a>Sintassi

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare uno stack frame.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per recuperare un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaccia. Chiamare [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) per recuperare una struttura `IDebugStackFrame2` [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) che contiene l'interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugStackFrame2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ottiene il contesto del codice per questo stack frame.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto del documento per questo stack frame.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ottiene il nome dello stack frame.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ottiene una descrizione dello stack frame.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ottiene una rappresentazione dipendente dal computer dell'intervallo di indirizzi fisici associati a uno stack frame.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ottiene un contesto di valutazione per l'esecuzione della valutazione dell'espressione nel contesto corrente di uno stack frame e un thread.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ottiene la lingua associata a uno stack frame.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ottiene una descrizione delle proprietà associate a uno stack frame.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crea un enumeratore per le proprietà dello stack frame.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ottiene il thread associato a uno stack frame.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia viene ottenuta solo quando il programma in fase di debug è stato arrestato in corrispondenza di un punto di interruzione (causato da un punto di interruzione impostato dall'utente o da un'eccezione). Da questa interfaccia è possibile ottenere un contesto di espressione per valutare le espressioni, restituire un elenco di registri o ottenere ed esaminare lo stack di chiamate.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
