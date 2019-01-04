---
title: IDebugObject::SetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a3e2166818de87ea2322cd7155c76c3f3209aef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938303"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Imposta il valore dell'oggetto da una serie consecutiva di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pValue`  
 [in] Matrice di byte che rappresenta il nuovo valore.  
  
 `nSize`  
 [in] Le dimensioni del valore in byte.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 I valori nella matrice vengono copiati [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto, sostituendo i valori esistenti. Le dimensioni del nuovo valore possono essere maggiore o minore di quello esistente. Ciò `IDebugObject` non può essere un riferimento null.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)