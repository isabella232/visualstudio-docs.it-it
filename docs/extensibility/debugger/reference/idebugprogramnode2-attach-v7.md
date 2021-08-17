---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
description: Questo metodo di interfaccia è un metodo di collegamento obsoleto e deprecato usato prima Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e8da72cb7dd087bc798aa3e998bb672d7f1b736c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029996"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Deprecato. NON USARE.

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
[in] Interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma a cui connettersi.

`pCallback`\
[in] Interfaccia [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da usare per inviare eventi di debug a SDM.

`dwReason`\
[in] Valore [dell'enumerazione ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) che specifica il motivo del collegamento.

## <a name="return-value"></a>Valore restituito

Un'implementazione deve sempre restituire `E_NOTIMPL` .

## <a name="remarks"></a>Commenti

> [!WARNING]
> A Visual Studio 2005, questo metodo non viene più usato e deve restituire sempre `E_NOTIMPL` . Vedere [l'interfaccia IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) per un approccio alternativo se il nodo del programma deve indicare che non può essere collegato a o se il nodo del programma sta semplicemente impostando il programma `GUID` . In caso contrario, implementare [il metodo Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="prior-to-visual-studio-2005"></a>Prima di Visual Studio 2005

Questo metodo deve essere implementato solo se de viene eseguito nello spazio degli indirizzi del programma di cui viene eseguito il debug. In caso contrario, questo metodo deve restituire `S_FALSE` .

Quando viene chiamato questo metodo, il DE deve inviare l'oggetto evento [IDebugEngineCreateEvent2,](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) se non è già stato inviato per questa istanza dell'interfaccia [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) nonché gli oggetti evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e [IDebugLoadCompleteEvent2.](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) [L'oggetto evento IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) viene quindi inviato se il `dwReason` parametro è `ATTACH_REASON_LAUNCH` .

De deve chiamare il [metodo GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sull'oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) fornito dall'oggetto evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e deve archiviare il GUID del programma nei dati dell'istanza per l'oggetto implementato da `IDebugProgram2` DE.

## <a name="see-also"></a>Vedi anche

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
