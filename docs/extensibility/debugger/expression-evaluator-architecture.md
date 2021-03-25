---
title: Architettura dell'analizzatore di espressioni | Microsoft Docs
description: Informazioni sull'integrazione di un linguaggio proprietario nel pacchetto di debug di Visual Studio, tra cui l'analizzatore di espressioni e le interfacce del provider di simboli/Binder.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31b382f4765a115657fb213f39530e88e4008c95
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094731"
---
# <a name="expression-evaluator-architecture"></a>Architettura dell'analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'integrazione di un linguaggio proprietario nel pacchetto di debug di Visual Studio significa che è necessario impostare le interfacce dell'analizzatore di espressioni (EE) richieste e chiamare le interfacce del provider di simboli Common Language Runtime (SP) e del gestore di associazione. Gli oggetti SP e Binder, insieme all'indirizzo di esecuzione corrente, sono il contesto in cui vengono valutate le espressioni. Le informazioni che queste interfacce producono e utilizzano rappresentano i concetti chiave dell'architettura di un EE.

## <a name="overview"></a>Panoramica

### <a name="parse-the-expression"></a>Analizzare l'espressione
 Quando si esegue il debug di un programma, le espressioni vengono valutate per diversi motivi, ma sempre quando il programma di cui è in corso il debug è stato interrotto in corrispondenza di un punto di interruzione (un punto di interruzione inserito dall'utente o uno causato da un'eccezione). Attualmente, quando Visual Studio ottiene una stack frame, come rappresentata dall'interfaccia [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , dal motore di debug (de). Visual Studio chiama quindi [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere l'interfaccia [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Questa interfaccia rappresenta un contesto in cui è possibile valutare le espressioni; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) è il punto di ingresso del processo di valutazione. Fino a questo punto, tutte le interfacce vengono implementate dal DE.

 Quando `IDebugExpressionContext2::ParseText` viene chiamato, l'oggetto de crea un'istanza di EE associato alla lingua del file di origine in cui si è verificato il punto di interruzione (anche la de crea un'istanza di SH a questo punto). EE è rappresentato dall'interfaccia [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) . Il DE chiama quindi [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per convertire l'espressione (in formato testo) in un'espressione analizzata, pronta per la valutazione. Questa espressione analizzata è rappresentata dall'interfaccia [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) . L'espressione viene in genere analizzata e non valutata in questo punto.

 Il DE crea un oggetto che implementa l'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , inserisce l' `IDebugParsedExpression` oggetto nell' `IDebugExpression2` oggetto e restituisce l' `IDebugExpression2` oggetto da `IDebugExpressionContext2::ParseText` .

### <a name="evaluate-the-expression"></a>Valutare l'espressione
 Visual Studio chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per valutare l'espressione analizzata. Entrambi questi metodi chiamano [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( `IDebugExpression2::EvaluateSync` chiama immediatamente il metodo, mentre `IDebugExpression2::EvaluateAsync` chiama il metodo tramite un thread in background) per valutare l'espressione analizzata e restituire un'interfaccia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il valore e il tipo dell'espressione analizzata. `IDebugParsedExpression::EvaluateSync` Usa l'oggetto SH, Address e Binder fornito per convertire l'espressione analizzata in un valore effettivo, rappresentato dall' `IDebugProperty2` interfaccia.

### <a name="for-example"></a>Ad esempio:
 Quando viene raggiunto un punto di interruzione in un programma in esecuzione, l'utente sceglie di visualizzare una variabile nella finestra di dialogo controllo **immediato** . In questa finestra di dialogo vengono visualizzati il nome della variabile, il relativo valore e il relativo tipo. In genere, l'utente può modificare il valore.

 Quando viene visualizzata la finestra di dialogo controllo **immediato** , il nome della variabile da esaminare viene inviato come testo a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Viene restituito un oggetto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) che rappresenta l'espressione analizzata, in questo caso la variabile. Viene quindi chiamato [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per produrre un `IDebugProperty2` oggetto che rappresenta il valore e il tipo della variabile e il relativo nome. Queste informazioni vengono visualizzate.

 Se l'utente modifica il valore della variabile, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) viene chiamato con il nuovo valore, che modifica il valore della variabile in memoria, in modo che venga usato quando il programma riprende l'esecuzione.

 Per ulteriori informazioni su questo processo di visualizzazione dei valori delle variabili, vedere Visualizzazione di variabili [locali](../../extensibility/debugger/displaying-locals.md) . Per informazioni dettagliate sulla modalità di modifica del valore di una variabile, vedere [modifica del valore di un oggetto locale](../../extensibility/debugger/changing-the-value-of-a-local.md) .

## <a name="in-this-section"></a>Contenuto della sezione
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Fornisce gli argomenti che vengono passati quando il DE chiama il EE.

 [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Descrive le interfacce cruciali necessarie per la scrittura di un EE, insieme al contesto di valutazione.

## <a name="see-also"></a>Vedi anche
- [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)
- [Modifica del valore di un oggetto locale](../../extensibility/debugger/changing-the-value-of-a-local.md)
