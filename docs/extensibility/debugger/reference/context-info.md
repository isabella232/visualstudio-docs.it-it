---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c41a155fb3a85bcb9f0b0e5eae461f2ae172c7e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709980"
---
# <a name="contextinfo"></a>CONTEXT_INFO
Questa struttura descrive un contesto in memoria o il contesto del codice.

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

## <a name="members"></a>Membri
Una combinazione di flag da egli dwFields [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumerazione che specifica quali campi vengono compilati<strong>.</strong>

bstrModuleUrl il nome del modulo in cui si trova il contesto.

bstrFunction il nome della funzione in cui si trova il contesto.

Oggetto posFunctionOffset [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che identifica l'offset di riga e alla colonna della funzione associata al contesto del codice.

bstrAddress l'indirizzo nel codice in cui si trova nel contesto specificato.

bstrAddressOffset l'offset dell'indirizzo nel codice in cui si trova nel contesto specificato.

bstrAddressAbsolute indirizzo assoluto nella memoria in cui si trova nel contesto specificato.

## <a name="remarks"></a>Note
Questa struttura viene restituita da una chiamata per il [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) (metodo).

Un utilizzo tipico per questa struttura è supportare una **memoria** finestra di debug.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
