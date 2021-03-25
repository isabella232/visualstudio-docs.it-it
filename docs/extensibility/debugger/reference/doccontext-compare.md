---
description: Specifica i criteri per il confronto di due contesti di documento.
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6eeee3e31c898660930b676df716fe25769bbb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096005"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Specifica i criteri per il confronto di due contesti di documento.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Campi
`DOCCONTEXT_EQUAL`\
Trovare il primo contesto del documento nell'elenco uguale al contesto del documento di destinazione.

`DOCCONTEXT_LESS_THAN`\
Trovare il primo contesto del documento nell'elenco inferiore al contesto del documento di destinazione.

`DOCCONTEXT_GREATER_THAN`\
Trovare il primo contesto del documento nell'elenco maggiore del contesto del documento di destinazione.

`DOCCONTEXT_SAME_DOCUMENT`\
Trovare il primo contesto del documento nell'elenco che si trova nello stesso documento del contesto del documento di destinazione.

## <a name="remarks"></a>Commenti
Passato come argomento al metodo [compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .

Questi valori vengono utilizzati per specificare un criterio di confronto per individuare il primo contesto del documento in un elenco. A un contesto del documento viene assegnato un elenco di contesti di documenti da confrontare con il `IDebugDocumentContext2::Compare` metodo. Viene quindi restituito il primo contesto del documento nell'elenco per il quale viene restituito l'operatore di confronto `true` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Confronta](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
