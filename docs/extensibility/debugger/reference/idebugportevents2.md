---
title: Proprietà IDebugPortEvents2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725182"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Questa interfaccia notifica a un listener (in genere il gestore di sessione di debug [SDM] o un motore di debug) di processo e programma creazione e distruzione su una porta specifica. Queste informazioni possono essere utilizzate per presentare una visualizzazione in tempo reale dei processi e dei programmi in esecuzione sulla porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa in genere questa interfaccia per ricevere notifiche sulla creazione e l'eliminazione del programma. Un motore di debug può anche implementare questa interfaccia per l'ascolto di tali eventi di porta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Tutte le interfacce [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) possono <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> essere sottoposte a query per un'interfaccia. Quindi <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> il `IDebugPortEvents2` metodo per <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> viene chiamato <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> nell'interfaccia per ottenere un'interfaccia. Infine, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> il metodo <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> nell'interfaccia viene chiamato per inviare gli eventi tramite il [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md) metodo.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene `IDebugPortEvents2`illustrato il metodo di .

|Metodo|Descrizione|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Invia eventi che descrivono la creazione e la distruzione di processi e programmi sulla porta.|

## <a name="remarks"></a>Osservazioni
 `IDebugPortEvents2`viene inoltre utilizzato dal modello SDM per eseguire il debug di programmi in esecuzione in un processo già sottoposto a debug.

 Gli eventi di porta vengono passati al file SDM da questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
