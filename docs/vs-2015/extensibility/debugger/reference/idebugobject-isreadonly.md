---
title: IDebugObject::IsReadOnly | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74b55895e440f900e59cd3b517e22dd8a0191414
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159084"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se questo oggetto è di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pfIsReadOnly`  
 [out] Restituisce diverso da zero (`TRUE`) se l'oggetto è di sola lettura; in caso contrario, restituisce zero (`FALSE`).  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un oggetto di sola lettura non può essere modificata dopo averlo creato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
