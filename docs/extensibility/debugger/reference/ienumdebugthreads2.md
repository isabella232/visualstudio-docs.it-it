---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9a7eae6a0a37f8bd1f530afe067f4766197591
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914107"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Questo Interfacc enumera i thread in esecuzione nella sessione di debug corrente.

## <a name="syntax"></a>Sintassi

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di thread in un programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i thread in tutti i programmi in esecuzione in un processo. Chiamare [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) per ottenere questa interfaccia che rappresenta un elenco di thread in esecuzione in un programma.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugThreads2`.

|Metodo|Descrizione|
|------------|-----------------|
|[avanti](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera un determinato numero di thread nella sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignora un determinato numero di thread in una sequenza di enumerazione.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione di quello corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Ottiene il numero di thread in un enumeratore.|

## <a name="remarks"></a>Note
 Visual Studio ottiene in genere questa interfaccia per aggiornare il **thread** finestra anche per ottenere il primo thread dell'elenco, per poter chiamare [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md), e [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)