---
title: IEnumDebugBoundBreakpoints2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugBoundBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Clone
ms.assetid: c6ce01a2-7da3-46ec-9837-855042fa7244
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fa6561dbbe2a91af5d59ecd46985683f9879695
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965327"
---
# <a name="ienumdebugboundbreakpoints2clone"></a>IEnumDebugBoundBreakpoints2::Clone
Restituisce una copia dell'enumerazione corrente come oggetto separato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Clone(  
   IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce una copia di questa enumerazione come oggetto separato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 La copia dell'enumerazione ha lo stesso stato originale al momento che questo metodo viene chiamato. Tuttavia, gli Stati dell'originale e la copia sono separati e possono essere modificati singolarmente.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)