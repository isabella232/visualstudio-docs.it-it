---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a5ad34904a2f0bf02e5a2221f1ff73093012a41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916930"
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