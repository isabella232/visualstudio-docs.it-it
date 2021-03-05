---
description: Descrive la posizione di un punto di interruzione in corrispondenza di un indirizzo nel codice.
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 961a62284b841d56ae73a29df0e83810ff9d7d20
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144442"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
Descrive la posizione di un punto di interruzione in corrispondenza di un indirizzo nel codice.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Members
`bstrContext`\
Contesto del punto di interruzione, in genere un metodo o un nome di funzione come visualizzato in uno stack di chiamate.

`bstrModuleUrl`\
URL del modulo che contiene il punto di interruzione.

`bstrFunction`\
Nome della funzione che contiene il punto di interruzione.

`bstrAddress`\
Indirizzo del punto di interruzione, analizzato da un analizzatore di espressioni per associarlo a un oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="remarks"></a>Commenti
Questa struttura è un membro della struttura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) come parte di un'Unione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
