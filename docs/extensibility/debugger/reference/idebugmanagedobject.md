---
description: Questa interfaccia consente all'analizzatore di espressioni (edizione Enterprise) di chiamare proprietà o metodi nelle istanze della classe di valori (ad esempio, System.Decimal) e di impostarne il valore senza chiamare Evaluate sul programma di cui è in corso il debug.
title: Interfaccia IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6cdf99a651f91d941aab00a732b6885300d092a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088471"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia consente all'analizzatore di espressioni (edizione Enterprise) di chiamare proprietà o metodi nelle istanze della classe di valori (ad esempio , ) e di impostarne il valore senza chiamare Evaluate sul programma di cui è in corso il `System.Decimal` debug. [](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)

## <a name="syntax"></a>Sintassi

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto di codice gestito, ad esempio una variabile.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Per ottenere questa interfaccia, chiamare [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) su [un oggetto IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta un'istanza di una classe di valori.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` l'interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Restituisce un'interfaccia che rappresenta l'oggetto codice gestito e da cui è possibile ottenere qualsiasi interfaccia del codice gestito appropriata.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Imposta il valore di questo oggetto sul valore di un oggetto di codice gestito specificato.|

## <a name="remarks"></a>Commenti
 Un analizzatore di espressioni usa questa interfaccia per archiviare un oggetto di codice gestito in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Valuta](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
