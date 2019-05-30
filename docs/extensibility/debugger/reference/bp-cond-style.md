---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ded3d31f9be2d0a02a238ead4bc989cc21b4922a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351822"
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

## <a name="fields"></a>Campi
`BP_COND_NONE`\
Quando viene raggiunta la posizione del punto di interruzione, viene attivato il punto di interruzione. Nessuna condizione di punto di interruzione specificati.

`BP_COND_WHEN_TRUE`\
Viene attivato il punto di interruzione solo quando il punto di interruzione associata l'espressione condizionale restituisce `true`.

`BP_COND_WHEN_CHANGED`\
Viene attivato il punto di interruzione solo quando il valore dell'espressione condizionale associato il punto di interruzione è stato modificato da relativo valutazione precedente.

## <a name="remarks"></a>Note
Utilizzato per il `styleCondition` membro della [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struttura.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
