---
description: Descrive il conteggio e le condizioni in base alle quali viene attivato un punto di interruzione condizionale.
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca17b821cc5cedb38ec3405404921a5d759018b80ce313f06a0dc6b20768279a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417626"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Descrive il conteggio e le condizioni in base alle quali viene attivato un punto di interruzione condizionale.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Members
`dwPassCount`\
Numero di volte in cui passare il punto di interruzione prima di generarlo.

`stylePassCount`\
Valore dell'enumerazione [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) che specifica lo stile del conteggio dei passaggi del punto di interruzione.

## <a name="remarks"></a>Commenti
Questa struttura è un membro della [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struttura .

Questa struttura viene anche passata come parametro ai[metodi SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) [e SetPassCount.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
