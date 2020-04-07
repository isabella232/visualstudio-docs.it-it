---
title: Proprietà IDebugEventCallback2::Event . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729902"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Invia la notifica degli eventi di debug.

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

## <a name="parameters"></a>Parametri
`pEngine`\
[in] Oggetto [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) che rappresenta il motore di debug (DE) che invia questo evento. Per compilare questo parametro è necessario un DE.

`pProcess`\
[in] Oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo in cui si verifica l'evento. Questo parametro viene compilato dal gestore di debug della sessione (SDM). Un DE passa sempre un valore null per questo parametro.

`pProgram`\
[in] Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma in cui si verifica questo evento. Per la maggior parte degli eventi, questo parametro non è un valore null.

`pThread`\
[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in cui si verifica questo evento. Per gli eventi di arresto, questo parametro non può essere un valore null poiché lo stack frame viene ottenuto da questo parametro.

`pEvent`\
[in] Oggetto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) che rappresenta l'evento di debug.

`riidEvent`\
[in] GUID che identifica l'interfaccia `pEvent` eventi da ottenere dal parametro.

`dwAttrib`\
[in] Combinazione di flag dell'enumerazione [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Quando si chiama `dwAttrib` questo metodo, il parametro deve corrispondere al valore restituito dal `pEvent` [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) metodo come chiamato sull'oggetto evento passato nel parametro.

 Tutti gli eventi di debug vengono registrati in modo asincrono, indipendentemente dal fatto che un evento stesso sia asincrono o meno. Quando un DE chiama questo metodo, il valore restituito non indica se l'evento è stato elaborato, ma solo se l'evento è stato ricevuto. Infatti, nella maggior parte dei casi, l'evento non è stato elaborato quando questo metodo restituisce.

## <a name="see-also"></a>Vedere anche
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
