---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e20db594fcc00f641634bfaae8d5342d4b520d7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337431"
---
# <a name="bpcondition"></a>BP_CONDITION
Descrive le condizioni in cui viene attivato un punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Membri
`pThread`\
Il [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread attivo per l'applicazione che contiene il punto di interruzione.

`styleCondition`\
Un valore compreso il [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) enumerazione che indica lo stile di questa condizione di punto di interruzione.

`bstrContext`\
La posizione del punto di interruzione.

`bstrCondition`\
La condizione di attivazione del punto di interruzione.

`nRadix`\
Radice da usare nella valutazione di tutte le informazioni numeriche.

## <a name="remarks"></a>Note
Questa struttura è un membro del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.

Questa struttura viene anche passata come parametro per il [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) e [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) metodi.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
