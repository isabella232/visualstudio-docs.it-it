---
title: DOCCONTEXT_COMPARE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737225"
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
Trovare il primo contesto del documento nell'elenco che è uguale al contesto del documento di destinazione.

`DOCCONTEXT_LESS_THAN`\
Trovare il primo contesto del documento nell'elenco che è minore del contesto del documento di destinazione.

`DOCCONTEXT_GREATER_THAN`\
Trovare il primo contesto del documento nell'elenco maggiore del contesto del documento di destinazione.

`DOCCONTEXT_SAME_DOCUMENT`\
Trovare il primo contesto del documento nell'elenco che si trova nello stesso documento del contesto del documento di destinazione.

## <a name="remarks"></a>Osservazioni
Passato come argomento per il [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) metodo.

Questi valori vengono utilizzati per specificare un criterio di confronto per trovare il primo contesto del documento in un elenco. A un contesto di documento viene fornito un `IDebugDocumentContext2::Compare` elenco di contesti di documento con cui confrontarsi tramite il metodo . Contesto del primo documento nell'elenco `true` per il quale viene restituito l'operatore di confronto.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Confronta](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
