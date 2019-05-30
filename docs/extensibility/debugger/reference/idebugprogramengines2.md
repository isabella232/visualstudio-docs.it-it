---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b45cbe8cd1b68e1681b07fcdf1fc715973a11295
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325255"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Questa interfaccia viene utilizzata dai nodi di programma per specificare tutti i possibili motori di debug (DE) che è possono eseguire il debug di questo programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un CRI o un fornitore di porte personalizzato implementa questa interfaccia nello stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) a consente di stabilire un CRI specifico da utilizzare per un particolare programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProgramNode2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugProgramEngines2`.

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica tutte le possibili DEs che è possibile eseguire il debug di questo programma.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Seleziona il DE da utilizzare per il debug di questo programma.|

## <a name="remarks"></a>Note
 Una volta un CRI scelto dall'utente, questa scelta è registrata con il nodo di programma chiamando [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Il motore selezionato diventa il motore restituito dal [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)