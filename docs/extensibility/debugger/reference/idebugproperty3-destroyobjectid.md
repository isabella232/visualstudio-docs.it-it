---
title: IDebugProperty3::DestroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e6679c35452c63009046afb275922188d4fede6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916355"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Elimina l'ID univoco associato a questa proprietà, che indica che il chiamante non si occupa più identificare questa proprietà in modo univoco da tutte le altre proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se il motore di debug non è necessaria supportare gli ID univoci per una proprietà (perché già vengono rilevate in modo univoco internamente), quindi può semplicemente restituire `E_NOTIMPL` per questo metodo.  
  
 ID univoci vengono creati con una chiamata per il [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) metodo quando il chiamante desidera assicurarsi che questa proprietà è identificata in modo univoco tra tutte le altre proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)