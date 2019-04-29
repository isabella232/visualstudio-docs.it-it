---
title: IDebugEventCallback2::Event | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 461c2487c18cb6edc5601868c0f9644d7b8eeac1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874609"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Invia una notifica degli eventi di debug.

## <a name="syntax"></a>Sintassi

```cpp
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

 [in] Un' [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oggetto che rappresenta il motore di debug (DE) che invia questo evento. Per compilare questo parametro è necessario un CRI.

 `pProcess`

 [in] Un' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) oggetto che rappresenta il processo in cui si verifica l'evento. Questo parametro viene inserito dal gestore di sessione di debug (SDM). Un CRI passa sempre un valore null per questo parametro.

 `pProgram`

 [in] Un' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma in cui si verifica questo evento. Per la maggior parte degli eventi, questo parametro non è un valore null.

 `pThread`

 [in] Un' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread in cui si verifica questo evento. Per eventi di arresto, questo parametro non può essere un valore null durante il frame dello stack viene ottenuto da questo parametro.

 `pEvent`

 [in] Un' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) oggetto che rappresenta l'evento di debug.

 `riidEvent`

 [in] GUID che identifica quale interfaccia evento per ottenere dal `pEvent` parametro.

 `dwAttrib`

 [in] Una combinazione di flag dal [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Quando si chiama questo metodo, il `dwAttrib` parametro deve corrispondere al valore restituito dal [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) metodo chiamato sull'oggetto dell'evento passato il `pEvent` parametro.

 Tutti gli eventi di debug vengono inviati in modo asincrono, indipendentemente dal fatto che un evento stesso è asincrono. Quando un CRI chiama questo metodo, il valore restituito non indica se l'evento è stato elaborato, solo se è stato ricevuto l'evento. In effetti, nella maggior parte dei casi, l'evento non è stato elaborato quando questo metodo viene restituito.

## <a name="see-also"></a>Vedere anche
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)