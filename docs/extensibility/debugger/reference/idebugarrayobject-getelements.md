---
title: IDebugArrayObject::GetElements | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7693c4ed3442cf86a0e310a6e2dd6d75655fcb69
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904726"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Ottiene un enumeratore di tutti gli elementi della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) oggetto che consente l'enumerazione su tutti gli elementi.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In alternativa, usare il [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) e [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodi per scorrere gli elementi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)