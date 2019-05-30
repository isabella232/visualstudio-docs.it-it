---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f31b33eeb782e71a87103d26a3bb78175611644e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318138"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
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
Trovare il primo contesto del documento nell'elenco che è uguale al contesto di documento di destinazione.

`DOCCONTEXT_LESS_THAN`\
Trovare il primo contesto del documento nell'elenco che è minore rispetto al contesto di documento di destinazione.

`DOCCONTEXT_GREATER_THAN`\
Trovare il primo contesto del documento nell'elenco che è maggiore rispetto al contesto di documento di destinazione.

`DOCCONTEXT_SAME_DOCUMENT`\
Trovare il primo contesto del documento nell'elenco che è nello stesso documento come contesto di documento di destinazione.

## <a name="remarks"></a>Note
Passato come argomento per il [confrontare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) (metodo).

Questi valori vengono utilizzati per specificare un criterio di confronto per trovare il primo contesto del documento in un elenco. Un contesto di documento viene fornito un elenco di contesti di documento di confrontarsi con tramite il `IDebugDocumentContext2::Compare` (metodo). Il contesto del documento prima nell'elenco per il quale l'operatore di confronto è `true` viene quindi restituito.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
