---
title: Proprietà IDebugMemoryBytes2::ReadAt . Documenti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727541"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Legge una sequenza di byte, a partire da una posizione specificata.

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
[in] Il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto che specifica da dove iniziare la lettura di byte.

`dwCount`\
[in] Numero di byte da leggere. Specifica anche la lunghezza `rgbMemory` della matrice.

`rgbMemory`\
[in, out] Matrice compilata con i byte effettivamente letti.

`pdwRead`\
[fuori] Restituisce il numero di byte contigui effettivamente letti.

`pdwUnreadable`\
[in, out] Restituisce il numero di byte illeggibili. Può essere un valore null se il client non è interessato al numero di byte illeggibili.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Se vengono richiesti 100 byte e i primi 50 sono leggibili, i 20 successivi sono illeggibili e i restanti 30 sono leggibili, questo metodo restituisce:

 *`pdwRead`50 USD

 *`pdwUnreadable`20 USD

 In questo caso, poiché `*pdwRead + *pdwUnreadable < dwCount`, il chiamante deve effettuare una chiamata aggiuntiva per leggere i restanti 30 byte dell'originale 100 richiesto e l'oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passato nel `pStartContext` parametro deve essere avanzato di 70.

## <a name="see-also"></a>Vedere anche
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
