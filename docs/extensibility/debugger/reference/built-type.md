---
description: La BUILT_TYPE specifica informazioni su un tipo di campo derivato dai metadati.
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3179ea403cd542a54d4b4a5e0a10776daa87b76f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635156"
---
# <a name="built_type"></a>BUILT_TYPE
Questa struttura specifica informazioni su un tipo di campo tratto dai metadati.

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

## <a name="members"></a>Members
`ulAppDomainID`\
ID dell'applicazione da cui deriva il simbolo. Viene usato per identificare in modo univoco un'istanza dell'applicazione.

`guidModule`\
GUID del modulo che contiene questo campo.

`pUnderlyingField`\
Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che identifica il campo sottostante associato a questo campo compilato.

## <a name="remarks"></a>Commenti
Questa struttura viene visualizzata come parte dell'unione nella struttura TYPE_INFO [quando](../../../extensibility/debugger/reference/type-info.md) il campo della struttura è impostato su (un valore dell'enumerazione dwTYPE_KIND `dwKind` di `TYPE_INFO` `TYPE_KIND_BUILT` dati). [](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
