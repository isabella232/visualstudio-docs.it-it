---
description: Scrive il numero specificato di byte di memoria, a partire dall'indirizzo specificato.
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 099da50a72150d425fca560648df743f1804776f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035020"
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
[in] Oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che specifica dove iniziare a scrivere byte.

`dwCount`\
[in] Numero di byte da scrivere.

`rgbMemory`\
[in] Byte da scrivere. Si presuppone che le dimensioni di questa matrice `dwCount` siano almeno byte.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce ; in caso contrario, restituisce se non tutti i byte possono essere scritti o restituisce un `S_OK` `S_FALSE` codice di errore (in genere `E_FAIL` ).

## <a name="remarks"></a>Commenti
 Se l'indirizzo iniziale non si trova all'interno della finestra di memoria rappresentata da questo oggetto [IDebugMemoryBytes2,](../../../extensibility/debugger/reference/idebugmemorybytes2.md) non viene eseguita alcuna scrittura e viene restituito un codice di errore di , anche se la quantità di scrittura si sovrappone allo spazio di `E_FAIL` memoria.

## <a name="see-also"></a>Vedi anche
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
