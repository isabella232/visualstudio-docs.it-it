---
title: IDebugObject::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9fe479c93cadeb6826ee4e4d3ba41ff973cb11c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027737"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Ottiene il contesto di memoria che rappresenta l'indirizzo del valore dell'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```csharp  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pContext`  
 [out] Restituisce un [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto che rappresenta l'indirizzo del valore dell'oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il contesto di memoria restituita specifica l'indirizzo del valore come rappresentato da questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)