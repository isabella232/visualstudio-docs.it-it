---
description: Questa interfaccia rappresenta un oggetto puntatore.
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af6b8f6022a9363eb5391d6f0519603fa48668c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087600"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta un oggetto puntatore.

## <a name="syntax"></a>Sintassi

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto puntatore.

## <a name="notes-for-callers"></a>Note per i chiamanti
 L'interfaccia [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) può ottenere questa interfaccia utilizzando [QueryInterface](/cpp/atl/queryinterface) se `IDebugObject` rappresenta un puntatore.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), l' `IDebugPointerObject` interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ottiene l'oggetto al quale punta l'interfaccia.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ottiene il valore al quale l'interfaccia punta come una serie di byte consecutivi.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Imposta il valore su cui l'interfaccia punta da una serie di byte consecutivi.|

## <a name="remarks"></a>Commenti
 Un analizzatore di espressioni usa questa interfaccia per rappresentare un puntatore in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
