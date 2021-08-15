---
description: Questa interfaccia consente all'analizzatore di espressioni (edizione Enterprise) di chiamare proprietà o metodi nelle istanze della classe di valori (ad esempio, System.Decimal) e di impostarne il valore senza chiamare Evaluate nel programma di cui è in corso il debug.
title: Oggetto IDebugManagedObject | Microsoft Docs
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
ms.openlocfilehash: 2cc541ddcfe09755288c41ef0c0ac09327a7054d9c5c7669527706220e098f5d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121451874"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Questa interfaccia consente all'analizzatore di espressioni (edizione Enterprise) di chiamare proprietà o metodi nelle istanze della classe di valori (ad esempio , ) e di impostarne il valore senza chiamare Evaluate sul programma di cui è in corso il `System.Decimal` debug. [](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)

## <a name="syntax"></a>Sintassi

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto di codice gestito, ad esempio una variabile.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Per ottenere questa interfaccia, chiamare [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) su [un IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta un'istanza di una classe di valori.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` l'interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Restituisce un'interfaccia che rappresenta l'oggetto di codice gestito e da cui è possibile ottenere qualsiasi interfaccia di codice gestito appropriata.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Imposta il valore di questo oggetto sul valore di un oggetto di codice gestito specificato.|

## <a name="remarks"></a>Commenti
 Un analizzatore di espressioni utilizza questa interfaccia per archiviare un oggetto di codice gestito in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Valuta](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
