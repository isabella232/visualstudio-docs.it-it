---
description: Questa interfaccia notifica a un listener (in genere gestione del debug di sessione [SDM] o motore di debug) di creazione e distruzione di processi e programmi su una porta specifica.
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 571c82cbb84686dd863e431c9956aa077b16f976
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132977"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Questa interfaccia notifica a un listener (in genere gestione del debug di sessione [SDM] o motore di debug) di creazione e distruzione di processi e programmi su una porta specifica. Queste informazioni possono essere usate per presentare una visualizzazione in tempo reale dei processi e dei programmi in esecuzione sulla porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa in genere questa interfaccia per ricevere notifiche relative alla creazione e alla distruzione del programma. Un motore di debug può anche implementare questa interfaccia per restare in ascolto di tali eventi di porta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 È possibile eseguire query su tutte le interfacce [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) per <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> un'interfaccia. Il metodo <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> per viene quindi chiamato `IDebugPortEvents2` <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> nell'interfaccia per ottenere <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> un'interfaccia . Infine, viene <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> chiamato il metodo <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> nell'interfaccia per inviare gli eventi tramite il [metodo Event.](../../../extensibility/debugger/reference/idebugportevents2-event.md)

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo di `IDebugPortEvents2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Invia eventi che descrivono la creazione e la distruzione di processi e programmi sulla porta.|

## <a name="remarks"></a>Commenti
 `IDebugPortEvents2` viene usato anche da SDM per eseguire il debug di programmi eseguiti in un processo già in fase di debug.

 Gli eventi di porta vengono passati a SDM da questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
