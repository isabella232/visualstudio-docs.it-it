---
title: Architettura dell'analizzatore di espressioni | Microsoft Docs
description: Informazioni sull'integrazione di un linguaggio proprietario nel pacchetto di debug Visual Studio, tra cui l'analizzatore di espressioni e le interfacce del provider/binder di simboli.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7a1d394cf9b985c1b239b0184f7fa3580c7775537c3e1b8b3beba4c48447e59f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417808"
---
# <a name="expression-evaluator-architecture"></a>Architettura dell'analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 L'integrazione di un linguaggio proprietario nel pacchetto di debug Visual Studio significa che è necessario configurare le interfacce dell'analizzatore di espressioni (edizione Enterprise) necessarie e chiamare il provider di simboli di runtime e le interfacce dello strumento di associazione common language. Gli oggetti SP e binder, insieme all'indirizzo di esecuzione corrente, sono il contesto in cui vengono valutate le espressioni. Le informazioni che queste interfacce producono e utilizzano rappresentano i concetti chiave nell'architettura di un edizione Enterprise.

## <a name="overview"></a>Panoramica

### <a name="parse-the-expression"></a>Analizzare l'espressione
 Quando si esegue il debug di un programma, le espressioni vengono valutate per diversi motivi, ma sempre quando il programma in fase di debug è stato arrestato in corrispondenza di un punto di interruzione (un punto di interruzione inserito dall'utente o uno causato da un'eccezione). È in questo momento che Visual Studio ottiene un stack frame, come rappresentato [dall'interfaccia IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) dal motore di debug. Visual Studio quindi chiama [GetExpressionContext per](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) ottenere [l'interfaccia IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Questa interfaccia rappresenta un contesto in cui è possibile valutare le espressioni. [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) è il punto di ingresso al processo di valutazione. Fino a questo punto, tutte le interfacce vengono implementate da DE.

 Quando viene chiamato , de crea un'istanza dell'edizione Enterprise associata alla lingua del file di origine in cui si è verificato il punto di interruzione (de crea anche un'istanza `IDebugExpressionContext2::ParseText` di SH a questo punto). Il edizione Enterprise è rappresentato [dall'interfaccia IDebugExpressionEvaluator.](../../extensibility/debugger/reference/idebugexpressionevaluator.md) De chiama quindi [Parse per](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) convertire l'espressione (in formato testo) in un'espressione analizzata, pronta per la valutazione. Questa espressione analizzata è rappresentata [dall'interfaccia IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md) L'espressione viene in genere analizzata e non valutata a questo punto.

 DE crea un oggetto che implementa [l'interfaccia IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) inserisce l'oggetto nell'oggetto e `IDebugParsedExpression` restituisce `IDebugExpression2` `IDebugExpression2` l'oggetto da `IDebugExpressionContext2::ParseText` .

### <a name="evaluate-the-expression"></a>Valutare l'espressione
 Visual Studio chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync per](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) valutare l'espressione analizzata. Entrambi questi metodi chiamano [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( chiama immediatamente il metodo , mentre chiama il metodo tramite un thread in background) per valutare l'espressione analizzata e restituire un'interfaccia `IDebugExpression2::EvaluateSync` `IDebugExpression2::EvaluateAsync` [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il valore e il tipo dell'espressione analizzata. `IDebugParsedExpression::EvaluateSync` usa sh, indirizzo e binder forniti per convertire l'espressione analizzata in un valore effettivo, rappresentato `IDebugProperty2` dall'interfaccia .

### <a name="for-example"></a>Ad esempio:
 Dopo aver raggiunto un punto di interruzione in un programma in esecuzione, l'utente sceglie di visualizzare una variabile nella **finestra di dialogo** Controllo immediato . Questa finestra di dialogo mostra il nome della variabile, il relativo valore e il relativo tipo. L'utente può in genere modificare il valore.

 Quando viene **visualizzata la** finestra di dialogo Controllo immediato, il nome della variabile esaminata viene inviato come testo a [ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Viene restituito [un oggetto IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) che rappresenta l'espressione analizzata, in questo caso la variabile . [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) viene quindi chiamato per produrre un oggetto che rappresenta il valore e il tipo della `IDebugProperty2` variabile, nonché il relativo nome. Si tratta di queste informazioni visualizzate.

 Se l'utente modifica il valore della variabile, Viene chiamato [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) con il nuovo valore, che modifica il valore della variabile in memoria in modo che verrà usato quando il programma riprenderà l'esecuzione.

 Per [altri dettagli su questo](../../extensibility/debugger/displaying-locals.md) processo di visualizzazione dei valori delle variabili, vedere Visualizzazione delle variabili locali. Vedere [Modifica del valore di una variabile](../../extensibility/debugger/changing-the-value-of-a-local.md) locale per altri dettagli su come viene modificato il valore di una variabile.

## <a name="in-this-section"></a>Contenuto della sezione
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md) Fornisce gli argomenti passati quando de chiama il metodo edizione Enterprise.

 [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Descrive le interfacce cruciali necessarie per la scrittura di edizione Enterprise, insieme al contesto di valutazione.

## <a name="see-also"></a>Vedi anche
- [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzazione delle variabili locali](../../extensibility/debugger/displaying-locals.md)
- [Modifica del valore di un oggetto locale](../../extensibility/debugger/changing-the-value-of-a-local.md)
