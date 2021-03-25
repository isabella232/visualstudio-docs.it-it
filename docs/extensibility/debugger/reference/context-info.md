---
description: Questa struttura descrive un contesto di memoria o un contesto di codice.
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58b524de5d2d230e240ae7338190568ccfe6fb2a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096486"
---
# <a name="context_info"></a>CONTEXT_INFO
Questa struttura descrive un contesto di memoria o un contesto di codice.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Members
`dwFields`\
Combinazione di flag di [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumerazione che specifica i campi che vengono compilati<strong>.</strong>

`bstrModuleUrl`\
Nome del modulo in cui si trova il contesto.

`bstrFunction`\
Nome della funzione in cui si trova il contesto.

`posFunctionOffset`\
Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che identifica l'offset di riga e di colonna della funzione associata al contesto del codice.

`bstrAddress`\
Indirizzo nel codice in cui si trova il contesto specificato.

`bstrAddressOffset`\
Offset dell'indirizzo nel codice in cui si trova il contesto specificato.

`bstrAddressAbsolute`\
Indirizzo assoluto in memoria in cui si trova il contesto specificato.

## <a name="remarks"></a>Commenti
Questa struttura viene restituita da una chiamata al metodo [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) .

Un uso tipico di questa struttura è il supporto di una finestra di debug della **memoria** .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
