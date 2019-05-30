---
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fd1ab73a20b319af6c9464062113f4e8f2d64fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353015"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
Descrive il numero e le condizioni in cui viene attivato un punto di interruzione condizionale.

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

## <a name="members"></a>Membri
`dwPassCount`\
Il numero di volte in cui passa sopra il punto di interruzione prima che venga attivata.

`stylePassCount`\
Un valore compreso il [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) conteggio esecuzioni di test di enumerazione che specifica lo stile del punto di interruzione.

## <a name="remarks"></a>Note
Questa struttura è un membro del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struttura.

Questa struttura viene anche passata come parametro per il[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) e[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) metodi.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
