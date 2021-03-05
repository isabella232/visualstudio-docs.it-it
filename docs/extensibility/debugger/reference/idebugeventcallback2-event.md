---
description: Invia la notifica di eventi di debug.
title: 'IDebugEventCallback2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afa0cfd8f96d21a510370a4fc526a3cae053c77b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152923"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Invia la notifica di eventi di debug.

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
in Oggetto [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) che rappresenta il motore di debug (de) che sta inviando questo evento. Per compilare questo parametro è necessario un valore DE.

`pProcess`\
in Oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo nel quale si verifica l'evento. Questo parametro viene compilato da gestione debug sessione (SDM). Un DE passa sempre un valore null per questo parametro.

`pProgram`\
in Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma in cui si verifica questo evento. Per la maggior parte degli eventi, questo parametro non è un valore null.

`pThread`\
in Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in cui si verifica questo evento. Per gli eventi di arresto, questo parametro non può essere un valore null perché il stack frame viene ottenuto da questo parametro.

`pEvent`\
in Oggetto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) che rappresenta l'evento di debug.

`riidEvent`\
in GUID che identifica l'interfaccia eventi da ottenere dal `pEvent` parametro.

`dwAttrib`\
in Combinazione di flag dell'enumerazione [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Quando si chiama questo metodo, il `dwAttrib` parametro deve corrispondere al valore restituito dal metodo [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) come chiamato sull'oggetto evento passato nel `pEvent` parametro.

 Tutti gli eventi di debug vengono inviati in modo asincrono, indipendentemente dal fatto che un evento sia o meno asincrono. Quando un DE chiama questo metodo, il valore restituito non indica se l'evento è stato elaborato, solo se l'evento è stato ricevuto. In realtà, nella maggior parte dei casi, l'evento non è stato elaborato quando il metodo restituisce.

## <a name="see-also"></a>Vedi anche
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
