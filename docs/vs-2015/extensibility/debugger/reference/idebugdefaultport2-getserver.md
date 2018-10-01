---
title: IDebugDefaultPort2::GetServer | Microsoft Docs
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
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 968f350836a09457bff78415f02a8d434cb3e5ef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530197"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugDefaultPort2::GetServer](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdefaultport2-getserver).  
  
Questo metodo ottiene un'interfaccia per il server su questa porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```csharp  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppServer`  
 [out] Restituisce un oggetto che implementa il [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) viene implementata da Visual Studio e rappresenta il server che la porta si trova in.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

