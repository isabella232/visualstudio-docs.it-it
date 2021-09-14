---
description: Sottrae il valore specificato dal contesto corrente e restituisce un nuovo contesto.
title: IDebugMemoryContext2::Subtract | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b25e58fed406863009b72220fad4ba04b0d3b1e0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627372"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Sottrae il valore specificato dal contesto corrente e restituisce un nuovo contesto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametri
`dwCount`\
[in] Numero di byte di memoria da decrementare.

`ppMemCxt`\
[out] Restituisce un nuovo [oggetto IDebugMemoryContext2.](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un contesto di memoria è un indirizzo, quindi la sottrazione di un valore da un indirizzo produce un nuovo indirizzo che richiede una nuova interfaccia di contesto.

 Questo metodo deve sempre produrre un nuovo contesto, anche se l'indirizzo risultante non è compreso nello spazio di memoria associato a questo contesto. L'unica eccezione è se non è possibile allocare memoria per il nuovo contesto o se è `ppMemCxt` un valore Null (si tratta di un errore).

## <a name="see-also"></a>Vedi anche
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
