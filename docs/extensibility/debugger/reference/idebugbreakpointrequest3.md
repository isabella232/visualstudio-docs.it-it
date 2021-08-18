---
description: L'interfaccia IDebugBreakpointRequest3 rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione.
title: Oggetto IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3522bdfc122cdb684a95f2407dd1f373ce3b1f9c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072537"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione. Si tratta di [un'estensione di IDebugBreakpointRequest2.](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 La gestione del debug di sessione (SDM) implementa in genere questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il motore di debug accede a questa interfaccia chiamando [QueryInterface](/cpp/atl/queryinterface) sull'interfaccia IDebugBreakpointRequest2 ricevuta in una chiamata a [CreatePendingBreakpoint.](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugBreakpointRequest2,](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) `IDebugBreakpointRequest3` l'interfaccia espone il metodo seguente.

|Metodo|Descrizione|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Ottiene le informazioni sulla richiesta del punto di interruzione che descrivono la richiesta del punto di interruzione.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene usata per fornire informazioni aggiuntive a DE tramite la [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura . Queste informazioni aggiuntive includono l'ID fornitore di DE (sotto forma di GUID), il nome di un punto di analisi e il nome di un vincolo del punto di interruzione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
