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
ms.openlocfilehash: 81b18a6e238b71a7c91445b551beb34dd081e53c24b5301cd58c495a04e1e733
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360963"
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

## <a name="members"></a>Members
`ulAppDomainID`\
ID dell'applicazione da cui deriva il simbolo. Viene usato per identificare in modo univoco un'istanza dell'applicazione.

`guidModule`\
GUID del modulo che contiene questo campo.

`pUnderlyingField`\
Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che identifica il campo sottostante associato a questo campo compilato.

## <a name="remarks"></a>Commenti
Questa struttura viene visualizzata come parte dell'unione nella struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il campo della struttura è impostato su (un valore `dwKind` dell'enumerazione `TYPE_INFO` `TYPE_KIND_BUILT` [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) tabella).

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
