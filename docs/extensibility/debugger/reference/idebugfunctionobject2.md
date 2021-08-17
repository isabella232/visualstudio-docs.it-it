---
description: Rappresenta una funzione e migliora l'interfaccia IDebugFunctionObject.
title: Interfaccia IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9bc2ebc0422dcffeb682f7ac9eb02216d5adf6505b1799d6f33c22e192aa184c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389774"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Rappresenta una funzione e migliora [l'interfaccia IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="syntax"></a>Sintassi

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni (edizione Enterprise) implementa questa interfaccia per rappresentare una funzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi di questa interfaccia rinviano **quelli di IDebugFunctionObject** nei modi seguenti:

- Il **metodo IDebugEvaluate** accetta flag.

- Il **metodo CreateObject** accetta flag e un timeout.

- Il **metodo CreateStringObjectWithLength** accetta una lunghezza.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crea un oggetto che utilizza un costruttore in base alle impostazioni del flag di valutazione e a un valore di timeout.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crea un oggetto stringa con la lunghezza specificata.|
|[Valuta](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Chiama la funzione e restituisce il valore risultante come oggetto .|

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
