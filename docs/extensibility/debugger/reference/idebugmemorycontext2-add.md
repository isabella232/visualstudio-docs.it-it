---
title: IDebugMemoryContext2::Add | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9625bcdc69d4df157f4309ae24d4baafcda1264a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974344"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Aggiunge il valore specificato per il contesto corrente e restituisce un nuovo contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCount`  
 [in] Il valore da aggiungere al contesto corrente.  
  
 `ppMemCxt`  
 [out] Restituisce un nuovo [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un contesto in memoria è un indirizzo, quindi aggiunge un valore a un indirizzo produce un nuovo indirizzo che richiede una nuova interfaccia contesto.  
  
 Questo metodo deve produrre sempre un nuovo contesto, anche se l'indirizzo risulta è all'esterno dello spazio di memoria associato al contesto. L'unica eccezione è se non può essere allocata nessuna memoria per il nuovo contesto o se `ppMemCxt` è un valore null (ovvero un errore).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)