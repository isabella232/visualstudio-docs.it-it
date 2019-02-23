---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c45b1bae11710063d089aeca61a9d20fb6e907a4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691098"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione. È un'estensione della [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Gestore di sessione di debug (SDM) è in genere implementa questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il motore di debug (DE) accede a questa interfaccia mediante la chiamata [QueryInterface](/cpp/atl/queryinterface) sull'interfaccia IDebugBreakpointRequest2 ricevuto in una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), il `IDebugBreakpointRequest3` interfaccia espone il metodo seguente.

|Metodo|Descrizione|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Ottiene le informazioni richieste punto di interruzione che descrive questa richiesta di punto di interruzione.|

## <a name="remarks"></a>Note
 Questa interfaccia viene utilizzata per fornire informazioni aggiuntive per la Germania attraverso il [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura. Queste informazioni aggiuntive includono l'ID fornitore del DE (sotto forma di un GUID), il nome di un punto di analisi e il nome di un vincolo di punto di interruzione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)