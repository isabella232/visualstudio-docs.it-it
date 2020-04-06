---
title: Proprietà IDebugBoundBreakpoint2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d22b10085baefeb3a0286c1b4edcb5876c0dac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735419"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Questa interfaccia rappresenta un punto di interruzione associato a un percorso di codice.

## <a name="syntax"></a>Sintassi

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del relativo supporto per i punti di interruzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea questa interfaccia. Anche le chiamate a [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) e [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) possono ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugBoundBreakpoint2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso da cui è stato creato il punto di interruzione associato specificato.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ottiene lo stato di questo punto di interruzione associato.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Ottiene il numero di passaggi corrente per questo punto di interruzione associato.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione del punto di interruzione che descrive questo punto di interruzione.|
|[Abilitare](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Abilita o disabilita il punto di interruzione.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Imposta il numero di passaggi per questo punto di interruzione associato.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Imposta o modifica la condizione associata a questo punto di interruzione associato.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Imposta o modifica il numero di passaggi associato a questo punto di interruzione associato.|
|[Elimina](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina il punto di interruzione.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
