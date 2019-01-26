---
title: IDebugEngine2::RemoveAllSetExceptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e28eb35d1d6172f693cc2be0e17aa3cd25050373
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986293"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Rimuove l'elenco delle eccezioni che nell'IDE è impostata per un linguaggio o una particolare architettura della fase di esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidType`  
 [in] Il GUID per la lingua o il GUID per il motore di debug specifico per un'architettura di runtime.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Le eccezioni rimosse da questo metodo sono state impostate dalle chiamate precedenti per il [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (metodo).  
  
 Per rimuovere un'eccezione specifica, chiamare il [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)