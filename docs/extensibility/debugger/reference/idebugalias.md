---
description: Rappresenta un alias numerico per una variabile.
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5eb9f1d4bc493779d9b42a984c8fc1577e2fe66
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059145"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Rappresenta un alias numerico per una variabile. Un alias è semplicemente un nome diverso per una variabile.

## <a name="syntax"></a>Sintassi

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni (EE) implementa questa interfaccia per supportare gli alias numerici per le variabili.

## <a name="notes-for-callers"></a>Note per i chiamanti
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) crea un alias per un oggetto specifico. Per cercare gli alias, usare [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) o [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 I metodi seguenti sono definiti nell' `IDebugAlias` interfaccia.

|Metodo|Descrizione|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Ottiene l'oggetto a cui si riferisce questo alias.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Ottiene il nome dell'alias.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera un' `ICorDebugValue` interfaccia che fornisce accesso alle informazioni sul codice gestito relative a questo oggetto (solo codice gestito).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Contrassegna questo alias come non più utilizzato.|

## <a name="remarks"></a>Commenti
 Un alias è un numero decimale in formato stringa seguito dal carattere #, ad esempio 1001 #.

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
