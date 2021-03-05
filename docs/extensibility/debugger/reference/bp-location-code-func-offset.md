---
description: Descrive la posizione di offset di un punto di interruzione in una funzione nel codice.
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 83a5a27601ab6d7498394d6723b86ad3e66aceb5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144364"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Descrive la posizione di offset di un punto di interruzione in una funzione nel codice.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>Members
`bstrContext`\
Contesto del punto di interruzione, in genere un metodo o un nome di funzione come visualizzato in uno stack di chiamate.

`pFuncPos`\
Oggetto [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) che descrive il nome della funzione e la posizione relativa dall'inizio della funzione.

## <a name="remarks"></a>Commenti
Questa struttura è un membro della struttura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) come parte di un'Unione.

Il `pFuncPos` membro indica dove impostare il punto di interruzione della funzione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
