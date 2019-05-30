---
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 51137b5a5a69c80ecd7129d4c645f63b5805d27d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319135"
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
Descrive la posizione di un punto di interruzione in un indirizzo nel codice.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Membri
`bstrContext`\
Il contesto del punto di interruzione, in genere un nome di metodo o una funzione come visualizzato in uno stack di chiamate.

`bstrModuleUrl`\
L'URL del modulo che contiene il punto di interruzione.

`bstrFunction`\
Il nome della funzione che contiene il punto di interruzione.

`bstrAddress`\
L'indirizzo del punto di interruzione, viene analizzato da un analizzatore di espressioni per associarlo a un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto.

## <a name="remarks"></a>Note
Questa struttura è un membro del [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struttura come parte di un'unione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
