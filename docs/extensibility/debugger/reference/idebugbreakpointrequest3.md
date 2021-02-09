---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6e42111ca0c8b357a7f8841511cf935694a30b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893061"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione. Si tratta di un'estensione di [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il gestore di debug della sessione implementa in genere questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il motore di debug (DE) accede a questa interfaccia chiamando [QueryInterface](/cpp/atl/queryinterface) sull'interfaccia IDebugBreakpointRequest2 ricevuta in una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), l' `IDebugBreakpointRequest3` interfaccia espone il metodo seguente.

|Metodo|Descrizione|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Ottiene le informazioni sulla richiesta del punto di interruzione che descrivono questa richiesta di interruzione.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene utilizzata per fornire informazioni aggiuntive a DE tramite la struttura [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) . Queste informazioni aggiuntive includono l'ID fornitore DE (sotto forma di GUID), il nome di un punto di analisi e il nome di un vincolo di punto di interruzione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
