---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d4a40da82f77f3eb04317fcb936e7a10c5351e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863709"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Restituisce una struttura che descrive un oggetto e il relativo percorso nel relativo ambito o di un contenitore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in, out] Oggetto [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura che viene compilato da questo metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura viene passata a questo metodo, che quindi viene riempita con le informazioni appropriate. Modalità di interpretazione di queste informazioni dipende dal tipo di informazioni restituite e il gestore di simboli se stesso. Visualizzare [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) per altri dettagli.  
  
## <a name="see-also"></a>Vedere anche  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)