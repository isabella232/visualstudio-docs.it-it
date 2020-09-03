---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738109"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Specifica lo stile della condizione del punto di interruzione per i punti di interruzione in sospeso e associati.

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
Genera il punto di interruzione quando viene raggiunta la posizione del punto di interruzione. Non è stata specificata alcuna condizione del punto di interruzione.

`BP_COND_WHEN_TRUE`\
Genera il punto di interruzione solo quando l'espressione condizionale associata al punto di interruzione restituisce `true` .

`BP_COND_WHEN_CHANGED`\
Genera il punto di interruzione solo quando il valore dell'espressione condizionale associato al punto di interruzione è stato modificato rispetto alla valutazione precedente.

## <a name="remarks"></a>Osservazioni
Utilizzato per il `styleCondition` membro della struttura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
