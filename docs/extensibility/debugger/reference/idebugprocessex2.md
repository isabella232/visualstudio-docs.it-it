---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0b29d88387ccb2ed711f1a000bf7bb00a34dd01
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084258"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Questa interfaccia consente la sessione di debug manager (SDM) notifica di un processo che viene collegamento a o lo scollegamento dal processo.

## <a name="syntax"></a>Sintassi

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia sull'oggetto stesso come il [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaccia al fine di:

- Rilevamento di supporto di sessioni connesse a un processo

- Supporto della connessione automatica tra più motori di debug

  Il fornitore della porta personalizzate possa implementare questa interfaccia se sceglie.

## <a name="notes-for-callers"></a>Note per i chiamanti

- Le chiamate SDM [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProcess2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugProcessEx2`.

|Metodo|Descrizione|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa il processo di una sessione è ora il debug del processo.|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa il processo che una sessione di debug non è più il processo.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Consente di aggiungere nodi di programma per un elenco dei motori di debug.|

## <a name="remarks"></a>Note
 Questa interfaccia è privata tra il modello SDM e il processo.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)