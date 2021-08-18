---
description: Usato per impostare punti di interruzione dei dati basati su una stringa che l'utente può immettere dall'ambiente di sviluppo integrato (IDE).
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 81506ddf411b3a983d3801d569e7069a2ae34e00
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120478"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Usato per impostare punti di interruzione dei dati basati su una stringa che l'utente può immettere dall'ambiente di sviluppo integrato (IDE).

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
Contesto del punto di interruzione all'interno del codice, in genere un nome di metodo o funzione come visualizzato in uno stack di chiamate.

`bstrDataExpr`\
Stringa di dati immessa dall'utente per impostare il punto di interruzione.

`dwNumElements`\
Numero di elementi nella stringa di dati in cui si verifica il punto di interruzione.

## <a name="remarks"></a>Commenti
Questa struttura è un membro della [struttura](../../../extensibility/debugger/reference/bp-location.md) BP_LOCATION come parte di un'unione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
