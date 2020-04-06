---
title: Esempio di implementazione delle variabili locali Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713079"
---
# <a name="sample-implementation-of-locals"></a>Esempio di implementazione di gente del posto
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Di seguito è riportata una panoramica di come Visual Studio ottiene le variabili locali per un metodo dall'analizzatore di espressioni (EE):Following is an overview of how Visual Studio gets the locals for a method from the expression evaluator (EE):

1. Visual Studio chiama il motore di debug (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) per ottenere un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta tutte le proprietà dello stack frame, incluse le variabili locali.

2. `IDebugStackFrame2::GetDebugProperty`chiama [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) per ottenere un oggetto che descrive il metodo all'interno del quale si è verificato il punto di interruzione. Il DE fornisce un provider di simboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), un indirizzo ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) e un gestore di associazione ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty`chiama [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con `IDebugAddress` l'oggetto fornito per ottenere un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) che rappresenta il metodo contenente l'indirizzo specificato.

4. L'interfaccia `IDebugContainerField` viene eseguita una query per il [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaccia. È questa interfaccia che consente di accedere alle variabili locali del metodo.

5. `IDebugExpressionEvaluator::GetMethodProperty`crea un'istanza `CFieldProperty` di una classe (chiamata nell'esempio) che esegue l'interfaccia `IDebugProperty2` per rappresentare le variabili locali del metodo. `IDebugMethodField` L'oggetto viene `CFieldProperty` inserito in `IDebugSymbolProvider` `IDebugAddress`questo `IDebugBinder` oggetto insieme agli oggetti , e .

6. Quando `CFieldProperty` l'oggetto viene inizializzato, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) viene chiamato sull'oggetto `IDebugMethodField` per ottenere una struttura [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) che contiene tutte le informazioni visualizzabili sul metodo stesso.

7. `IDebugExpressionEvaluator::GetMethodProperty`restituisce `CFieldProperty` l'oggetto come `IDebugProperty2` oggetto.

8. Visual Studio chiama [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) `IDebugProperty2` sull'oggetto `guidFilterLocalsPlusArgs`restituito con il filtro , che restituisce un oggetto [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente le variabili locali del metodo. Questa enumerazione viene compilata dalle chiamate a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) ed [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio chiama [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) per ottenere una struttura [di DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) per ogni locale. Questa struttura contiene un `IDebugProperty2` puntatore a un'interfaccia per un locale.

10. Visual Studio chiama [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ogni locale per ottenere il nome, il valore e il tipo del locale. Queste informazioni vengono visualizzate nella finestra **Variabili locali.**

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementare GetMethodPropertyImplement GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Viene descritta un'implementazione di [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Enumerazione delle variabili locali](../../extensibility/debugger/enumerating-locals.md) Viene descritto come il motore di debug (DE) effettua una chiamata per enumerare le variabili locali o gli argomenti.

 [Ottenere le proprietà localiGet local properties](../../extensibility/debugger/getting-local-properties.md) Viene descritto come il DE effettua una chiamata per ottenere il nome, tipo e valore di uno o più variabili locali.

 [Ottenere valori localiGet local values](../../extensibility/debugger/getting-local-values.md) Viene illustrato come ottenere il valore del locale, che richiede i servizi di un oggetto binder fornito dal contesto di valutazione.

 [Valutare la gente del posto](../../extensibility/debugger/evaluating-locals.md) Viene illustrato come vengono valutate le variabili locali.

## <a name="related-sections"></a>Sezioni correlate
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Fornisce gli argomenti che vengono passati quando il DE chiama l'analizzatore di espressioni (EE).

 [Esempio MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) Viene illustrato un approccio di implementazione alla creazione di un analizzatore di espressioni per il linguaggio MyC.

## <a name="see-also"></a>Vedere anche
- [Visualizzazione di gente del posto](../../extensibility/debugger/displaying-locals.md)
