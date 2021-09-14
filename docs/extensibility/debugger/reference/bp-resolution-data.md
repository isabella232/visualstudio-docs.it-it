---
description: Descrive il risultato dell'associazione di un punto di interruzione dati.
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e82ede309d0483dfc406dc54444975ae4cc8afa9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635235"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Descrive il risultato dell'associazione di un punto di interruzione dati.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Members
`bstrDataExpr`\
Espressione di dati associata.

`bstrFunc`\
Nome della funzione a cui è associato il punto di interruzione dati (se presente).

`bstrImage`\
Nome del modulo (ad esempio MyModule.dll) a cui è associato il punto di interruzione dati.

`dwFlags`\
Valore dell'enumerazione [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) che descrive come viene implementato il punto di interruzione dei dati.

## <a name="remarks"></a>Commenti
Questa struttura è un membro della [struttura BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) che a sua volta è un membro della struttura BP_RESOLUTION_INFO [restituita](../../../extensibility/debugger/reference/bp-resolution-info.md) dal [metodo GetResolutionInfo.](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
