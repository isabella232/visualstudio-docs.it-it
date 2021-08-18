---
description: Collega un motore di debug (DE) a uno o più programmi.
title: IDebugEngine2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f733dc1ad1ee3e87c5d28721a308c22f3fc2e0fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119165"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Collega un motore di debug (DE) a uno o più programmi. Chiamato dalla gestione del debug di sessione (SDM) quando DE è in esecuzione in-process in SDM.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parametri
`pProgram`\
[in] Matrice di oggetti [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresentano i programmi a cui connettersi. Si tratta di programmi di porta.

`rgpProgramNodes`\
[in] Matrice di oggetti [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che rappresentano i nodi di programma, uno per ogni programma. I nodi di programma in questa matrice rappresentano gli stessi programmi di `pProgram` . I nodi di programma vengono dati in modo che de possa identificare i programmi a cui connettersi.

`celtPrograms`\
[in] Numero di programmi e/o nodi di programma nelle `pProgram` `rgpProgramNodes` matrici e .

`pCallback`\
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da usare per inviare eventi di debug a SDM.

`dwReason`\
[in] Valore [dell'enumerazione ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) che specifica il motivo per il collegamento di questi programmi. Per altre informazioni, vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Esistono tre motivi per collegarsi a un programma, come indicato di seguito:

- `ATTACH_REASON_LAUNCH` indica che de è collegato al programma perché l'utente ha avviato il processo che lo contiene.

- `ATTACH_REASON_USER` indica che l'utente ha richiesto esplicitamente a DE di connettersi a un programma (o al processo che contiene un programma).

- `ATTACH_REASON_AUTO` indica che DE si sta connettendo a un programma specifico perché sta già debug di altri programmi in un determinato processo. Questa operazione è detta anche collegamento automatico.

  Quando questo metodo viene chiamato, de deve inviare questi eventi in sequenza:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (se non è già stato inviato per una particolare istanza del motore di debug)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Inoltre, se il motivo per il collegamento è `ATTACH_REASON_LAUNCH` , de deve inviare [l'evento IDebugEntryPointEvent2.](../../../extensibility/debugger/reference/idebugentrypointevent2.md)

   Una volta che DE ottiene [l'oggetto IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) corrispondente al programma sottoposto a debug, è possibile eseguire query per qualsiasi interfaccia privata.

   Prima di chiamare i metodi di un nodo di programma nella matrice specificata da o , la rappresentazione, se necessario, deve essere abilitata nell'interfaccia `pProgram` che rappresenta il nodo di `rgpProgramNodes` `IDebugProgram2` programma. In genere, tuttavia, questo passaggio non è necessario. Per altre informazioni, vedere Problemi [di sicurezza.](../../../extensibility/debugger/security-issues.md)

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
