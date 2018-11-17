---
title: IDebugProperty2::GetDerivedMostProperty | Microsoft Docs
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
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68d4f3447916dfaed3a6788bb31eb79910aeed11
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733611"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene la proprietà più derivato di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppDerivedMost`  
 [out] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta la proprietà più derivato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore. Restituisce `S_GETDERIVEDMOST_NO_DERIVED_MOST` se è presente nessuna proprietà più derivato da recuperare.  
  
## <a name="remarks"></a>Note  
 Ad esempio, se questa proprietà descrive un oggetto che implementa `ClassRoot` ma che è effettivamente un'istanza di `ClassDerived` che è derivato da `ClassRoot`, questo metodo restituisce un' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che descrive il `ClassDerived` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

