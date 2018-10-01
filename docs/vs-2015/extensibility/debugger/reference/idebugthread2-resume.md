---
title: IDebugThread2::Resume | Microsoft Docs
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
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a3591ff3363a267b65c41093b18ff8d3ed154d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529248"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugThread2::Resume](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugthread2-resume).  
  
Riprende l'esecuzione di un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSuspendCount`  
 [out] Restituisce il conteggio di sospensione al termine dell'operazione di ripresa.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ogni chiamata a questo metodo decrementa il conteggio di sospensione fino a raggiungere 0 a quel punto, in realtà ripresa l'esecuzione. Questo conteggio di sospensione viene visualizzato nei **thread** finestra di debug.  
  
 Per ogni chiamata a questo metodo, deve esistere una chiamata precedente al [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) (metodo). Il conteggio di suspend determina quante volte il `IDebugThread2::Suspend` metodo è stato chiamato fino a questo momento.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)

