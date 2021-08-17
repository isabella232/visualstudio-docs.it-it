---
description: Questa interfaccia rappresenta una singola stack frame in uno stack di chiamate in un thread specifico.
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 69bb2e2f58393311b0867a7ea684b99a8df51676
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029671"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Questa interfaccia rappresenta una singola stack frame in uno stack di chiamate in un thread specifico.

## <a name="syntax"></a>Sintassi

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare un stack frame.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per recuperare [un'interfaccia IEnumDebugFrameInfo2.](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Chiamare [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) per recuperare una [struttura FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) che contiene l'interfaccia `IDebugStackFrame2` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugStackFrame2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ottiene il contesto del codice per questo stack frame.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto del documento per questo stack frame.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ottiene il nome dell'stack frame.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ottiene una descrizione dell'stack frame.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ottiene una rappresentazione dipendente dal computer dell'intervallo di indirizzi fisici associati a un stack frame.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ottiene un contesto di valutazione per eseguire la valutazione dell'espressione all'interno del contesto corrente di un stack frame thread.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ottiene la lingua associata a un stack frame.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ottiene una descrizione delle proprietà associate a un stack frame.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crea un enumeratore per stack frame proprietà.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ottiene il thread associato a un stack frame.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene ottenuta solo quando il programma in fase di debug è stato arrestato in corrispondenza di un punto di interruzione (causato da un punto di interruzione impostato dall'utente o da un'eccezione). Da questa interfaccia è possibile ottenere un contesto di espressione per valutare le espressioni, restituire un elenco di registri oppure ottenere ed esaminare lo stack di chiamate.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
