---
description: Questa interfaccia enumera i thread in esecuzione nella sessione di debug corrente.
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e2f291d02a9420b465681a0e75278d022e14b3cf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034786"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Questa interfaccia enumera i thread in esecuzione nella sessione di debug corrente.

## <a name="syntax"></a>Sintassi

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare un elenco di thread in un programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumThreads per](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) ottenere questa interfaccia che rappresenta un elenco di tutti i thread in tutti i programmi in esecuzione in un processo. Chiamare [EnumThreads per](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) ottenere questa interfaccia che rappresenta un elenco di thread in esecuzione in un programma.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugThreads2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera un numero specificato di thread nella sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignora un numero specificato di thread in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione di quello corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Ottiene il numero di thread in un enumeratore.|

## <a name="remarks"></a>Commenti
 Visual Studio in genere ottiene questa interfaccia  per aggiornare la finestra Thread e per ottenere il primo thread dell'elenco, per chiamare [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)e [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Eseguire](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
