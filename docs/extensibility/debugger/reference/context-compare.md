---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35c68d2be2179b3bbcb1b3c691deb42cd8e8414f
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412838"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
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

## <a name="members"></a>Membri
CONTEXT_EQUAL  
Trovare il primo contesto di memoria nell'elenco uguale al contesto di destinazione di memoria.

CONTEXT_LESS_THAN  
Trovare il primo contesto di memoria nell'elenco che è minore rispetto al contesto di memoria di destinazione.

CONTEXT_GREATER_THAN  
Trovare il primo contesto di memoria nell'elenco che è maggiore rispetto al contesto di memoria di destinazione.

CONTEXT_LESS_THAN_OR_EQUAL  
Trovare il primo contesto di memoria nell'elenco che è minore o uguale al contesto di destinazione di memoria.

CONTEXT_GREATER_THAN_OR_EQUAL  
Trovare il primo contesto di memoria nell'elenco che è maggiore o uguale al contesto di destinazione di memoria.

CONTEXT_SAME_SCOPE  
Trovare il primo contesto di memoria nell'elenco che è nello stesso ambito il contesto di memoria di destinazione.

CONTEXT_SAME_FUNCTION  
Trovare il primo contesto di memoria nell'elenco che è la stessa funzione dell'ambito della memoria di destinazione.

CONTEXT_SAME_MODULE  
Trovare il primo contesto di memoria nell'elenco che è nello stesso modulo del contesto di destinazione di memoria.

CONTEXT_SAME_PROCESS  
Trovare il primo contesto di memoria nell'elenco che è nello stesso processo come contesto di memoria di destinazione.

## <a name="remarks"></a>Note
Passato come argomento per il [confrontare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) (metodo).

Questi valori vengono usati per trovare il primo contesto di memoria in un elenco che soddisfa i criteri di confronto specificate. Un contesto in memoria viene assegnato un elenco di contesti di memoria di confrontarsi con tramite il `IDebugMemoryContext2::Compare` (metodo). Il primo contesto di memoria nell'elenco per il quale l'operatore di confronto è `true` viene quindi restituito.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
