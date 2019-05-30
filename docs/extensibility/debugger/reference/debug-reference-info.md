---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c22ab1a7d0cb03f66455f76c1d9878a9df76604e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346140"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
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
Una combinazione di flag dal [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumerazione che specifica quali campi vengono compilati.

`bstrName`\
Il nome specificato dall'utente del [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto.

`bstrType`\
Il tipo di riferimento sotto forma di stringa formattata.

`bstrValue`\
Il valore di riferimento sotto forma di stringa formattata

`dwAttrib`\
Una combinazione di flag dal [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumerazione che specifica i flag per gli attributi della proprietà di debug.

`dwRefType`\
Un valore compreso il [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) enumerazione che specifica se il tipo di riferimento è forte o debole.

`m_pReference`\
Un' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che specifica le informazioni di riferimento.

## <a name="remarks"></a>Note
Questa struttura viene passata a una chiamata per il [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metodo da compilare. Questa struttura viene anche restituita come parte di un elenco dal [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) interfaccia che, a sua volta, viene restituito da una chiamata ai [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) (metodo).

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
