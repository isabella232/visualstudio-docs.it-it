---
title: Proprietà IEnumDebugBoundBreakpoints2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717449"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Questa interfaccia enumera i punti di interruzione associati associati a un punto di interruzione in sospeso o a un evento associato a un punto di interruzione.

## <a name="syntax"></a>Sintassi

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del relativo supporto per i punti di interruzione. Questa interfaccia deve essere implementata se i punti di interruzione sono supportati.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamate di Visual Studio:

- [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione che sono stati attivati.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione che sono stati associati.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione associati a tale punto di interruzione in sospeso.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IEnumDebugBoundBreakpoints2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera un numero specificato di punti di interruzione associati in una sequenza di enumerazione.|
|[Saltare](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Ignora un numero specificato di punti di interruzione associati in una sequenza di enumerazione.|
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md) (Clona)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Ottiene il numero di punti di interruzione associati in un enumeratore.|

## <a name="remarks"></a>Osservazioni
 Visual Studio usa i punti di interruzione associati rappresentati da questa interfaccia per aggiornare la visualizzazione dei punti di interruzione nell'IDE.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
