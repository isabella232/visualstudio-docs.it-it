---
description: Specifica i criteri per confrontare due contesti di memoria.
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49c8975a93d54d9138cbdcf510e7ee18d5bc55d2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145614"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Specifica i criteri per confrontare due contesti di memoria.

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
Trovare nell'elenco il primo contesto di memoria uguale al contesto di memoria di destinazione.

`CONTEXT_LESS_THAN`\
Trovare nell'elenco il primo contesto di memoria minore del contesto di memoria di destinazione.

`CONTEXT_GREATER_THAN`\
Trovare nell'elenco il primo contesto di memoria maggiore del contesto di memoria di destinazione.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Trovare nell'elenco il primo contesto di memoria minore o uguale al contesto di memoria di destinazione.

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

## <a name="remarks"></a>Commenti
Passato come argomento al [metodo Compare.](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)

Questi valori vengono usati per trovare il primo contesto di memoria in un elenco che soddisfa i criteri di confronto specificati. A un contesto di memoria viene fornito un elenco di contesti di memoria con cui confrontarsi tramite il `IDebugMemoryContext2::Compare` metodo . Viene quindi restituito il primo contesto di memoria nell'elenco per il quale viene restituito `true` l'operatore di confronto.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Confronta](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
