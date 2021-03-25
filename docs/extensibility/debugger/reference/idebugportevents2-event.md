---
description: Questo metodo invia eventi che indicano la creazione e la distruzione di processi e programmi su una porta.
title: 'IDebugPortEvents2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 314c31c426300c31f90813e2b73b150678578437
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058339"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Questo metodo invia eventi che indicano la creazione e la distruzione di processi e programmi su una porta.

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
in Oggetto [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) che rappresenta il server di debug, ovvero uno per ogni istanza di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , in cui si è verificato l'evento.

`pPort`\
in Oggetto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) che rappresenta la porta in cui si è verificato l'evento.

`pProcess`\
in Oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo in cui si è verificato l'evento.

`pProgram`\
in Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma in cui si è verificato l'evento.

`pEvent`\
in Oggetto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) che identifica l'evento. Gli eventi possibili sono i seguenti:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
in GUID dell'evento. Poiché viene eseguito il cast dell'evento in [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) prima di chiamare questo metodo, questo identificatore rende più semplice determinare quale evento viene inviato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
