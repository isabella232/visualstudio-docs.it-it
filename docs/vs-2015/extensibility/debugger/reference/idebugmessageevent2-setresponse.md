---
title: IDebugMessageEvent2::SetResponse | Microsoft Docs
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
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7c0ac3f2e06a69d397ec4880059d90bb3df01ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526971"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugMessageEvent2::SetResponse](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmessageevent2-setresponse).  
  
Imposta la risposta, se presente, nella finestra di messaggio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetResponse(   
   DWORD dwResponse  
);  
```  
  
```csharp  
int SetResponse(   
   uint dwResponse  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwResponse`  
 [in] Specifica la risposta, usando le convenzioni di Win32 `MessageBox` (funzione). Vedere le [AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) funzione per i dettagli.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)

