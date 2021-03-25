---
description: Questa interfaccia viene utilizzata dai nodi del programma per specificare tutti i possibili motori di debug (DE) in grado di eseguire il debug del programma.
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0202185d760a1e3334996906807e5922fe61e0a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084220"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Questa interfaccia viene utilizzata dai nodi del programma per specificare tutti i possibili motori di debug (DE) in grado di eseguire il debug del programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore della porta DE o personalizzato implementa questa interfaccia sullo stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per supportare la definizione di una specifica de da usare per un programma specifico.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un' `IDebugProgramNode2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugProgramEngines2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica tutte le DEs possibili che possono eseguire il debug del programma.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Consente di selezionare il DE da usare per il debug del programma.|

## <a name="remarks"></a>Commenti
 Una volta scelto dall'utente, tale scelta viene registrata nel nodo del programma chiamando il [motore](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Il motore selezionato diventa il motore restituito da [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
