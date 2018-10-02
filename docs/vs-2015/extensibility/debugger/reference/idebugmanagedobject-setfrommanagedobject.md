---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
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
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c452225290136cd168b655f2ed3196ca91961168
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520005"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugManagedObject::SetFromManagedObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject).  
  
Imposta il valore dell'istanza dell'oggetto della classe di valore dall'istanza della classe di valori fornita come parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pManagedObject`  
 [in] Un'interfaccia che rappresenta l'oggetto gestito che contiene il nuovo valore.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato per modificare l'oggetto gestito, come rappresentate dal [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

