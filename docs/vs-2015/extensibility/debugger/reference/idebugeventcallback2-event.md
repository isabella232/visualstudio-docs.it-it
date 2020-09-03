---
title: 'IDebugEventCallback2:: Event | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 37462b5f274ca6e6c2a4a2feb4083ea94ea2f066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163977"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Invia la notifica di eventi di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pEngine`  
 in Oggetto [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) che rappresenta il motore di debug (de) che sta inviando questo evento. Per compilare questo parametro è necessario un valore DE.  
  
 `pProcess`  
 in Oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo nel quale si verifica l'evento. Questo parametro viene compilato da gestione debug sessione (SDM). Un DE passa sempre un valore null per questo parametro.  
  
 `pProgram`  
 in Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma in cui si verifica questo evento. Per la maggior parte degli eventi, questo parametro non è un valore null.  
  
 `pThread`  
 in Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in cui si verifica questo evento. Per gli eventi di arresto, questo parametro non può essere un valore null perché il stack frame viene ottenuto da questo parametro.  
  
 `pEvent`  
 in Oggetto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) che rappresenta l'evento di debug.  
  
 `riidEvent`  
 in GUID che identifica l'interfaccia eventi da ottenere dal `pEvent` parametro.  
  
 `dwAttrib`  
 in Combinazione di flag dell'enumerazione [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si chiama questo metodo, il `dwAttrib` parametro deve corrispondere al valore restituito dal metodo [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) come chiamato sull'oggetto evento passato nel `pEvent` parametro.  
  
 Tutti gli eventi di debug vengono inviati in modo asincrono, indipendentemente dal fatto che un evento sia o meno asincrono. Quando un DE chiama questo metodo, il valore restituito non indica se l'evento è stato elaborato, solo se l'evento è stato ricevuto. In realtà, nella maggior parte dei casi, l'evento non è stato elaborato quando il metodo restituisce.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
