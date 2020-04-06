---
title: Proprietà IDebugBreakpointResolution2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb5e4f9e32017cfb493aae00a24f9f8184605d1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734741"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Questa interfaccia rappresenta le informazioni che descrivono un punto di interruzione associato.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del relativo supporto per i punti di interruzione. Questa interfaccia fornisce una descrizione di un punto di interruzione associato che il gestore di debug della sessione utilizza quando un utente visualizza le proprietà di un punto di interruzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugBreakpointResolution2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo del punto di interruzione rappresentato da questa risoluzione.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni sulla risoluzione del punto di interruzione che descrivono questo punto di interruzione.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
