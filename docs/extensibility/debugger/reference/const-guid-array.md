---
description: Struttura che contiene un elenco di GUID.
title: CONST_GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c69f45ea0ef67ee388db719dc07360c51e53bfbff82af37661750cd46b966483
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360924"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
Struttura che contiene un elenco di `GUID` .

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagCONST_GUID_ARRAY {
    DWORD       dwCount;
    CONST GUID* Members;
} CONST_GUID_ARRAY;
```

```csharp
public struct CONST_GUID_ARRAY {
    public uint   dwCount;
    public Guid[] Members;
}
```

## <a name="members"></a>Members
`dwCount`\
Numero di `GUID` s nella `Members` matrice.

`Members`\
Matrice di `GUID` s.

## <a name="remarks"></a>Commenti
Questa struttura viene passata [al metodo PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) e viene restituita dai [metodi GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) e [WatchForProviderEvents.](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

Il proprietario di un'istanza di questa struttura è responsabile della liberatura della memoria allocata.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
