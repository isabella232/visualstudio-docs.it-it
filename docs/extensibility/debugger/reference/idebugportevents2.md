---
description: Questa interfaccia invia una notifica a un listener (in genere la gestione del debug della sessione [SDM] o un motore di debug) di creazione e distruzione di processi e programmi su una porta specifica.
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 50dadee6ac2e1d1a441796aac7ca49614b84bcdf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169470"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Questa interfaccia invia una notifica a un listener (in genere la gestione del debug della sessione [SDM] o un motore di debug) di creazione e distruzione di processi e programmi su una porta specifica. Queste informazioni possono essere usate per presentare una visualizzazione in tempo reale dei processi e dei programmi in esecuzione sulla porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa in genere questa interfaccia per ricevere notifiche sulla creazione e la distruzione di programmi. Un motore di debug può inoltre implementare questa interfaccia per restare in ascolto di tali eventi di porta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 È possibile eseguire query su tutte le interfacce [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) per un' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia. Il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metodo per `IDebugPortEvents2` viene quindi chiamato nell' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia per ottenere un' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia. Infine, il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metodo nell' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia viene chiamato per inviare gli eventi tramite il metodo dell' [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo di `IDebugPortEvents2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Invia eventi che descrivono la creazione e l'eliminazione di processi e programmi sulla porta.|

## <a name="remarks"></a>Commenti
 `IDebugPortEvents2` viene usato anche da SDM per eseguire il debug di programmi eseguiti in un processo di cui è già in corso il debug.

 Gli eventi porta vengono passati a SDM da questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
