---
description: Questa interfaccia enumera i punti di interruzione associati associati a un punto di interruzione in sospeso o a un evento associato al punto di interruzione.
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: efac05deb9d528b66f93d69cdd071113bb5d2b51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118372"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Questa interfaccia enumera i punti di interruzione associati associati a un punto di interruzione in sospeso o a un evento associato al punto di interruzione.

## <a name="syntax"></a>Sintassi

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia come parte del supporto per i punti di interruzione. Questa interfaccia deve essere implementata se sono supportati punti di interruzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiamate:

- [EnumBreakpoints per](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione attivati.

- [EnumBoundBreakpoints per](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione associati.

- [EnumBoundBreakpoints per](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione associati a tale punto di interruzione in sospeso.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugBoundBreakpoints2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera un numero specificato di punti di interruzione associati in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Ignora un numero specificato di punti di interruzione associati in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Ottiene il numero di punti di interruzione associati in un enumeratore.|

## <a name="remarks"></a>Commenti
 Visual Studio i punti di interruzione associati rappresentati da questa interfaccia per aggiornare la visualizzazione dei punti di interruzione nell'IDE.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
