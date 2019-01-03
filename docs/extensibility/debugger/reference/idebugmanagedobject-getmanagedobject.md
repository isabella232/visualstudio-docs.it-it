---
title: IDebugManagedObject::GetManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9915e4b9096f9e7ac42700012ea55ee23baef46c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823050"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Restituisce un'interfaccia che rappresenta l'oggetto gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppManagedObject`  
 [out] Restituisce un'interfaccia che rappresenta l'oggetto gestito.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'interfaccia restituita da questo metodo è possibile eseguire query per qualsiasi interfaccia implementata dalla classe gestita, che consente di chiamare i relativi metodi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)