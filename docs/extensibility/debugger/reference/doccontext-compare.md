---
description: Specifica i criteri per confrontare due contesti di documento.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3329c805ab1e5f6f45f82a2789fdec242c83931f18e525a50fd883f3601c63da
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360820"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Specifica i criteri per confrontare due contesti di documento.

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
Trovare nell'elenco il primo contesto del documento uguale al contesto del documento di destinazione.

`DOCCONTEXT_LESS_THAN`\
Trovare nell'elenco il primo contesto del documento minore del contesto del documento di destinazione.

`DOCCONTEXT_GREATER_THAN`\
Trovare il primo contesto del documento nell'elenco maggiore del contesto del documento di destinazione.

`DOCCONTEXT_SAME_DOCUMENT`\
Trovare il primo contesto del documento nell'elenco che si trova nello stesso documento del contesto del documento di destinazione.

## <a name="remarks"></a>Commenti
Passato come argomento al [metodo Compare.](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

Questi valori vengono usati per specificare criteri di confronto per trovare il primo contesto di documento in un elenco. A un contesto di documento viene fornito un elenco di contesti di documento con cui confrontarsi tramite il `IDebugDocumentContext2::Compare` metodo . Viene quindi restituito il primo contesto del documento nell'elenco per il quale viene restituito `true` l'operatore di confronto.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Confronta](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
