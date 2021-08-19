---
description: Questa interfaccia viene utilizzata dai nodi di programma per specificare tutti i possibili motori di debug che possono eseguire il debug di questo programma.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: eedc4dd60ce3fbd8581e91ee14404abbe6454a62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126414"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Questa interfaccia viene utilizzata dai nodi di programma per specificare tutti i possibili motori di debug che possono eseguire il debug di questo programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un de o un fornitore di porte personalizzato implementa questa interfaccia sullo stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per supportare la definizione di una de specifica da usare per un particolare programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su `IDebugProgramNode2` un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProgramEngines2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica tutti i possibili DE che possono eseguire il debug di questo programma.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Seleziona il de da usare per il debug di questo programma.|

## <a name="remarks"></a>Commenti
 Dopo che un deret viene scelto dall'utente, tale scelta viene registrata con il nodo del programma chiamando [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Il motore selezionato diventa il motore restituito [da GetEngineInfo.](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
