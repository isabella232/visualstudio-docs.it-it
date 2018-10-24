---
title: IDebugObject2::GetAlias | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0919fe9617231a94f39b08b83c10e3b5ef645792
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854338"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Ottiene l'alias associato all'oggetto, se presente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppAlias`  
 [out] Restituisce un [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) dell'oggetto che rappresenta l'alias per questo oggetto; in caso contrario, restituisce un valore null.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un alias per un oggetto viene creato con una chiamata per il [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)