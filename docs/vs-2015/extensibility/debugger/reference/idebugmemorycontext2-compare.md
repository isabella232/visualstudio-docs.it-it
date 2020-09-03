---
title: 'IDebugMemoryContext2:: compare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3eb48c324b5a1a918ab864c5eb4c4ca39eae41ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163436"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Confronta il contesto di memoria con ogni contesto nella matrice specificata nel modo indicato dai flag di confronto, restituendo un indice del primo contesto corrispondente a.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 in Valore dell'enumerazione [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) che determina il tipo di confronto.  
  
 `rgpMemoryContextSet`  
 in Matrice di riferimenti agli oggetti [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) da confrontare.  
  
 `dwMemoryContextSetLen`  
 in Il numero di contesti nella `rgpMemoryContextSet` matrice.  
  
 `pdwMemoryContext`  
 out Restituisce l'indice del primo contesto di memoria che soddisfa il confronto.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_COMPARE_CANNOT_COMPARE` se i due contesti non possono essere confrontati.  
  
## <a name="remarks"></a>Osservazioni  
 Un motore di debug (de) non deve supportare tutti i tipi di confronto, ma deve supportare almeno `CONTEXT_EQUAL` , `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` e `CONTEXT_SAME_SCOPE` .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
