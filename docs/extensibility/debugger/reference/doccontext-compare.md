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
ms.openlocfilehash: 766f745a88e178a82627ed24da761dec4560989e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104638"
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
Trovare il primo contesto del documento nell'elenco uguale al contesto del documento di destinazione.

`DOCCONTEXT_LESS_THAN`\
Trovare il primo contesto del documento nell'elenco minore del contesto del documento di destinazione.

`DOCCONTEXT_GREATER_THAN`\
Trovare il primo contesto del documento nell'elenco maggiore del contesto del documento di destinazione.

`DOCCONTEXT_SAME_DOCUMENT`\
Trovare il primo contesto del documento nell'elenco che si trova nello stesso documento del contesto del documento di destinazione.

## <a name="remarks"></a>Commenti
Passato come argomento al [metodo Compare.](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

Questi valori vengono usati per specificare criteri di confronto per trovare il primo contesto del documento in un elenco. A un contesto di documento viene assegnato un elenco di contesti di documento con cui confrontarsi tramite il `IDebugDocumentContext2::Compare` metodo . Primo contesto del documento nell'elenco per il quale viene quindi restituito l'operatore `true` di confronto.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Confronta](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
