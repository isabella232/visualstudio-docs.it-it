---
title: proprietà DEBUG_REFERENCE_INFO . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737409"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Descrive un riferimento.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Membri
`dwFields`\
Combinazione di flag dell'enumerazione [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) che specifica quali campi vengono compilati.

`bstrName`\
Nome specificato dall'utente dell'oggetto [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

`bstrType`\
Tipo di riferimento come stringa formattata.

`bstrValue`\
Il valore di riferimento come stringa formattata

`dwAttrib`\
Combinazione di flag dell'enumerazione [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) che specifica i flag per gli attributi della proprietà di debug.

`dwRefType`\
Valore dell'enumerazione [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) che specifica se il tipo di riferimento è forte o debole.

`m_pReference`\
Oggetto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che specifica le informazioni di riferimento.

## <a name="remarks"></a>Osservazioni
Questa struttura viene passata a una chiamata al [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metodo da compilare. Questa struttura viene restituita anche come parte di un elenco dal [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) interfaccia che, a sua volta, viene restituito da una chiamata al [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) metodo.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
