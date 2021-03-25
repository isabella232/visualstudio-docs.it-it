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
ms.workload:
- vssdk
ms.openlocfilehash: 8788e7a78bcd4c03567e5d07c96a310fa6970fb1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054452"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il gestore di debug della sessione implementa in genere questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il motore di debug (DE) riceve questa interfaccia tramite una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) per creare un punto di interruzione in sospeso. Una chiamata a [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) può recuperare questa interfaccia da de.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugBreakpointRequest2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ottiene il tipo di posizione del punto di interruzione della richiesta del punto di interruzione.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ottiene le informazioni sulla richiesta del punto di interruzione che descrivono questa richiesta di interruzione.|

## <a name="remarks"></a>Commenti
 Dopo che il programma di cui è in corso il debug è stato caricato, una chiamata a [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) associa un punto di interruzione in sospeso alla posizione richiesta nel programma.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
