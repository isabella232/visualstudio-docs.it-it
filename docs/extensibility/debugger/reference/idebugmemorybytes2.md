---
description: Questa interfaccia rappresenta i byte di memoria.
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: add2f353b432d5a7a935a7206ece2113382182ca06aa0755c084fe8123fd7298
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417093"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Questa interfaccia rappresenta i byte di memoria.

## <a name="syntax"></a>Sintassi

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare i byte in memoria.

## <a name="notes-for-callers"></a>Note per i chiamanti
- [GetMemoryBytes restituisce questa](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) interfaccia per fornire l'accesso alla memoria di sistema. [GetMemoryBytes e](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) restituiscono questa interfaccia per fornire l'accesso ai byte di un oggetto.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugMemoryBytes2` .

|Metodo|Descrizione|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Legge una sequenza di byte, a partire da una posizione specificata.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Scrive `dwCount` byte, a partire da `pStartContext` .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Ottiene le dimensioni, in byte, della memoria rappresentata da questa interfaccia.|

## <a name="remarks"></a>Commenti
 Per le proprietà, [un'interfaccia IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta una matrice fornisce un'interfaccia `IDebugMemoryBytes2` per accedere ai valori in tale matrice.

 Visual Studio memory **view** chiama [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) per recuperare un'interfaccia `IDebugMemoryBytes2` per l'accesso alla memoria di sistema. L'indirizzo a cui accedere viene ottenuto analizzando l'espressione immessa come indirizzo nella visualizzazione memoria e quindi valutando l'espressione analizzata usando [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere `IDebugProperty2` un'interfaccia. Una chiamata a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) restituisce [LDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che descrive l'indirizzo di memoria. Questo contesto di memoria viene quindi passato [a ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt.](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
