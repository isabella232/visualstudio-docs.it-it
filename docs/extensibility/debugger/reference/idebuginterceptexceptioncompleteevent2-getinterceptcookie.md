---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14316ac59394f6328da82f155c43ab069985ba9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042530"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Chiamato quando è stata completata l'elaborazione di un'eccezione intercettata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pqwCookie`  
 [out] Valore univoco che viene associata all'eccezione che è stato intercettato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 Dopo il [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) metodo ha completato la gestione di un'eccezione intercettata, invia le [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) evento. Il gestore di è possibile usare la `GetInterceptCookie` metodo per recuperare il valore univoco associato all'eccezione (lo stesso valore passato al `InterceptCurrentException` (metodo)).  
  
## <a name="see-also"></a>Vedere anche  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)