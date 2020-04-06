---
title: BP_PASSCOUNT_STYLE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737924"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Specifica la condizione associata al numero di passaggi del punto di interruzione che causa l'accensimento del punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Campi
`BP_PASSCOUNT_NONE`\
Non specifica alcuno stile di conteggio dei passaggi del punto di interruzione.

`BP_PASSCOUNT_EQUAL`\
Imposta lo stile del numero di passaggi del punto di interruzione su uguale. Il punto di interruzione viene generato quando il numero di volte in cui il punto di interruzione viene raggiunto è uguale al numero di passaggi.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Imposta lo stile del numero di passaggi del punto di interruzione su uguale o maggiore. Il punto di interruzione viene generato quando il numero di volte in cui viene raggiunto il punto di interruzione è uguale o maggiore del numero di passaggi.

`BP_PASSCOUNT_MOD`\
Specifica un conteggio dei passaggi modulo. Ad esempio, se il numero `BP_PASSCOUNT_MOD` di passaggi è del tipo e il valore del numero di passaggi è 4, il punto di interruzione viene attivato ogni volta che il numero di passaggi è un multiplo di 4.

## <a name="remarks"></a>Osservazioni
Utilizzato per `stylePassCount` il membro della struttura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) che a sua volta è un membro della [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
