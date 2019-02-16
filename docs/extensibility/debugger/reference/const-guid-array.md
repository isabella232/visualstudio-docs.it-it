---
title: CONST_GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40511cac0a6d731d451d1fb2e0e4c02d214297f7
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318537"
---
# <a name="constguidarray"></a>CONST_GUID_ARRAY
Una struttura che contiene un elenco di `GUID`s.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagCONST_GUID_ARRAY {
    DWORD       dwCount;
    CONST GUID* Members;
} CONST_GUID_ARRAY;
```

```csharp
public struct CONST_GUID_ARRAY {
    public uint   dwCount;
    public Guid[] Members;
}
```

## <a name="members"></a>Membri
dwCount  
Numerosi `GUID`s nel `Members` matrice.

Membri  
Matrice di `GUID`s.

## <a name="remarks"></a>Note
Questa struttura viene passata al [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) metodo e viene restituito dalle [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) e [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) metodi.

Il proprietario di un'istanza di questa struttura è responsabile della liberazione di memoria allocata.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)  
[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)  
[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
