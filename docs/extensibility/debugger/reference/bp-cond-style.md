---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70ab3655d27e810b3c05d0e0e81d81bc15a26950
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685859"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Specifica lo stile di condizione punto di interruzione per in sospeso e associati i punti di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="members"></a>Membri
BP_COND_NONE viene attivato il punto di interruzione quando la posizione del punto di interruzione viene raggiunto. Nessuna condizione di punto di interruzione specificati.

BP_COND_WHEN_TRUE viene attivato il punto di interruzione solo quando il punto di interruzione associata l'espressione condizionale restituisce `true`.

BP_COND_WHEN_CHANGED viene attivato il punto di interruzione solo quando il valore dell'espressione condizionale associato il punto di interruzione è stato modificato da relativo valutazione precedente.

## <a name="remarks"></a>Note
Utilizzato per il `styleCondition` membro della [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struttura.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
