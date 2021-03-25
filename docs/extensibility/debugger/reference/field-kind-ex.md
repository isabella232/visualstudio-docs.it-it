---
description: Enumera i tipi aggiuntivi di campi che possono essere contenuti in un oggetto IDebugField.
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75c1839987901edc9bc3571fa303ca0d3218a53c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059392"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
Enumera i tipi aggiuntivi di campi che possono essere contenuti in un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Questa enumerazione estende l'enumerazione [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) .

## <a name="syntax"></a>Sintassi

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>Campi
`FIELD_KIND_EX_NONE`\
Il campo non contiene un tipo esteso.

`FIELD_TYPE_EX_METHODVAR`\
Il campo contiene una variabile di metodo.

`FIELD_TYPE_EX_CLASSVAR`\
Il campo contiene una variabile di classe.

## <a name="requirements"></a>Requisiti
Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
