---
title: IDebugBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6ebb698fc839a93547d15828b250bd436260e33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881035"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Questa interfaccia rappresenta le informazioni che descrivono un punto di interruzione associato.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i punti di interruzione. Questa interfaccia fornisce una descrizione di un punto di interruzione associato utilizzato dal gestore di debug della sessione quando un utente visualizza le proprietà di un punto di interruzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugBreakpointResolution2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo del punto di interruzione rappresentato da questa risoluzione.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni di risoluzione del punto di interruzione che descrivono questo punto di interruzione.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
