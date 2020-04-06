---
title: Proprietà IDebugProgramEngines2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722394"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Questa interfaccia viene utilizzata dai nodi di programma per specificare tutti i possibili motori di debug (DE) che possono eseguire il debug di questo programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un DE o un fornitore di porta personalizzato implementa questa interfaccia sullo stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per supportare la definizione di un DE specifico da utilizzare per un determinato programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` su un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugProgramEngines2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica tutte le possibili DE che possono eseguire il debug di questo programma.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Seleziona il DE da utilizzare per il debug di questo programma.|

## <a name="remarks"></a>Osservazioni
 Una volta scelto un DE dall'utente, tale scelta viene registrata con il nodo del programma chiamando [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Il motore selezionato diventa il motore restituito da [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
