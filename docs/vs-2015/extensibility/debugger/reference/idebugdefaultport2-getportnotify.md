---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0f5b1faf000ef982e38736b3cd3ea89a1dc2dc0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967264"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
