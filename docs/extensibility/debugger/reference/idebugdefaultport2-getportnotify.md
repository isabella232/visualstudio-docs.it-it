---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f91fd7792a47b0a2e02bdf28c75702e896b704f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865570"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Questo metodo ottiene un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaccia per la porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppPortNotify`  
 [out] Un' [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, il `QueryInterface` viene chiamato sull'oggetto che implementa le [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia per ottenere una [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaccia. Tuttavia, esistono circostanze in cui viene implementata l'interfaccia desiderata in un oggetto diverso. Questo metodo consente di nascondere tali circostanze e restituisce il `IDebugPortNotify2` interfaccia dall'oggetto più appropriato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)