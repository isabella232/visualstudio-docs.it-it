---
title: 'IDebugMemoryContext2:: compare | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e54a2bf7cd37b411dbc2d18d23a3466a4b47ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851205"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Confronta il contesto di memoria con ogni contesto nella matrice specificata nel modo indicato dai flag di confronto, restituendo un indice del primo contesto corrispondente a.

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
in Valore dell'enumerazione [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) che determina il tipo di confronto.

`rgpMemoryContextSet`\
in Matrice di riferimenti agli oggetti [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) da confrontare.

`dwMemoryContextSetLen`\
in Il numero di contesti nella `rgpMemoryContextSet` matrice.

`pdwMemoryContext`\
out Restituisce l'indice del primo contesto di memoria che soddisfa il confronto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_COMPARE_CANNOT_COMPARE` se i due contesti non possono essere confrontati.

## <a name="remarks"></a>Commenti
 Un motore di debug (de) non deve supportare tutti i tipi di confronto, ma deve supportare almeno `CONTEXT_EQUAL` , `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` e `CONTEXT_SAME_SCOPE` .

## <a name="see-also"></a>Vedi anche
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
