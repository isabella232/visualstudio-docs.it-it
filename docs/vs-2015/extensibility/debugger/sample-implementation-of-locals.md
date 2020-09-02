---
title: Implementazione di esempio di variabili locali | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e943fd7ba27fe21029bab4d818803186147476e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704894"
---
# <a name="sample-implementation-of-locals"></a>Implementazione di esempio di variabili locali
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ecco una panoramica del modo in cui Visual Studio ottiene le variabili locali per un metodo dall'analizzatore di espressioni (EE):  
  
1. Visual Studio chiama il (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) del motore di debug per ottenere un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta tutte le proprietà del stack frame, incluse le variabili locali.  
  
2. `IDebugStackFrame2::GetDebugProperty` chiama [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) per ottenere un oggetto che descrive il metodo in cui si è verificato il punto di interruzione. Il DE fornisce un provider di simboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), un indirizzo ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) e un Binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3. `IDebugExpressionEvaluator::GetMethodProperty` chiama [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con l' `IDebugAddress` oggetto fornito per ottenere un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) che rappresenta il metodo che contiene l'indirizzo specificato.  
  
4. `IDebugContainerField`Viene eseguita una query sull'interfaccia per l'interfaccia [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Si tratta di un'interfaccia che consente di accedere alle variabili locali del metodo.  
  
5. `IDebugExpressionEvaluator::GetMethodProperty` Crea un'istanza di una classe (chiamata `CFieldProperty` nell'esempio) che implementa l' `IDebugProperty2` interfaccia per rappresentare le variabili locali del metodo. L' `IDebugMethodField` oggetto viene inserito in questo `CFieldProperty` oggetto insieme agli `IDebugSymbolProvider` oggetti, `IDebugAddress` e `IDebugBinder` .  
  
6. Quando l' `CFieldProperty` oggetto viene inizializzato, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) viene chiamato sull' `IDebugMethodField` oggetto per ottenere una struttura [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) contenente tutte le informazioni visualizzabili sul metodo stesso.  
  
7. `IDebugExpressionEvaluator::GetMethodProperty` Restituisce l' `CFieldProperty` oggetto come `IDebugProperty2` oggetto.  
  
8. Visual Studio chiama [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sull'oggetto restituito `IDebugProperty2` con il filtro `guidFilterLocalsPlusArgs` . Viene restituito un oggetto [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente le variabili locali del metodo. Questa enumerazione viene compilata dalle chiamate a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) e [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio chiama [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) per ottenere una struttura di [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) per ogni locale. Questa struttura contiene un puntatore a un' `IDebugProperty2` interfaccia per un oggetto locale.  
  
10. Visual Studio chiama [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ogni locale per ottenere il nome, il valore e il tipo dell'oggetto locale. Si tratta delle informazioni visualizzate nella finestra **variabili locali** .  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Implementazione di GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Descrive un'implementazione di [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumerazione di variabili locali](../../extensibility/debugger/enumerating-locals.md)  
 Viene descritto come il motore di debug (DE) effettua una chiamata per enumerare variabili o argomenti locali.  
  
 [Recupero delle proprietà della variabile locale](../../extensibility/debugger/getting-local-properties.md)  
 Viene descritto in che modo il DE effettua una chiamata per ottenere il nome, il tipo e il valore di una o più variabili locali.  
  
 [Recupero dei valori della variabile locale](../../extensibility/debugger/getting-local-values.md)  
 Viene illustrato come ottenere il valore di local, che richiede i servizi di un oggetto Binder fornito dal contesto di valutazione.  
  
 [Valutazione di variabili locali](../../extensibility/debugger/evaluating-locals.md)  
 Viene illustrato come vengono valutate le variabili locali.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti che vengono passati quando il DE chiama l'analizzatore di espressioni (EE).  
  
 [Esempio MyCEE](https://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Viene illustrato un approccio di implementazione alla creazione di un analizzatore di espressioni per il linguaggio MyC.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)
