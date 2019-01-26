---
title: IDebugPropertyField::GetPropertyGetter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5df84fc77443cdbc8554b3755385d3cd8682f1b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041529"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
Ottiene il metodo che ottiene la proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPropertyGetter(   
   IDebugMethodField** ppField  
);  
```  
  
```cpp  
int GetPropertyGetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppField`  
 [out] Restituisce un [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) oggetto che rappresenta il metodo che ottiene la proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Per ottenere il metodo che imposta la proprietà [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) chiamare il metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)