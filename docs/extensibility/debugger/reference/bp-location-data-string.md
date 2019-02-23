---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 056b7efc01b9536184c3e443156e27e328bdd2b3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689096"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Utilizzata per impostare i punti di interruzione dei dati che si basano su una stringa che l'utente può immettere dall'ambiente di sviluppo integrato (IDE).

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Membri
`pThread` Il [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread in cui si verifica il punto di interruzione.

`bstrContext` Contesto del punto di interruzione all'interno del codice, in genere un nome di metodo o una funzione come visualizzato in uno stack di chiamate.

`bstrDataExpr` La stringa di dati l'utente immette per impostare il punto di interruzione.

`dwNumElements` Il numero di elementi nella stringa di dati in cui si verifica il punto di interruzione.

## <a name="remarks"></a>Note
Questa struttura è un membro del [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struttura come parte di un'unione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
