---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67da86fd82020ef811484cb91dcd46f5f2b850da
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942779"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Determina l'esistenza di un attributo personalizzato in base al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCustomAttributeName`  
 [in] Stringa contenente il nome dell'attributo personalizzato da trovare.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce che S_OK se l'attributo personalizzato viene definito per questo campo, in caso contrario, restituisce S_FALSE.  
  
## <a name="remarks"></a>Note  
 Per ottenere i byte di attributo associati all'attributo personalizzato, chiamare il [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)