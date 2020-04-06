---
title: Proprietà IDebugPortEvents2::Event . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725244"
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
[in] Oggetto [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) che rappresenta il server di debug [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)](ne esiste uno per ogni istanza di ) in cui si è verificato l'evento.

`pPort`\
[in] Oggetto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) che rappresenta la porta in cui si è verificato l'evento.

`pProcess`\
[in] Oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo in cui si è verificato l'evento.

`pProgram`\
[in] Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma in cui si è verificato l'evento.

`pEvent`\
[in] Oggetto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) che identifica l'evento. I possibili eventi sono i seguenti:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
[in] GUID dell'evento. Poiché viene eseguito il cast dell'evento a [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) prima di chiamare questo metodo, questo identificatore semplifica la determinazione dell'evento inviato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
