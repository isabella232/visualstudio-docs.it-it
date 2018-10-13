---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1dde6683173931fa261e4f0793413bcf5bc42e5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198562"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea una copia dell'oggetto gestito nello spazio degli indirizzi del motore di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppObject`  
 [out] Restituisce un [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) oggetto che rappresenta l'oggetto gestito appena creato.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se l'oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) non rappresenta un'istanza della classe valore gestito.  
  
## <a name="remarks"></a>Note  
 Ciò [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto deve rappresentare un'istanza della classe valore gestito, ad esempio un `System.Decimal` istanza. Facendo in modo che una copia locale, l'overhead della chiamata al metodo [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) viene eliminato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

