---
title: Interfacce di valutazione delle espressioni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736950"
---
# <a name="expression-evaluation-interfaces"></a>Interfacce di valutazione delle espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Di seguito sono riportate le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfacce di valutazione delle espressioni per l'SDK di debug.

## <a name="discussion"></a>Discussione
 Queste interfacce vengono utilizzate per valutare le espressioni in uno stack di chiamate durante la modalità di interruzione. Vengono implementati solo per gli analizzatori di espressioni di runtime comuni (EE).

 Ogni interfaccia nella tabella mostra il componente che può implementarla dall'elenco seguente:Each interface in the table shows the component that can implement it from the following list:

- Motore di debug (DE)Debug Engine (DE)

- Analizzatore espressioni (EE)Expression Evaluator (EE)

- Visual Studio (VS)

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Rappresenta un alias numerico per una variabile.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Rappresenta un alias numerico per una variabile e consente a un analizzatore di espressioni (EE) di ottenere il dominio applicazione per l'alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Rappresenta un oggetto matrice.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Rappresenta un oggetto matrice gestita e consente a un analizzatore di espressioni (EE) di determinare l'indice di base (limiti inferiori) per la matrice.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Rappresenta un gestore di associazione che associa i simboli di debug agli indirizzi effettivi in memoria.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Uguale al [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaccia ma fornisce l'accesso a tipi, alias e visualizzatori personalizzati.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Rappresenta l'analizzatore di espressioni.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Rappresenta una versione avanzata di un analizzatore di espressioni (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Rappresenta un analizzatore di espressioni (EE) con una struttura ad albero del parser avanzata.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Rappresenta una funzione.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Rappresenta una funzione e migliora il [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Consente a un analizzatore di espressioni (EE) di visualizzare un messaggio nella finestra di output del debugger.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Rappresenta un oggetto di codice gestito.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaccia di base che rappresenta qualsiasi simbolo associato a un indirizzo di memoria.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Uguale a [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia ma fornisce l'accesso a informazioni aggiuntive.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Rappresenta un'espressione analizzata pronta per essere valutata.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Rappresenta un puntatore.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Rappresenta un puntatore in un albero di analisi ed estende il **IDebugPointerObject** interfaccia.|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Consente di modificare il valore di un tipo tramite un visualizzatore di tipo.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fornisce l'accesso a visualizzatori e visualizzatori di tipo personalizzati.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Consente di creare un oggetto [IEEVisualizerService.](../../../extensibility/debugger/reference/ieevisualizerservice.md)|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Rappresenta una raccolta di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti.|

## <a name="see-also"></a>Vedere anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Scrittura di un analizzatore di espressioni CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
