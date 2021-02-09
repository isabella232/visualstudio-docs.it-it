---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: ce47dc9a3fac9ee56b801e4d2681668f4467f532
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902168"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Usato per impostare i punti di interruzione dei dati basati su una stringa che l'utente può immettere dall'Integrated Development Environment (IDE).

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Members
`pThread`\
Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in cui si verifica il punto di interruzione.

`bstrContext`\
Contesto del punto di interruzione all'interno del codice, in genere un metodo o un nome di funzione come visualizzato in uno stack di chiamate.

`bstrDataExpr`\
Stringa di dati che l'utente immette per impostare il punto di interruzione.

`dwNumElements`\
Numero di elementi nella stringa di dati in cui si verifica il punto di interruzione.

## <a name="remarks"></a>Commenti
Questa struttura è un membro della struttura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) come parte di un'Unione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
