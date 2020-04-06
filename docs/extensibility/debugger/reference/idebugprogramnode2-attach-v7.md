---
title: IDebugProgramNode2::Attach_V7 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722134"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Deprecato. NON UTILIZZARE.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Parametri

`pMDMProgram`\
[in] Il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia che rappresenta il programma a cui connettersi.

`pCallback`\
[in] Il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia da utilizzare per inviare eventi di debug al modello SDM.

`dwReason`\
[in] Valore dell'enumerazione [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) che specifica il motivo della connessione.

## <a name="return-value"></a>Valore restituito

Un'implementazione `E_NOTIMPL`deve sempre restituire .

## <a name="remarks"></a>Osservazioni

> [!WARNING]
> A partire da Visual Studio 2005, questo metodo `E_NOTIMPL`non viene più utilizzato e deve sempre restituire . Vedere il [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia per un approccio alternativo se il nodo del programma deve indicare `GUID`che non può essere collegato o se il nodo del programma è semplicemente l'impostazione del programma . In caso contrario, implementare il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo.

## <a name="prior-to-visual-studio-2005"></a>Prima di Visual Studio 2005

Questo metodo deve essere implementato solo se il DE viene eseguito nello spazio degli indirizzi del programma in fase di debug. In caso contrario, questo metodo deve restituire `S_FALSE`.

Quando questo metodo viene chiamato, il DE deve inviare il [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) oggetto evento, se non è già stato inviato per questa istanza del [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaccia, nonché il [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oggetti evento. L'oggetto evento [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) viene `dwReason` quindi `ATTACH_REASON_LAUNCH`inviato se il parametro è .

Il DE deve chiamare il [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto fornito dal [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) oggetto evento e deve `IDebugProgram2` archiviare il GUID del programma nei dati di istanza per l'oggetto implementato dal DE.

## <a name="see-also"></a>Vedere anche

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
