---
description: Specifica la condizione associata al numero di passaggi del punto di interruzione che determina l'attivazione del punto di interruzione.
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e216b61d6fed41571baa7f68201d96f84532fc3a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144169"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Specifica la condizione associata al numero di passaggi del punto di interruzione che determina l'attivazione del punto di interruzione.

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
Non specifica alcuno stile di conteggio passaggi del punto di interruzione.

`BP_PASSCOUNT_EQUAL`\
Imposta lo stile del conteggio pass per il punto di interruzione su uguale. Il punto di interruzione viene attivato quando il numero di volte in cui viene raggiunto il punto di interruzione è uguale al numero di passaggi.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Imposta lo stile del conteggio pass per il punto di interruzione su uguale o maggiore. Il punto di interruzione viene attivato quando il numero di volte in cui viene raggiunto il punto di interruzione è maggiore o uguale al numero di passaggi.

`BP_PASSCOUNT_MOD`\
Specifica un numero di passaggi modulo. Se, ad esempio, il numero di passaggi è del tipo `BP_PASSCOUNT_MOD` e il valore del numero di passaggi è 4, il punto di interruzione viene attivato ogni volta che il numero di passaggi è un multiplo di 4.

## <a name="remarks"></a>Commenti
Utilizzato per il `stylePassCount` membro della struttura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) che è a sua volta un membro delle strutture [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
