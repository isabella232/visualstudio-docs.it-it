---
description: Legge una sequenza di byte, a partire da una posizione specificata.
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6715129ad449e7d92ed2b74785469408973b25c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043440"
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
[in] Oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che specifica dove iniziare la lettura dei byte.

`dwCount`\
[in] Numero di byte da leggere. Specifica anche la lunghezza della `rgbMemory` matrice.

`rgbMemory`\
[in, out] Matrice compilata con i byte effettivamente letti.

`pdwRead`\
[out] Restituisce il numero di byte contigui effettivamente letti.

`pdwUnreadable`\
[in, out] Restituisce il numero di byte illeggibili. Può essere un valore Null se il client non è interessato dal numero di byte illeggibili.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Se vengono richiesti 100 byte e i primi 50 sono leggibili, i 20 successivi sono illeggibili e i 30 rimanenti sono leggibili, questo metodo restituisce:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 In questo caso, poiché , il chiamante deve effettuare una chiamata aggiuntiva per leggere i 30 byte rimanenti dei 100 originali richiesti e l'oggetto `*pdwRead + *pdwUnreadable < dwCount` [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passato nel parametro deve essere avanzato di `pStartContext` 70.

## <a name="see-also"></a>Vedi anche
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
