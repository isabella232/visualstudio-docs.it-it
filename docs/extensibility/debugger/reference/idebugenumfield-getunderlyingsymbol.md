---
title: IDebugEnumField::GetUnderlyingSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d555bea266180ac0405fc815107dd4db3db3e60
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962365"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Questo metodo restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il nome dell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppField`  
 [out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descriva il nome di questa enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il nome dell'enumerazione contiene anche il tipo di enumerazione, che è associato a una posizione di memoria usando [associare](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)