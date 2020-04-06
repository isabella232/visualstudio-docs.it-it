---
title: Proprietà IDebugEngine2::Attach . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731211"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Collega un motore di debug (DE) a uno o più programmi. Chiamato dal gestore di sessione di debug (SDM) quando il DE è in esecuzione in-process per il modello SDM.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parametri
`pProgram`\
[in] Matrice di [oggetti IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresentano programmi da collegare. Questi sono programmi portuali.

`rgpProgramNodes`\
[in] Matrice di [oggetti IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che rappresentano i nodi del programma, uno per ogni programma. I nodi di programma in questa `pProgram`matrice rappresentano gli stessi programmi di . I nodi del programma sono dati in modo che il DE può identificare i programmi a cui collegarsi.

`celtPrograms`\
[in] Numero di programmi e/o `pProgram` nodi di programma negli array e `rgpProgramNodes` .

`pCallback`\
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da utilizzare per inviare eventi di debug al modello SDM.

`dwReason`\
[in] Valore dell'enumerazione [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) che specifica il motivo per cui si collegano questi programmi. Per altre informazioni, vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Ci sono tre motivi per allegare a un programma, come segue:

- `ATTACH_REASON_LAUNCH`indica che il DE si sta collegando al programma perché l'utente ha avviato il processo che lo contiene.

- `ATTACH_REASON_USER`indica che l'utente ha esplicitamente richiesto al DE di connettersi a un programma (o al processo che contiene un programma).

- `ATTACH_REASON_AUTO`indica che il DE si sta collegando a un particolare programma perché sta già eseguendo il debug di altri programmi in un particolare processo. Questo è anche chiamato auto-attach.

  Quando questo metodo viene chiamato, il DE deve inviare questi eventi in sequenza:When this method is called, the DE needs to send these events in sequence:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (se non è già stato inviato per una particolare istanza del motore di debug)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Inoltre, se il motivo `ATTACH_REASON_LAUNCH`della connessione è , il DE deve inviare il [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) evento.

   Una volta che il DE ottiene il [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto corrispondente al programma sottoposto a debug, è possibile eseguire una query per qualsiasi interfaccia privata.

   Prima di chiamare i metodi di un `pProgram` `rgpProgramNodes`nodo di programma nella matrice specificata da `IDebugProgram2` o , la rappresentazione, se necessario, deve essere abilitata sull'interfaccia che rappresenta il nodo del programma. Normalmente, tuttavia, questo passaggio non è necessario. Per ulteriori informazioni, vedere [Problemi di protezione](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
