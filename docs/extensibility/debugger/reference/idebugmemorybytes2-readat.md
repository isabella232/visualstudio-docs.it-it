---
title: 'IDebugMemoryBytes2:: ReadAt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81a6ce40457243e5492d5c6a44dd5d9dd590920f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909928"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Legge una sequenza di byte a partire da una posizione specificata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Parametri
`pStartContext`\
in Oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che specifica la posizione in cui iniziare la lettura dei byte.

`dwCount`\
in Numero di byte da leggere. Specifica anche la lunghezza della `rgbMemory` matrice.

`rgbMemory`\
[in, out] Matrice compilata con i byte effettivamente letti.

`pdwRead`\
out Restituisce il numero di byte contigui effettivamente letti.

`pdwUnreadable`\
[in, out] Restituisce il numero di byte illeggibili. Può essere un valore null se il client non è interessato dal numero di byte illeggibili.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Se vengono richiesti 100 byte e i primi 50 sono leggibili, i 20 successivi sono illeggibili e i 30 rimanenti sono leggibili, questo metodo restituisce:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 In questo caso, poiché `*pdwRead + *pdwUnreadable < dwCount` il chiamante deve effettuare una chiamata aggiuntiva per leggere i restanti 30 byte dell'originale 100 richiesto e l'oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passato nel `pStartContext` parametro deve essere avanzato da 70.

## <a name="see-also"></a>Vedi anche
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
