---
description: Confronta il contesto di memoria con ogni contesto nella matrice specificata nel modo indicato dai flag di confronto, restituisce un indice del primo contesto corrispondente.
title: IDebugMemoryContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b0e4e55872da333089d91eddd8edb54d7ce99f5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627389"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Confronta il contesto di memoria con ogni contesto nella matrice specificata nel modo indicato dai flag di confronto, restituisce un indice del primo contesto corrispondente.

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
[in] Valore [dell'enumerazione CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) che determina il tipo di confronto.

`rgpMemoryContextSet`\
[in] Matrice di riferimenti agli oggetti [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) da confrontare.

`dwMemoryContextSetLen`\
[in] Numero di contesti nella `rgpMemoryContextSet` matrice.

`pdwMemoryContext`\
[out] Restituisce l'indice del primo contesto di memoria che soddisfa il confronto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_COMPARE_CANNOT_COMPARE` se non è possibile confrontare i due contesti.

## <a name="remarks"></a>Commenti
 Un motore di debug (DE) non deve supportare tutti i tipi di confronti, ma deve supportare almeno `CONTEXT_EQUAL` , `CONTEXT_LESS_THAN` e `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE` .

## <a name="see-also"></a>Vedi anche
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
