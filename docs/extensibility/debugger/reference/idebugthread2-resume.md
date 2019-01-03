---
title: IDebugThread2::Resume | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bad2daaa21607194504923db8e896237298c75d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824587"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Riprende l'esecuzione di un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
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