---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55e7c73b720e326b823c3038928d7141ea732155
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352909"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Gestore di sessione di debug (SDM) è in genere implementa questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il motore di debug (DE) riceve questa interfaccia tramite una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) per creare un punto di interruzione in sospeso. Una chiamata a [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) possibile recuperarne il DE questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugBreakpointRequest2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ottiene il tipo di posizione del punto di interruzione di questa richiesta di punto di interruzione.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ottiene le informazioni richieste punto di interruzione che descrive questa richiesta di punto di interruzione.|

## <a name="remarks"></a>Note
 Dopo il programma sottoposto a debug è stato caricato, una chiamata a [associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) associa un punto di interruzione in sospeso per la località richiesta nel programma.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)