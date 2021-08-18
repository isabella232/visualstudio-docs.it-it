---
description: Invia la notifica degli eventi di debug.
title: IDebugEventCallback2::Event | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcf3fe8bc0c71340681e913dcbe117146944299d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089043"
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
[in] Oggetto [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) che rappresenta il motore di debug che invia questo evento. Per compilare questo parametro è necessario un de.

`pProcess`\
[in] Oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo in cui si verifica l'evento. Questo parametro viene compilato dalla gestione del debug di sessione (SDM). De passa sempre un valore Null per questo parametro.

`pProgram`\
[in] Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma in cui si verifica questo evento. Per la maggior parte degli eventi, questo parametro non è un valore Null.

`pThread`\
[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in cui si verifica questo evento. Per gli eventi di arresto, questo parametro non può essere un valore Null perché stack frame viene ottenuto da questo parametro.

`pEvent`\
[in] Oggetto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) che rappresenta l'evento di debug.

`riidEvent`\
[in] GUID che identifica l'interfaccia eventi da ottenere dal `pEvent` parametro .

`dwAttrib`\
[in] Combinazione di flag [dell'enumerazione EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Quando si chiama questo metodo, il parametro deve corrispondere al valore restituito dal `dwAttrib` [metodo GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) come chiamato sull'oggetto evento passato nel `pEvent` parametro .

 Tutti gli eventi di debug vengono pubblicati in modo asincrono, indipendentemente dal fatto che un evento sia asincrono o meno. Quando denota questo metodo, il valore restituito non indica se l'evento è stato elaborato, ma solo se l'evento è stato ricevuto. Nella maggior parte dei casi, infatti, l'evento non è stato elaborato quando questo metodo viene restituito.

## <a name="see-also"></a>Vedi anche
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
