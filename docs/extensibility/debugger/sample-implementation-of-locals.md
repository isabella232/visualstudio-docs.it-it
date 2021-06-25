---
title: Esempio di implementazione di variabili | Microsoft Docs
description: Informazioni su Visual Studio le variabili locali per un metodo dall'analizzatore di espressioni in questo articolo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ac52f1524c4be2e4a7afcbd21fb437977fb663e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902280"
---
# <a name="sample-implementation-of-locals"></a>Implementazione di esempio di variabili locali
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Di seguito è riportata una panoramica Visual Studio ottiene le variabili locali per un metodo dall'analizzatore di espressioni (EE):

1. Visual Studio chiama [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) (DE) del motore di debug per ottenere un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta tutte le proprietà del stack frame, incluse le variabili locali.

2. `IDebugStackFrame2::GetDebugProperty` chiama [GetMethodProperty per](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) ottenere un oggetto che descrive il metodo all'interno del quale si è verificato il punto di interruzione. Il de fornisce un provider di simboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), un indirizzo ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) e un binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` chiama [GetContainerField con](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) l'oggetto `IDebugAddress` fornito per ottenere un oggetto [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) che rappresenta il metodo contenente l'indirizzo specificato.

4. Viene `IDebugContainerField` eseguita una query sull'interfaccia [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Si tratta di questa interfaccia che consente l'accesso alle variabili locali del metodo.

5. `IDebugExpressionEvaluator::GetMethodProperty` crea un'istanza di una classe `CFieldProperty` (chiamata nell'esempio) che esegue `IDebugProperty2` l'interfaccia per rappresentare le variabili locali del metodo. `IDebugMethodField`L'oggetto viene inserito in questo oggetto insieme agli oggetti , e `CFieldProperty` `IDebugSymbolProvider` `IDebugAddress` `IDebugBinder` .

6. Quando `CFieldProperty` l'oggetto viene inizializzato, viene chiamato [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) sull'oggetto per ottenere una struttura FIELD_INFO contenente tutte le informazioni visualizzabili `IDebugMethodField` sul metodo stesso. [](../../extensibility/debugger/reference/field-info.md)

7. `IDebugExpressionEvaluator::GetMethodProperty` restituisce `CFieldProperty` l'oggetto come `IDebugProperty2` oggetto .

8. Visual Studio [chiama EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sull'oggetto restituito con il filtro , che restituisce un oggetto `IDebugProperty2` `guidFilterLocalsPlusArgs` [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente le variabili locali del metodo. Questa enumerazione viene compilata dalle chiamate a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) ed [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio chiama [Next per](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) ottenere una [struttura DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) per ogni locale. Questa struttura contiene un puntatore a `IDebugProperty2` un'interfaccia per un oggetto locale.

10. Visual Studio chiama [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ogni oggetto locale per ottenere il nome, il valore e il tipo dell'oggetto locale. Queste informazioni vengono visualizzate nella **finestra** Variabili locali.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementare GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Descrive un'implementazione di [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Enumerare le variabili locali](../../extensibility/debugger/enumerating-locals.md) Viene descritto come il motore di debug effettua una chiamata per enumerare argomenti o variabili locali.

 [Ottenere le proprietà locali](../../extensibility/debugger/getting-local-properties.md) Descrive il modo in cui de effettua una chiamata per ottenere il nome, il tipo e il valore di una o più variabili locali.

 [Ottenere valori locali](../../extensibility/debugger/getting-local-values.md) Viene illustrato come ottenere il valore dell'oggetto locale, che richiede i servizi di un oggetto binder specificato dal contesto di valutazione.

 [Valutare le variabili locali](../../extensibility/debugger/evaluating-locals.md) Viene illustrato come vengono valutate le variabili locali.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Fornisce gli argomenti passati quando de chiama l'analizzatore di espressioni (EE).

 [Esempio myCEE](/previous-versions/) Illustra un approccio di implementazione alla creazione di un analizzatore di espressioni per il linguaggio MyC.

## <a name="see-also"></a>Vedere anche
- [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)