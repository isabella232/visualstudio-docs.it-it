---
title: IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fcc496131cd27837dc53fe2ecba05cf6b2c44d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966374"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se è stato definito un attributo personalizzato specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 Restituisce che S_OK se l'attributo personalizzato viene definito per questo metodo, in caso contrario, restituisce S_FALSE.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
