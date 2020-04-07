---
title: "Architettura dell'analizzatore di espressioni : Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738702"
---
# <a name="expression-evaluator-architecture"></a>Architettura dell'analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'integrazione di un linguaggio proprietario nel pacchetto di debug di Visual Studio significa che è necessario impostare le interfacce dell'analizzatore di espressioni (EE) necessarie e chiamare il provider di simboli di runtime del linguaggio comune (SP) e le interfacce del gestore di associazione. Gli oggetti SP e binder, insieme all'indirizzo di esecuzione corrente, sono il contesto in cui vengono valutate le espressioni. Le informazioni che queste interfacce producono e utilizzano rappresentano i concetti chiave nell'architettura di un EE.

## <a name="overview"></a>Panoramica

### <a name="parse-the-expression"></a>Analizzare l'espressioneParse the Expression
 Quando si esegue il debug di un programma, le espressioni vengono valutate per diversi motivi, ma sempre quando il programma in fase di debug è stato arrestato in corrispondenza di un punto di interruzione (un punto di interruzione inserito dall'utente o uno causato da un'eccezione). È in questo momento in cui Visual Studio ottiene uno stack frame, come rappresentato dal [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia, dal motore di debug (DE). Visual Studio chiama quindi [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Questa interfaccia rappresenta un contesto in cui le espressioni possono essere valutate; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) è il punto di ingresso al processo di valutazione. Fino a questo punto, tutte le interfacce vengono implementate dal DE.

 Quando `IDebugExpressionContext2::ParseText` viene chiamato, il DE crea un'istanza di EE associato al linguaggio del file di origine in cui si è verificato il punto di interruzione (il DE crea anche un'istanza di SH a questo punto). L'EE è rappresentato dal [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaccia. Il DE chiama quindi [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per convertire l'espressione (in formato testo) in un'espressione analizzata, pronta per la valutazione. Questa espressione analizzata è rappresentata dal [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaccia. L'espressione viene in genere analizzata e non valutata a questo punto.

 Il DE crea un oggetto che implementa il `IDebugParsedExpression` [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, inserisce l'oggetto nell'oggetto `IDebugExpression2` e restituisce l'oggetto `IDebugExpression2` da `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>Valutare l'espressione
 Visual Studio chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per valutare l'espressione analizzata. Entrambi questi metodi chiamano`IDebugExpression2::EvaluateSync` [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( chiama `IDebugExpression2::EvaluateAsync` il metodo immediatamente, mentre chiama il metodo tramite un thread in background) per valutare l'espressione analizzata e restituire un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il valore e il tipo dell'espressione analizzata. `IDebugParsedExpression::EvaluateSync`utilizza lo SH, l'indirizzo e il gestore di associazione forniti `IDebugProperty2` per convertire l'espressione analizzata in un valore effettivo, rappresentato dall'interfaccia.

### <a name="for-example"></a>Ad esempio:
 Dopo aver raggiunto un punto di interruzione in un programma in esecuzione, l'utente sceglie di visualizzare una variabile nella finestra di dialogo **Controllo oggetti guida.** Questa finestra di dialogo mostra il nome della variabile, il relativo valore e il relativo tipo. L'utente può in genere modificare il valore.

 Quando viene visualizzata la finestra di dialogo **Controllo oggetti da avvio** rapido, il nome della variabile esaminata viene inviato come testo a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Restituisce un [oggetto IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) che rappresenta l'espressione analizzata, in questo caso la variabile. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) viene quindi chiamato `IDebugProperty2` per produrre un oggetto che rappresenta il valore e il tipo della variabile, nonché il relativo nome. È questa informazione che viene visualizzata.

 Se l'utente modifica il valore della variabile, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) viene chiamato con il nuovo valore, che modifica il valore della variabile in memoria in modo che venga utilizzato quando il programma riprende l'esecuzione.

 Per ulteriori informazioni su questo processo di visualizzazione dei valori delle variabili, vedere [Visualizzazione delle variabili.](../../extensibility/debugger/displaying-locals.md) Vedere [Modifica del valore di un locale](../../extensibility/debugger/changing-the-value-of-a-local.md) per ulteriori dettagli su come viene modificato il valore di una variabile.

## <a name="in-this-section"></a>Contenuto della sezione
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Fornisce gli argomenti che vengono passati quando il DE chiama l'eE.

 [Interfacce dell'analizzatore di espressioni chiaveKey expression evaluator interfaces](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Descrive le interfacce cruciali necessarie per la scrittura di un EE, insieme al contesto di valutazione.

## <a name="see-also"></a>Vedere anche
- [Scrittura di un analizzatore di espressioni CLRWriting a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzazione di gente del posto](../../extensibility/debugger/displaying-locals.md)
- [Modifica del valore di un](../../extensibility/debugger/changing-the-value-of-a-local.md)
