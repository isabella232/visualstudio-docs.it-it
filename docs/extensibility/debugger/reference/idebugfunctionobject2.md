---
title: Proprietà IDebugFunctionObject2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4150480d2e6686992d78727b6fed817da270145
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728436"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Rappresenta una funzione e migliora il [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni (EE) implementa questa interfaccia per rappresentare una funzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi di questa interfaccia rinviano quelli di IDebugFunctionObject nei modi seguenti:Methods of this interface defer those of **IDebugFunctionObject** in the following ways:

- Il **IDebugEvaluate** metodo accetta flag.

- Il **metodo CreateObject** accetta flag e un timeout.

- Il **CreateStringObjectWithLength** metodo accetta una lunghezza.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:This interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crea un oggetto che utilizza un costruttore date le impostazioni del flag di valutazione e un valore di timeout.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crea un oggetto stringa con la lunghezza specificata.|
|[Valutare](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Chiama la funzione e restituisce il valore risultante come oggetto.|

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
