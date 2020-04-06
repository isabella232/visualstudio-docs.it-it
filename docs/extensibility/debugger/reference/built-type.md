---
title: proprietà BUILT_TYPE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737693"
---
# <a name="built_type"></a>BUILT_TYPE
Questa struttura specifica le informazioni su un tipo di campo derivato dai metadati.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Membri
`ulAppDomainID`\
ID dell'applicazione da cui proveniva il simbolo. Viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.

`guidModule`\
GUID del modulo che contiene questo campo.

`pUnderlyingField`\
Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che identifica il campo sottostante associato a questo campo compilato.

## <a name="remarks"></a>Osservazioni
Questa struttura viene visualizzata come parte dell'unione `TYPE_INFO` nella struttura `TYPE_KIND_BUILT` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il `dwKind` campo della struttura è impostato su (un valore dell'enumerazione [dwTYPE_KIND).](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
