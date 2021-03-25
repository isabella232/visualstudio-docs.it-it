---
description: Questa interfaccia rappresenta una posizione nello spazio degli indirizzi del computer in cui è in esecuzione il programma di cui è in corso il debug.
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a967c992fc55065c50dbbe173495e7c1199df59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058482"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Questa interfaccia rappresenta una posizione nello spazio degli indirizzi del computer in cui è in esecuzione il programma di cui è in corso il debug.

## <a name="syntax"></a>Sintassi

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un indirizzo in memoria.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) o [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) restituisce questa interfaccia. Inoltre, le chiamate a [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) e [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) restituiscono nuove copie di questa interfaccia dopo l'applicazione dell'operazione aritmetica appropriata.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugMemoryContext2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ottiene il nome visualizzabile dall'utente per questo contesto.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ottiene informazioni che descrivono questo contesto.|
|[Aggiungere](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Aggiunge un valore specificato all'indirizzo del contesto corrente per creare un nuovo contesto.|
|[Sottrarre](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Sottrae un valore specificato dall'indirizzo del contesto corrente per creare un nuovo contesto.|
|[Confronta](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Confronta due contesti nel modo indicato dai flag di confronto.|

## <a name="remarks"></a>Commenti
 La finestra **memoria** di Visual Studio chiama [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) per ottenere l' `IDebugMemoryContext2` interfaccia che contiene l'espressione valutata utilizzata per l'indirizzo di memoria. Questo contesto viene quindi passato a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) per specificare l'indirizzo per la lettura o la scrittura.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
