---
title: proprietà CONTEXT_COMPARE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737613"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Specifica i criteri per il confronto di due contesti di memoria.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Campi
`CONTEXT_EQUAL`\
Trovare il primo contesto di memoria nell'elenco che è uguale al contesto di memoria di destinazione.

`CONTEXT_LESS_THAN`\
Trovare il primo contesto di memoria nell'elenco che è minore del contesto di memoria di destinazione.

`CONTEXT_GREATER_THAN`\
Trovare il primo contesto di memoria nell'elenco maggiore del contesto di memoria di destinazione.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Trovare il primo contesto di memoria nell'elenco che è minore o uguale al contesto di memoria di destinazione.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Trovare il primo contesto di memoria nell'elenco maggiore o uguale al contesto di memoria di destinazione.

`CONTEXT_SAME_SCOPE`\
Trovare il primo contesto di memoria nell'elenco che si trova nello stesso ambito del contesto di memoria di destinazione.

`CONTEXT_SAME_FUNCTION`\
Trovare il primo contesto di memoria nell'elenco che si trova nella stessa funzione dell'ambito di memoria di destinazione.

`CONTEXT_SAME_MODULE`\
Trovare il primo contesto di memoria nell'elenco che si trova nello stesso modulo del contesto di memoria di destinazione.

`CONTEXT_SAME_PROCESS`\
Trovare il primo contesto di memoria nell'elenco che si trova nello stesso processo del contesto di memoria di destinazione.

## <a name="remarks"></a>Osservazioni
Passato come argomento per il [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) metodo.

Questi valori vengono utilizzati per trovare il primo contesto di memoria in un elenco che soddisfa i criteri di confronto specificati. A un contesto di memoria viene fornito un `IDebugMemoryContext2::Compare` elenco di contesti di memoria con cui confrontarsi tramite il metodo . Primo contesto di memoria nell'elenco `true` per il quale viene restituito l'operatore di confronto.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Confronta](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
