---
description: Descrive le condizioni in cui viene generato un punto di interruzione.
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8def7604362e7c1b84adf55dad8a9e10e31e7bb09331e24730e9abbcffcdbccb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342700"
---
# <a name="bp_condition"></a>BP_CONDITION
Descrive le condizioni in cui viene generato un punto di interruzione.

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

## <a name="members"></a>Members
`pThread`\
Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread attivo per l'applicazione che contiene il punto di interruzione.

`styleCondition`\
Valore dell'enumerazione [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) che descrive lo stile di questa condizione del punto di interruzione.

`bstrContext`\
Posizione del punto di interruzione.

`bstrCondition`\
Condizione di attivazione del punto di interruzione.

`nRadix`\
Radice da usare nella valutazione di qualsiasi informazione numerica.

## <a name="remarks"></a>Commenti
Questa struttura è un membro delle [strutture](../../../extensibility/debugger/reference/bp-request-info.md) BP_REQUEST_INFO e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Questa struttura viene passata anche come parametro ai [metodi SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) [e SetCondition.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
