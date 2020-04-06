---
title: Proprietà IDebugMemoryBytes2::WriteAt . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727525"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Scrive il numero specificato di byte di memoria, a partire dall'indirizzo specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parametri
`pStartContext`\
[in] Il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto che specifica dove iniziare a scrivere byte.

`dwCount`\
[in] Numero di byte da scrivere.

`rgbMemory`\
[in] Byte da scrivere. Si presuppone che questa `dwCount` matrice abbia una dimensione di almeno byte.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso `S_FALSE` contrario, restituisce se non tutti `E_FAIL`i byte possono essere scritti o restituisce un codice di errore (in genere ).

## <a name="remarks"></a>Osservazioni
 Se l'indirizzo iniziale non è all'interno della finestra di memoria rappresentata `E_FAIL` da questo [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) oggetto, non viene eseguita alcuna scrittura e viene restituito un codice di errore di , anche se la quantità di scrittura si sovrappone nello spazio di memoria.

## <a name="see-also"></a>Vedere anche
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
