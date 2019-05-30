---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1083239dbb00e5b953fe7a72c27a350ffe34cc2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314307"
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
[in] Il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che specifica la posizione in cui iniziare la lettura dei byte.

`dwCount`\
[in] Il numero di byte da leggere. Specifica la lunghezza del `rgbMemory` matrice.

`rgbMemory`\
[in, out] Matrice contenente i byte effettivamente letti.

`pdwRead`\
[out] Restituisce il numero di byte contigui effettivamente letti.

`pdwUnreadable`\
[in, out] Restituisce il numero di byte illeggibile. Può essere un valore null se il client non il numero di byte illeggibile.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Se vengono richiesti 100 byte e le prime 50 sono leggibili, i prossimi 20 sono illeggibili e il 30 rimanenti sono leggibili, questo metodo restituisce:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 In questo caso, poiché `*pdwRead + *pdwUnreadable < dwCount`, il chiamante deve effettuare una chiamata aggiuntiva per leggere i byte rimanenti 30 del 100 originale richiesto e il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto passato nel `pStartContext` parametro deve essere anticipato da 70.

## <a name="see-also"></a>Vedere anche
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)