---
title: IDebugPortEvents2::Event | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ede9055f97a796e4e007914f68e370d4ff81420
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326752"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Questo metodo invia gli eventi che indicano la creazione e l'eliminazione di processi e i programmi su una porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Parametri
`pMachine`\
[in] Un' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) che rappresenta il server di debug (è presente una per ogni istanza di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]) in cui si è verificato l'evento.

`pPort`\
[in] Un' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) oggetto che rappresenta la porta in cui si è verificato l'evento.

`pProcess`\
[in] Un' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) oggetto che rappresenta il processo in cui si è verificato l'evento.

`pProgram`\
[in] Un' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma in cui si è verificato l'evento.

`pEvent`\
[in] Un' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) oggetto che identifica l'evento. Gli eventi possibili sono i seguenti:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
[in] Il GUID dell'evento. Poiché l'evento viene eseguito il cast [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) prima di chiamare questo metodo, questo identificatore rende più semplice determinare quale evento viene inviato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)