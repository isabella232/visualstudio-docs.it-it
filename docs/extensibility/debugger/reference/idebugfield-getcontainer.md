---
title: IDebugField::GetContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de664eb2a5c53317da9732101187965e6e5c7509
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945834"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Questo metodo ottiene il contenitore di un campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppContainerField`  
 [out] Restituisce il contenitore come rappresentata dai [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se questo campo non dispone di un contenitore, l'oggetto restituito `ppContainerField` sarà un valore null.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)