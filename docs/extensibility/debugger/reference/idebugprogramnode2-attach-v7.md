---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90b162476872700ee0ec69a3bb9e6e575e7862a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351176"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> DEPRECATO. NON USARE.

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
[in] Il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia da utilizzare per inviare gli eventi di debug per il modello SDM.

`dwReason`\
[in] Un valore compreso il [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumerazione che specifica il motivo per il collegamento.

## <a name="return-value"></a>Valore restituito

Un'implementazione deve sempre restituire `E_NOTIMPL`.

## <a name="remarks"></a>Note

> [!WARNING]
> A partire da Visual Studio 2005, questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL`. Vedere le [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia di amministrazione di un approccio alternativo se il nodo programma deve indicare non è possibile collegare o se il nodo di programma è semplicemente l'impostazione del programma `GUID`. In caso contrario, implementare il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) (metodo).

## <a name="prior-to-visual-studio-2005"></a>Prima di Visual Studio 2005

Questo metodo deve essere implementata solo se la Germania viene eseguito nello spazio degli indirizzi del programma in fase di debug. In caso contrario, questo metodo deve restituire `S_FALSE`.

Quando questo metodo viene chiamato, la Germania è necessario inviare il [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) oggetto dell'evento, se non si sono già stato inviato per questa istanza del [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaccia, così come il [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oggetti evento. Il [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) oggetto dell'evento viene inviato se le `dwReason` parametro `ATTACH_REASON_LAUNCH`.

La Germania è necessario chiamare il [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo sul [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto fornito dal [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventi dell'oggetto e devono archiviare il GUID del programma nei dati dell'istanza per il `IDebugProgram2` oggetto implementato dal DE.

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