---
description: Specifica la condizione associata al numero di passaggi del punto di interruzione che causa l'avvio del punto di interruzione.
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02aae6a4ef4939660639004602b539b0f68c4fa2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145913"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Specifica la condizione associata al numero di passaggi del punto di interruzione che causa l'avvio del punto di interruzione.

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
Non specifica lo stile di conteggio dei passaggi del punto di interruzione.

`BP_PASSCOUNT_EQUAL`\
Imposta lo stile di conteggio dei passaggi del punto di interruzione su uguale. Il punto di interruzione viene generato quando il numero di volte in cui viene raggiunto il punto di interruzione è uguale al numero di passaggi.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Imposta lo stile di conteggio dei passaggi del punto di interruzione su uguale o maggiore. Il punto di interruzione viene generato quando il numero di volte in cui viene raggiunto il punto di interruzione è uguale o maggiore del numero di passaggi.

`BP_PASSCOUNT_MOD`\
Specifica un conteggio delle passate modulo. Ad esempio, se il numero di passaggi è di tipo e il valore del numero di passaggi è 4, il punto di interruzione viene generato ogni volta che il numero di passaggi è `BP_PASSCOUNT_MOD` un multiplo di 4.

## <a name="remarks"></a>Commenti
Usato per il membro della struttura BP_PASSCOUNT che a sua volta è un membro delle strutture BP_REQUEST_INFO `stylePassCount` e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md) [](../../../extensibility/debugger/reference/bp-passcount.md) [](../../../extensibility/debugger/reference/bp-request-info.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
