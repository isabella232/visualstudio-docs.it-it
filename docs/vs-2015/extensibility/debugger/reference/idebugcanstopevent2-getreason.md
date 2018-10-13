---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
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
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c94a54f93cd9e7eb62e2b7cd1ff8aa8f17cd3cdd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302679"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il motivo per cui il motore di debug (DE) desidera arrestare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcr`  
 [out] Restituisce un valore di [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) enumerazione che descrive il motivo per questo evento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato in genere prima la [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metodo in modo che il chiamante può determinare se passare diverso da zero (`TRUE`) per il `IDebugCanStopEvent2::CanStop` (metodo).  
  
 Può essere il motivo di arresto `CANSTOP_ENTRYPOINT`, ovvero il DE ha raggiunto un punto di ingresso, o `CANSTOP_STEPIN`, ovvero il DE ha eseguito un'istruzione nella funzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)

