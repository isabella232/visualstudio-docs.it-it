---
title: Proprietà IDebugMemoryContext2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727422"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Questa interfaccia rappresenta una posizione nello spazio degli indirizzi del computer che esegue il programma sottoposto a debug.

## <a name="syntax"></a>Sintassi

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un indirizzo in memoria.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) o [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) restituisce questa interfaccia. Inoltre, le chiamate a [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) e [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) restituiscono nuove copie di questa interfaccia dopo l'applicazione dell'operazione aritmetica appropriata.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugMemoryContext2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ottiene il nome visualizzabile dall'utente per questo contesto.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ottiene informazioni che descrivono questo contesto.|
|[Aggiungere](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Aggiunge un valore specificato all'indirizzo del contesto corrente per creare un nuovo contesto.|
|[Sottrarre](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Sottrae un valore specificato dall'indirizzo del contesto corrente per creare un nuovo contesto.|
|[Confronta](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Confronta due contesti nel modo indicato dai flag di confronto.|

## <a name="remarks"></a>Osservazioni
 La finestra **Memoria** di Visual Studio chiama `IDebugMemoryContext2` [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) per ottenere l'interfaccia che contiene l'espressione valutata utilizzata per l'indirizzo di memoria. Questo contesto viene quindi passato a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) per specificare l'indirizzo da leggere o scrivere.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
