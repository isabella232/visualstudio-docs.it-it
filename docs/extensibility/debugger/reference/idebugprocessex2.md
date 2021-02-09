---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e8966be5c30bf2061fc1e03be6798279afbe8ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900168"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Questa interfaccia consente a gestione debug sessione (SDM) di notificare a un processo a cui si sta collegando o scollegando il processo.

## <a name="syntax"></a>Sintassi

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia sullo stesso oggetto dell'interfaccia [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) per:

- Supporto del rilevamento delle sessioni connesse a un processo

- Supporto della connessione automatica tra più motori di debug

  Il fornitore della porta personalizzata può implementare questa interfaccia se viene scelta.

## <a name="notes-for-callers"></a>Note per i chiamanti

- SDM chiama [QueryInterface](/cpp/atl/queryinterface) su un' `IDebugProcess2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugProcessEx2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa il processo che una sessione sta ora eseguendo il debug del processo.|
|[Scollega](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa il processo che una sessione non sta più eseguendo il debug del processo.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Aggiunge nodi di programma per un elenco di motori di debug.|

## <a name="remarks"></a>Commenti
 Questa interfaccia è privata tra il SDM e il processo.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
