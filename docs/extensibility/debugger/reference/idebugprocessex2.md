---
description: Questa interfaccia consente al gestore di debug di sessione (SDM) di inviare una notifica a un processo che si sta collegando o scollegando dal processo.
title: Interfaccia IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4158f7f13f374e933bcf1ec64d40ecd16c85b40c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071902"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Questa interfaccia consente al gestore di debug di sessione (SDM) di inviare una notifica a un processo che si sta collegando o scollegando dal processo.

## <a name="syntax"></a>Sintassi

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia sullo stesso oggetto [dell'interfaccia IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) per:

- Supporto del rilevamento delle sessioni connesse a un processo

- Supporto del collegamento automatico tra più motori di debug

  Il fornitore di porte personalizzato può implementare questa interfaccia, se lo desidera.

## <a name="notes-for-callers"></a>Note per i chiamanti

- SDM chiama [QueryInterface](/cpp/atl/queryinterface) su `IDebugProcess2` un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProcessEx2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa il processo che una sessione sta ora debug del processo.|
|[Scollega](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa il processo che una sessione non esegue più il debug del processo.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Aggiunge nodi di programma per un elenco di motori di debug.|

## <a name="remarks"></a>Commenti
 Questa interfaccia è privata tra SDM e il processo.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
