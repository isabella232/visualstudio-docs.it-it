---
title: IEnumDebugCustomAttributes::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumCustomAttributes::Skip
helpviewer_keywords:
- IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9525a96f1d5a5d7c6c31994058dabb6c051874c5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943955"
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
Ignora un determinato numero di attributi personalizzati in una sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Skip (   
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
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)