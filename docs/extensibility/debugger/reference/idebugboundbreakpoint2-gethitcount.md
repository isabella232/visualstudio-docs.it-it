---
description: Ottiene il numero di passaggi corrente per questo punto di interruzione associato.
title: IDebugBoundBreakpoint2::GetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96c93e4a6006060849bab1daf2c0f2ec7d420590d719817a1acbe0b1d35402ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360664"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
Ottiene il numero di passaggi corrente per questo punto di interruzione associato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetHitCount( 
   DWORD* pdwHitCount
);
```

```csharp
int GetHitCount( 
   out uint pdwHitCount
);
```

## <a name="parameters"></a>Parametri
`pdwHitCount`\
[out] Restituisce il numero di hit.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato è impostato su `BPS_DELETED` (parte dell BP_STATE enumere). [](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Commenti
 Il numero di passaggi è il numero di volte in cui questo punto di interruzione è stato attivato durante l'esecuzione corrente della sessione.

## <a name="see-also"></a>Vedi anche
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
