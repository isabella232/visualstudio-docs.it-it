---
description: Di seguito sono riportate le interfacce di valutazione delle espressioni per Visual Studio Debugging SDK.
title: Interfacce di valutazione delle espressioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 22110ea35cbac5bc2fbfca06448e7ece2e0fc7cf82b2a62e6f1d0ee835d38eae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434321"
---
# <a name="expression-evaluation-interfaces"></a>Interfacce di valutazione delle espressioni
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Di seguito sono riportate le interfacce di valutazione delle espressioni per [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l'SDK di debug.

## <a name="discussion"></a>Discussione
 Queste interfacce vengono usate per valutare le espressioni in uno stack di chiamate durante la modalità di interruzione. Vengono implementati solo per gli analizzatori di espressioni di runtime (edizione Enterprise).

 Ogni interfaccia nella tabella mostra il componente che può implementarlo dall'elenco seguente:

- Motore di debug (DE)

- Analizzatore di espressioni (edizione Enterprise)

- Visual Studio (VS)

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Rappresenta un alias numerico per una variabile.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Rappresenta un alias numerico per una variabile e consente a un analizzatore di espressioni (edizione Enterprise) di ottenere il dominio applicazione per l'alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Rappresenta un oggetto matrice.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Rappresenta un oggetto matrice gestita e consente a un analizzatore di espressioni (edizione Enterprise) di determinare l'indice di base (limiti inferiori) per la matrice.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Rappresenta uno binder che associa i simboli di debug agli indirizzi effettivi in memoria.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Uguale [all'interfaccia IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) ma fornisce l'accesso a tipi, alias e visualizzatori personalizzati.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Rappresenta l'analizzatore di espressioni.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Rappresenta una versione avanzata di un analizzatore di espressioni (edizione Enterprise).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Rappresenta un analizzatore di espressioni (edizione Enterprise) con un albero del parser avanzato.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Rappresenta una funzione.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Rappresenta una funzione e migliora [l'interfaccia IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Consente a un analizzatore di espressioni (edizione Enterprise) di visualizzare un messaggio nella finestra di output del debugger.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Rappresenta un oggetto di codice gestito.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaccia di base che rappresenta qualsiasi simbolo associato a un indirizzo di memoria.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Uguale [all'interfaccia IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) ma fornisce l'accesso a informazioni aggiuntive.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Rappresenta un'espressione analizzata pronta per la valutazione.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Rappresenta un puntatore.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Rappresenta un puntatore in un albero di analisi ed estende **l'interfaccia IDebugPointerObject.**|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Consente di modificare il valore di un tipo tramite un visualizzatore di tipi.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fornisce l'accesso ai visualizzatori personalizzati e ai visualizzatori di tipi.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Consente di creare un [oggetto IEEEVisualizerService.](../../../extensibility/debugger/reference/ieevisualizerservice.md)|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Rappresenta una raccolta di [oggetti IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)|

## <a name="see-also"></a>Vedi anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Scrittura di un analizzatore di espressioni CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
