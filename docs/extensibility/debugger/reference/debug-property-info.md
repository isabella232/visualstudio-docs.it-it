---
description: Contiene informazioni su una proprietà di debug.
title: DEBUG_PROPERTY_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bd2526853dd5c0c3bb84bdc7d00c76805dd28a1118b4a35b8d173b17ab9bde3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452394"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Contiene informazioni su una proprietà di debug.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Members
`dwValidFields`\
Combinazione di flag [dell'enumerazione DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) che specifica quali campi vengono compilati.

`bstrFullName`\
Nome completo della proprietà.

`bstrName`\
Nome della proprietà all'interno di un contesto.

`bstrType`\
Tipo di proprietà come stringa formattata.

`bstrValue`\
Valore della proprietà come stringa formattata.

`pProperty`\
Oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) descritto da questa struttura.

`dwAttrib`\
Combinazione di flag [dell'enumerazione DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) che descrivono gli attributi di questa proprietà.

## <a name="remarks"></a>Commenti
Una proprietà è un oggetto di natura gerarchica con un nome, un tipo e un valore. Ad esempio, una proprietà può descrivere variabili locali, parametri, variabili di espressione di controllo ed espressioni e registri.

Questa struttura viene passata [al metodo GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) dove viene compilata. Questa struttura viene restituita anche come parte di un elenco di questa struttura dall'interfaccia [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) che, a sua volta, viene restituita da una chiamata ai [metodi EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) ed [EnumProperties.](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
