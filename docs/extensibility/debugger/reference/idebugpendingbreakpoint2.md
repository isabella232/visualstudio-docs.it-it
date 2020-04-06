---
title: Proprietà IDebugPendingBreakpoint2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725646"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Questa interfaccia rappresenta un punto di interruzione pronto per l'associazione a un percorso di codice.

## <a name="syntax"></a>Sintassi

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del relativo supporto per i punti di interruzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crea un punto di interruzione in sospeso da un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaccia. Una chiamata [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) a `IDebugBreakpoint2` Bind crea un'interfaccia che rappresenta un punto di interruzione associato nel programma.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugPendingBreakpoint2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se questo punto di interruzione in sospeso può essere associato a un percorso di codice.|
|[Associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa questo punto di interruzione in sospeso a uno o più percorsi di codice.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato di questo punto di interruzione in sospeso.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione utilizzata per creare questo punto di interruzione in sospeso.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Attiva/disattiva lo stato virtualizzato di questo punto di interruzione in sospeso.|
|[Abilitare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva/disattiva lo stato abilitato di questo punto di interruzione in sospeso.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Imposta o modifica la condizione associata a questo punto di interruzione in sospeso.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Imposta o modifica il numero di passaggi associato a questo punto di interruzione in sospeso.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da questo punto di interruzione in sospeso.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore risultanti da questo punto di interruzione in sospeso.|
|[Elimina](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina questo punto di interruzione in sospeso e tutti i punti di interruzione associati da esso.|

## <a name="remarks"></a>Osservazioni
 `IDebugPendingBreakpoint2`può essere considerato come un provider di tutte le informazioni necessarie per associare un punto di interruzione al codice che può essere applicato a uno o più programmi.

 Un punto di interruzione in sospeso può potenzialmente produrre più di un punto di interruzione associato. Ad esempio, un punto di interruzione in un modello di tipo C , potrebbe produrre un punto di interruzione associato per ogni istanza univoca di tale modello.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
