---
title: IDebugMemoryContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d2e29cb65fb94ac5e244b7cb0536b6ac7be1901
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946568"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Confronta il contesto di memoria per ogni contesto nella matrice specificata nel modo indicato dai flag di confronto, la restituzione di un indice del primo contesto corrispondente.  
  
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
  
#### <a name="parameters"></a>Parametri  
 `compare`  
 [in] Un valore compreso il [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) enumerazione che determina il tipo di confronto.  
  
 `rgpMemoryContextSet`  
 [in] Una matrice di riferimenti per il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetti da confrontare.  
  
 `dwMemoryContextSetLen`  
 [in] Il numero di contesti di `rgpMemoryContextSet` matrice.  
  
 `pdwMemoryContext`  
 [out] Restituisce l'indice del primo contesto di memoria che soddisfa il confronto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_COMPARE_CANNOT_COMPARE` se non è possibile confrontare i due contesti.  
  
## <a name="remarks"></a>Note  
 Non dispone di un motore di debug (DE) supportare tutti i tipi di confronti, ma deve supportare almeno `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` e `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)