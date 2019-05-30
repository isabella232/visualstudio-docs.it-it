---
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c884f2794031d92add956bf4364824165ee1edfb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343933"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta un oggetto del puntatore.

## <a name="syntax"></a>Sintassi

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto del puntatore.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia può ottenere questa interfaccia tramite [QueryInterface](/cpp/atl/queryinterface) se il `IDebugObject` rappresenta un puntatore.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), il `IDebugPointerObject` interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ottiene l'oggetto a cui punta l'interfaccia.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ottiene il valore a cui punta l'interfaccia come una serie di byte consecutivi.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Imposta il valore a cui punta l'interfaccia da una serie di byte consecutivi.|

## <a name="remarks"></a>Note
 Un analizzatore di espressioni usa questa interfaccia per rappresentare un puntatore in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)