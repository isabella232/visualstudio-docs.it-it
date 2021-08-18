---
description: Imposta il numero di passaggi per il punto di interruzione associato.
title: IDebugBoundBreakpoint2::SetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fcc979118c4bb82327fe6bfcab76d3ca0d11b48
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127506"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Imposta il numero di passaggi per il punto di interruzione associato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>Parametri
`dwHitCount`\
[in] Numero di hit da impostare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato è impostato su `BPS_DELETED` (parte dell BP_STATE enumere). [](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Commenti
 Il numero di passaggi è il numero di volte in cui questo punto di interruzione è stato attivato durante l'esecuzione corrente della sessione.

 Questo metodo viene in genere chiamato dal motore di debug per aggiornare il numero di passaggi corrente in questo punto di interruzione.

## <a name="see-also"></a>Vedi anche
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
