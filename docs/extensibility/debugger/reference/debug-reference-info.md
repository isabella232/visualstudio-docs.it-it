---
description: Descrive un riferimento.
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6eb81c3ca39155a797682afa891fcabe4bae26e56373499cf46cf0e03903bb83
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360833"
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

## <a name="members"></a>Members
`dwFields`\
Combinazione di flag [dell'DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) che specifica quali campi vengono compilati.

`bstrName`\
Nome dell'oggetto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) specificato dall'utente.

`bstrType`\
Tipo di riferimento come stringa formattata.

`bstrValue`\
Valore di riferimento come stringa formattata

`dwAttrib`\
Combinazione di flag [dell'enumerazione DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) che specifica i flag per gli attributi della proprietà di debug.

`dwRefType`\
Valore [dell'enumerazione REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) che specifica se il tipo di riferimento è sicuro o debole.

`m_pReference`\
Oggetto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che specifica le informazioni di riferimento.

## <a name="remarks"></a>Commenti
Questa struttura viene passata a una chiamata [al metodo GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) da completare. Questa struttura viene restituita anche come parte di un elenco dall'interfaccia [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) che, a sua volta, viene restituita da una chiamata al [metodo EnumChildren.](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
