---
title: IDebugPort2::GetPortRequest | Microsoft Docs
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
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9570f1b7e1e77483d0cff001ce09a4b583416e1f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531123"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugPort2::GetPortRequest](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugport2-getportrequest).  
  
Ottiene la descrizione di una porta che è stato precedentemente utilizzata per creare la porta (se disponibile).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppRequest`  
 [out] Restituisce un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) oggetto che rappresenta la richiesta che è stata usata per creare la porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce `E_PORT_NO_REQUEST` se non è stata creata una porta con un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) richiesta porta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

