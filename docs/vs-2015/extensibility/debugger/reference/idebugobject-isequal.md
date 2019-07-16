---
title: IDebugObject::IsEqual | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85252cdaf9fb076ebd4f8000115bcea576531bb1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159118"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Confronta un oggetto con questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pObject`  
 [in] Un' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto da confrontare con l'oggetto.  
  
 `pfIsEqual`  
 [out] Restituisce diverso da zero (`TRUE`) se i valori degli oggetti sono uguali; in caso contrario, restituisce zero (`FALSE`).  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, questo metodo può confrontare gli indirizzi dei valori rappresentati dal `pObject` parametro e ciò [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto; se gli indirizzi sono uguali, quindi gli oggetti possono essere considerati uguali.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
