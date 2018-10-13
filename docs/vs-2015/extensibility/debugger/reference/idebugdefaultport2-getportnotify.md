---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
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
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afafdf2a7a7f92bd7c1ab23a7ebb98f63c5dc846
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294229"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo ottiene un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaccia per la porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
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

