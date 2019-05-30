---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5eefaee08d64952681e91711cdf8347186123e57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347141"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Scrive il numero specificato di byte di memoria, iniziando in corrispondenza dell'indirizzo specificato.

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
[in] Il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che specifica la posizione in cui iniziare la scrittura dei byte.

`dwCount`\
[in] Il numero di byte da scrivere.

`rgbMemory`\
[in] Byte da scrivere. Questa matrice si presuppone che sia almeno `dwCount` byte le dimensioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` se non tutti i byte può essere scritta o restituisce un codice di errore (in genere `E_FAIL`).

## <a name="remarks"></a>Note
 Se l'indirizzo iniziale non è presente all'interno della finestra memoria rappresentata da questo [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) dell'oggetto, si verifica alcuna scrittura e codice di errore `E_FAIL` viene restituito, anche se la quantità di scrivere si sovrappone allo spazio della memoria.

## <a name="see-also"></a>Vedere anche
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)