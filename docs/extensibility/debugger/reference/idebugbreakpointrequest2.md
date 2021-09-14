---
description: L'interfaccia IDebugBreakPointRequest2 rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione.
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: df0b17c6a1696315e328121eaa305a65defe40ea
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636443"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 La gestione debug di sessione (SDM) implementa in genere questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il motore di debug riceve questa interfaccia tramite una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) per creare un punto di interruzione in sospeso. Una chiamata a [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) può recuperare questa interfaccia dal de.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugBreakpointRequest2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ottiene il tipo di posizione del punto di interruzione di questa richiesta del punto di interruzione.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ottiene le informazioni sulla richiesta del punto di interruzione che descrivono questa richiesta del punto di interruzione.|

## <a name="remarks"></a>Commenti
 Dopo il caricamento del programma in fase di debug, una chiamata a [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) associa un punto di interruzione in sospeso al percorso richiesto nel programma.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
