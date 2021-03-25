---
description: Connette un motore di debug (DE) a un programma o a programmi.
title: 'IDebugEngine2:: alleghi | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38275cc623fcb8b30646c9d84ef194f584369ef2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093912"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Connette un motore di debug (DE) a un programma o a programmi. Chiamato da gestione debug sessione (SDM) quando il DE è in esecuzione in-process per SDM.

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
in Matrice di oggetti [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresentano i programmi da associare a. Si tratta di programmi porta.

`rgpProgramNodes`\
in Matrice di oggetti [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che rappresentano i nodi del programma, uno per ogni programma. I nodi del programma in questa matrice rappresentano gli stessi programmi di `pProgram` . I nodi del programma sono forniti in modo che il DE possa identificare i programmi a cui connettersi.

`celtPrograms`\
in Numero di programmi e/o nodi di programma nelle `pProgram` `rgpProgramNodes` matrici e.

`pCallback`\
in Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da utilizzare per inviare eventi di debug a SDM.

`dwReason`\
in Valore dell'enumerazione [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) che specifica il motivo per il fissaggio di questi programmi. Per altre informazioni, vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Esistono tre motivi per connettersi a un programma, come indicato di seguito:

- `ATTACH_REASON_LAUNCH` indica che il DE viene collegato al programma perché l'utente ha avviato il processo che lo contiene.

- `ATTACH_REASON_USER` indica che l'utente ha richiesto in modo esplicito il DE per connettersi a un programma (o al processo che contiene un programma).

- `ATTACH_REASON_AUTO` indica che il DE è associato a un particolare programma perché sta già eseguendo il debug di altri programmi in un determinato processo. Questa operazione è detta anche connessione automatica.

  Quando viene chiamato questo metodo, il DE deve inviare questi eventi in sequenza:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (se non è già stato inviato per una particolare istanza del motore di debug)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Inoltre, se il motivo per il fissaggio è `ATTACH_REASON_LAUNCH` , il de deve inviare l'evento [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .

   Una volta che il DE Ottiene l'oggetto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) corrispondente al programma di cui è in corso il debug, può essere sottoposto a query per qualsiasi interfaccia privata.

   Prima di chiamare i metodi di un nodo di programma nella matrice fornita da `pProgram` o `rgpProgramNodes` , la rappresentazione, se necessario, deve essere abilitata nell' `IDebugProgram2` interfaccia che rappresenta il nodo del programma. In genere, tuttavia, questo passaggio non è necessario. Per ulteriori informazioni, vedere [problemi di sicurezza](../../../extensibility/debugger/security-issues.md).

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
