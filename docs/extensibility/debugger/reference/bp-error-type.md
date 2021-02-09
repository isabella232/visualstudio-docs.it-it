---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b67b28c61624b73787dabe9fd24c4c39ff9b3c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853052"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Specifica il tipo di errore di un punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Campi
`BPET_NONE`\
Non specifica alcun errore del punto di interruzione.

`BPET_TYPE_WARNING`\
Specifica un errore di interruzione dello stile di avviso.

`BPET_TYPE_ERROR`\
Specifica un errore di interruzione dello stile di errore.

`BPET_SEV_HIGH`\
Specifica un errore di interruzione della gravità elevata.

`BPET_SEV_GENERAL`\
Specifica un errore di punto di interruzione di gravità medio.

`BPET_SEV_LOW`\
Specifica un errore di punto di interruzione di gravità basso.

`BPET_TYPE_MASK`\
Specifica un errore del punto di interruzione in stile maschera.

`BPET_SEV_MASK`\
Specifica un errore di interruzione del punto di interruzione dello stile della maschera di gravità.

`BPET_GENERAL_WARNING`\
Specifica un errore di punto di interruzione generale in stile avviso.

`BPET_GENERAL_ERROR`\
Specifica un errore di interruzione generale di tipo errore.

`BPET_ALL`\
Specifica tutti i tipi di errore del punto di interruzione.

## <a name="remarks"></a>Commenti
Questi valori possono essere combinati con un operatore `OR` and bit per bit utilizzati per il `dwType` membro della struttura [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) . Passato come parametro al metodo [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .

Un tipo di errore del punto di interruzione è costituito da un tipo e da una gravità. Questo significa che un tipo di errore del punto di interruzione non è mai solo un tipo (ad esempio, `BPET_TYPE_ERROR` ) o un livello di gravità (ad esempio, `BPET_SEV_GENERAL` ). `BPET_GENERAL_WARNING` e `BPET_GENERAL_ERROR` forniscono valori predefiniti per i punti di interruzione di avviso e di errore generali.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
