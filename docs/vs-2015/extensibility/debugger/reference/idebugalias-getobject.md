---
title: IDebugAlias::GetObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bced4d6ea45cc33c3811e42428aa43c334b7b83b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966411"
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene l'oggetto di questo alias.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppObject`  
 [out] Il [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) questo alias rappresenta.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
