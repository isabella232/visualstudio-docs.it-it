---
title: Interfacce di valutazione di espressioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbd7eaa37ba54757b4073f164b47e46a7d665267
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074401"
---
# <a name="expression-evaluation-interfaces"></a>Interfacce di valutazione delle espressioni
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Di seguito sono le interfacce di valutazione di espressioni per il [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debugging SDK.  
  
## <a name="discussion"></a>Discussione  
 Queste interfacce vengono usate per valutare le espressioni in uno stack di chiamate durante la modalità di interruzione. Essi sono state implementate solo per common language runtime gli analizzatori di espressioni (EE).  
  
 Ogni interfaccia nella tabella mostra il componente che può implementare nell'elenco seguente:  
  
- Eseguire il debug del motore (DE)  
  
- Analizzatore di espressioni (EE)  
  
- Visual Studio (VS)  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Rappresenta un alias per una variabile numerico.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Rappresenta un alias per una variabile numerico e consente un analizzatore di espressioni (EE) per ottenere il dominio dell'applicazione per l'alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Rappresenta un oggetto matrice.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Rappresenta una matrice gestita e consente un analizzatore di espressioni (EE) per determinare l'indice di base (inferiore) per la matrice.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Rappresenta uno strumento di associazione che associa i simboli per gli indirizzi effettivi nella memoria di debug.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Stesso come il [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaccia ma fornisce l'accesso a tipi, gli alias e i visualizzatori personalizzati.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Rappresenta l'analizzatore di espressioni.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Rappresenta una versione avanzata di un analizzatore di espressioni (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Rappresenta un analizzatore di espressioni (EE) con una struttura avanzata del parser.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Rappresenta una funzione.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Rappresenta una funzione e migliora la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Consente a un analizzatore di espressioni (EE) visualizzare un messaggio nella finestra di output del debugger.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Rappresenta un oggetto di codice gestito.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaccia di base che rappresenta qualsiasi simbolo associato a un indirizzo di memoria.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Stesso come il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia ma fornisce l'accesso a informazioni aggiuntive.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Rappresenta un'espressione analizzata pronta per essere valutata.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Rappresenta un puntatore.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Rappresenta un puntatore in un albero di analisi ed estende la **IDebugPointerObject** interfaccia.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Offre la possibilità di modificare il valore del tipo tramite un visualizzatore di tipi.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Consente di accedere ai visualizzatori personalizzati e visualizzatori di tipi.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Offre la possibilità di creare un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) oggetto.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Rappresenta una raccolta di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [La scrittura di un analizzatore di espressioni CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
