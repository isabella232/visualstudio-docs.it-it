---
title: IDebugObject2::IsUserData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33b6815f5d216e4259c7e43dad11ca93ab1a3776
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015628"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Determina se l'oggetto rappresenta i dati dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pfUser`  
 [out] Restituisce diversi da zero (`TRUE`) se l'oggetto rappresenta i dati utente; zero (`FALSE`) se non esiste.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 I dati dell'utente sono qualsiasi oggetto che fa parte di un modulo designato come JustMyCode (opzione configurabile dall'utente che contrassegna un modulo come codice utente e pertanto visibili in una traccia dello stack).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)