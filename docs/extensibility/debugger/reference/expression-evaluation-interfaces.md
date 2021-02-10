---
title: Interfacce di valutazione delle espressioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a048d11b09ee873a2f5a11e35db78f68df6ad680
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936938"
---
# <a name="expression-evaluation-interfaces"></a>Interfacce di valutazione delle espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Di seguito sono riportate le interfacce di valutazione delle espressioni per l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK di debug.

## <a name="discussion"></a>Discussione
 Queste interfacce vengono usate per valutare le espressioni in uno stack di chiamate durante la modalità di interruzioni. Vengono implementate solo per gli analizzatori di espressioni (EE) di Common Language Runtime.

 Ogni interfaccia della tabella mostra il componente che può implementarlo dall'elenco seguente:

- Motore di debug (DE)

- Analizzatore di espressioni (EE)

- Visual Studio (VS)

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Rappresenta un alias numerico per una variabile.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Rappresenta un alias numerico per una variabile e consente a un analizzatore di espressioni (EE) di ottenere il dominio applicazione per l'alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Rappresenta un oggetto matrice.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Rappresenta un oggetto matrice gestita e consente a un analizzatore di espressioni (EE) di determinare l'indice di base (limiti inferiori) per la matrice.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Rappresenta uno strumento di associazione che associa i simboli di debug agli indirizzi effettivi in memoria.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Uguale all'interfaccia [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , ma fornisce l'accesso a tipi, alias e visualizzatori personalizzati.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Rappresenta l'analizzatore di espressioni.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Rappresenta una versione migliorata di un analizzatore di espressioni (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Rappresenta un analizzatore di espressioni (EE) con un albero del parser migliorato.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Rappresenta una funzione.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Rappresenta una funzione e migliora l'interfaccia [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Consente a un analizzatore di espressioni (EE) di visualizzare un messaggio nella finestra di output del debugger.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Rappresenta un oggetto di codice gestito.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaccia di base che rappresenta qualsiasi simbolo associato a un indirizzo di memoria.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Uguale all'interfaccia [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , ma fornisce l'accesso a informazioni aggiuntive.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Rappresenta un'espressione analizzata pronta per la valutazione.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Rappresenta un puntatore.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Rappresenta un puntatore in una struttura ad albero di analisi ed estende l'interfaccia **IDebugPointerObject** .|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Offre la possibilità di modificare il valore di un tipo tramite un visualizzatore di tipi.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Consente di accedere ai visualizzatori personalizzati e ai visualizzatori di tipi.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Fornisce la possibilità di creare un oggetto [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) .|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Rappresenta una raccolta di oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .|

## <a name="see-also"></a>Vedi anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Scrittura di un analizzatore di espressioni CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
