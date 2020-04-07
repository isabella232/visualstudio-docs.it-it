---
title: IDebugMemoryContext2::Compare Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727500"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Confronta il contesto di memoria con ogni contesto nella matrice specificata nel modo indicato da flag di confronto, restituendo un indice del primo contesto che corrisponde.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>Parametri
`compare`\
[in] Valore dell'enumerazione [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) che determina il tipo di confronto.

`rgpMemoryContextSet`\
[in] Matrice di riferimenti agli oggetti [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) da confrontare.

`dwMemoryContextSetLen`\
[in] Numero di contesti `rgpMemoryContextSet` nella matrice.

`pdwMemoryContext`\
[fuori] Restituisce l'indice del primo contesto di memoria che soddisfa il confronto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_COMPARE_CANNOT_COMPARE` se i due contesti non possono essere confrontati.

## <a name="remarks"></a>Osservazioni
 Un motore di debug (DE) non deve supportare tutti i `CONTEXT_EQUAL`tipi `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` di `CONTEXT_SAME_SCOPE`confronti, ma deve supportare almeno , e .

## <a name="see-also"></a>Vedere anche
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
