---
title: IEnumDebugFields::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::Skip
helpviewer_keywords:
- IEnumDebugFields::Skip method
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03ae4578f5305b4b11404d588ed65fe73df24469
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989757"
---
# <a name="ienumdebugfieldsskip"></a>IEnumDebugFields::Skip
Questo metodo ignora il numero specificato di elementi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Numero di elementi da ignorare.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se `celt` è maggiore del numero di elementi rimanenti; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se `celt` specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione è impostata su Fine e `S_FALSE` viene restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)