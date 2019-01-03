---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab2078a655062e67c7db8c2fe2be7d5472b31dcf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854310"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica al motore di debug (DE) per interrompere in corrispondenza della posizione di codice corrente o semplicemente continuare l'esecuzione o meno.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fCanStop`  
 [in] Diverso da zero (`TRUE`) se la Germania deve essere interrotta in corrispondenza della posizione di codice corrente; in caso contrario, zero (`FALSE`).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il ricevitore dell'evento chiama in genere il [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodo per determinare il motivo per la Germania desidera arrestare e quindi chiama il `IDebugCanStopEvent2::CanStop` metodo con la risposta appropriata.  
  
 Se si arresta la Germania, invia un evento che descrive il motivo dell'arresto. In genere esistono due eventi che vengono inviati, rappresentata da un'interruzione di utente o un segnale i [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfaccia e un evento punto di interruzione rappresentato dal [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)