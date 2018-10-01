---
title: IDebugObject::IsProxy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6bf40de9aafce311ce26c42659a6e563882718b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528400"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugObject::IsProxy](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-isproxy).  
  
Determina se l'oggetto è un proxy trasparente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```csharp  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pfIsProxy`  
 [out] `TRUE` se l'oggetto è un proxy trasparente; in caso contrario, `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene implementato dal motore di debug C++ predefinite.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

