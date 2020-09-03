---
title: IDebugErrorBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17b20d0f3545b0f7266ad6d0c6423d581233dd3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730077"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
Questa interfaccia rappresenta un punto di interruzione di errore o di avviso, ad esempio un percorso non valido, un'espressione non valida o i motivi per cui il punto di interruzione in sospeso non è stato associato (codice non ancora caricato e così via).

## <a name="syntax"></a>Sintassi

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug implementa questa interfaccia come parte del supporto per i punti di interruzione. Questa interfaccia viene utilizzata per segnalare problemi relativi all'associazione di un punto di interruzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) ottiene questa interfaccia. Questa interfaccia può essere restituita anche (come parte di un elenco rappresentato da un'interfaccia [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) ) da una chiamata a [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) o [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugErrorBreakpoint2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che ha causato l'errore.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione degli errori del punto di interruzione in cui viene descritto l'errore.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
