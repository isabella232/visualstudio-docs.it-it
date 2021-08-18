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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 908660d606351ea37e602a285a81bdb2b6c492f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030347"
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
Contesto del punto di interruzione, in genere un nome di metodo o funzione come visualizzato in uno stack di chiamate.

`pFuncPos`\
Oggetto [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) che descrive il nome della funzione e la posizione relativa dall'inizio della funzione.

## <a name="remarks"></a>Commenti
Questa struttura è un membro della [struttura](../../../extensibility/debugger/reference/bp-location.md) BP_LOCATION come parte di un'unione.

Il `pFuncPos` membro indica dove impostare il punto di interruzione della funzione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
