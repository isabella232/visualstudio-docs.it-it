---
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25756c00ba493dba866ab70693e69971333ae9ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901928"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Descrive il risultato dell'associazione di un punto di interruzione dei dati.

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
Nome della funzione in cui è associato il punto di interruzione dei dati (se presente).

`bstrImage`\
Nome del modulo (ad esempio, MyModule.dll) a cui è associato il punto di interruzione dei dati.

`dwFlags`\
Valore dell'enumerazione [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) , che descrive la modalità di implementazione del punto di interruzione dei dati.

## <a name="remarks"></a>Commenti
Questa struttura è un membro della struttura di [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , che a sua volta è un membro della struttura [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) restituita dal metodo [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
