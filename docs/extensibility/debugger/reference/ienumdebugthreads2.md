---
title: Proprietà IEnumDebugThreads2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715094"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Questa interfaccia enumera i thread in esecuzione nella sessione di debug corrente.

## <a name="syntax"></a>Sintassi

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di thread in un programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i thread in tutti i programmi in esecuzione in un processo. Chiamare [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) per ottenere questa interfaccia che rappresenta un elenco di thread in esecuzione in un programma.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IEnumDebugThreads2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera un numero specificato di thread nella sequenza di enumerazione.|
|[Saltare](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignora un numero specificato di thread in una sequenza di enumerazione.|
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md) (Clona)|Crea un enumeratore che contiene lo stesso stato di enumerazione di quello corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Ottiene il numero di thread in un enumeratore.|

## <a name="remarks"></a>Osservazioni
 Visual Studio ottiene in genere questa interfaccia per aggiornare la finestra **Thread** e per ottenere il primo thread dell'elenco, al fine di chiamare [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)e [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continuare](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Eseguire](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
