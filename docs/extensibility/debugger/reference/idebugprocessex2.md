---
title: Proprietà IDebugProcessEx2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723334"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Questa interfaccia consente al gestore di debug della sessione (SDM) notificare a un processo che si sta connettendo o scollegando dal processo.

## <a name="syntax"></a>Sintassi

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porta personalizzato implementa questa interfaccia sullo stesso oggetto di IDebugProcess2 interfaccia per:A custom port supplier implements this interface on the same object as the [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interface in order to:

- Supportare il monitoraggio delle sessioni connesse a un processoSupport tracking of sessions connected to a process

- Supporto dell'associazione automatica tra più motori di debugSupport auto-attach across multiple debug engines

  Il fornitore della porta personalizzata può implementare questa interfaccia, se lo desidera.

## <a name="notes-for-callers"></a>Note per i chiamanti

- Il modello SDM chiama `IDebugProcess2` [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugProcessEx2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa il processo che una sessione sta eseguendo il debug del processo.|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa il processo che una sessione non esegue più il debug del processo.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Aggiunge nodi di programma per un elenco di motori di debug.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia è privata tra il modello SDM e il processo.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
