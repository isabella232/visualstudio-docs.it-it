---
title: IEnumDebugObjects::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d2921c5d49665b59c94fa82027ac5562f38b8b0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034570"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
Questo metodo restituisce il set successivo di elementi dall'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Next(  
   ULONG          celt,  
   IDebugObject** rgelt,  
   ULONG*         pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint           celt,  
   IDebugObject[] rgelt,  
   ref uint       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di elementi da recuperare. Specifica inoltre la dimensione massima del `rgelt` matrice.  
  
 `rgelt`  
 [in, out] Matrice di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) elementi da compilare.  
  
 `pceltFetched`  
 [out] Restituisce il numero di elementi effettivamente restituiti nella `rgelt`.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se inferiore al numero richiesto di elementi potrebbe essere restituiti; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)