---
title: Proprietà IDebugQueryEngine2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720660"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Questa interfaccia consente al gestore di sessione di debug (SDM) recuperare un'interfaccia che rappresenta il motore di debug (DE).

## <a name="syntax"></a>Sintassi

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia sugli oggetti che implementano le interfacce DE più comuni (ad esempio [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)e [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) per consentire l'accesso all'interfaccia [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) del DE stesso.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su una tipica interfaccia DE per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugQueryEngine2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ottiene un'interfaccia personalizzata del motore di debug (DE).|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia viene in genere implementata nell'oggetto che implementa il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per supportare le funzioni di esecuzione passo passo ordinata causalità ordinata; vale a dire, quando il debugger esce da una funzione, la funzione successiva da eseguire potrebbe non essere la funzione precedente nello stack, ma una funzione in un altro thread del tutto. Per una definizione di "causalità", vedere il [Glossario del debugger di Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
