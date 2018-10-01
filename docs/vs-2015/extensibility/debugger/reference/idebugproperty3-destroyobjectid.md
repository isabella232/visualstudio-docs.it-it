---
title: IDebugProperty3::DestroyObjectID | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 012a4fcc8b5ada9208a3d2b4cd65e5e7ae5c225d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518327"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProperty3::DestroyObjectID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-destroyobjectid).  
  
Elimina l'ID univoco associato a questa proprietà, che indica che il chiamante non si occupa più identificare questa proprietà in modo univoco da tutte le altre proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se il motore di debug non è necessaria supportare gli ID univoci per una proprietà (perché già vengono rilevate in modo univoco internamente), quindi può semplicemente restituire `E_NOTIMPL` per questo metodo.  
  
 ID univoci vengono creati con una chiamata per il [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) metodo quando il chiamante desidera assicurarsi che questa proprietà è identificata in modo univoco tra tutte le altre proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)

