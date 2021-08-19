---
description: Questa interfaccia rappresenta un punto di interruzione pronto per l'associazione a una posizione del codice.
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 96de5582c4ae60c9775af5ca72e5a15b8a370a7e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160075"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Questa interfaccia rappresenta un punto di interruzione pronto per l'associazione a una posizione del codice.

## <a name="syntax"></a>Sintassi

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia come parte del supporto per i punti di interruzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [CreatePendingBreakpoint crea](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) un punto di interruzione in sospeso da [un'interfaccia IDebugBreakpointRequest2.](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Una chiamata a [Bind crea](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) `IDebugBreakpoint2` un'interfaccia che rappresenta un punto di interruzione associato nel programma.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugPendingBreakpoint2` .

|Metodo|Descrizione|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se questo punto di interruzione in sospeso può essere associato a una posizione del codice.|
|[Associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa questo punto di interruzione in sospeso a una o più posizioni del codice.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato di questo punto di interruzione in sospeso.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione utilizzata per creare questo punto di interruzione in sospeso.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Attiva o disattiva lo stato virtualizzato di questo punto di interruzione in sospeso.|
|[Abilita](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva o disattiva lo stato abilitato di questo punto di interruzione in sospeso.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Imposta o modifica la condizione associata a questo punto di interruzione in sospeso.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Imposta o modifica il numero di passaggi associato a questo punto di interruzione in sospeso.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da questo punto di interruzione in sospeso.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore risultanti da questo punto di interruzione in sospeso.|
|[Elimina](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina questo punto di interruzione in sospeso e tutti i punti di interruzione associati.|

## <a name="remarks"></a>Commenti
 `IDebugPendingBreakpoint2` può essere pensato come un provider di tutte le informazioni necessarie per associare un punto di interruzione al codice che può essere applicato a uno o più programmi.

 Un punto di interruzione in sospeso può produrre potenzialmente più di un punto di interruzione associato. Ad esempio, un punto di interruzione in un modello di tipo C++ potrebbe produrre un punto di interruzione associato per ogni istanza univoca di tale modello.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
