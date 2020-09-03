---
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727686"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia consente all'analizzatore di espressioni di chiamare proprietà o metodi nelle istanze della classe di valori (ad esempio, `System.Decimal` ) e di impostare il relativo valore senza chiamare [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) sul programma di cui è in corso il debug.

## <a name="syntax"></a>Sintassi

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto di codice gestito, ad esempio una variabile.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Per ottenere questa interfaccia, chiamare [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) su un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta un'istanza di una classe di valori.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), l' `IDebugManagedObject` interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Restituisce un'interfaccia che rappresenta l'oggetto codice gestito e da cui è possibile ottenere qualsiasi interfaccia di codice gestito appropriata.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Imposta il valore di questo oggetto sul valore di un oggetto di codice gestito specificato.|

## <a name="remarks"></a>Osservazioni
 Un analizzatore di espressioni usa questa interfaccia per archiviare un oggetto di codice gestito in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Valuta](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
