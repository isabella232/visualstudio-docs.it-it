---
title: Architettura dell'analizzatore di espressioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8e0aa8f5cc45e0f6e012ecb3f0a27a22725a259
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421218"
---
# <a name="expression-evaluator-architecture"></a>Architettura dell'analizzatore di espressioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'integrazione di un linguaggio proprietario nel pacchetto di debug di Visual Studio si intende implementare le interfacce dell'analizzatore di espressioni (EE) espressione necessaria e chiamare il provider in fase di esecuzione simbolo del linguaggio comune (SP) e le interfacce dello strumento di associazione. Gli oggetti SP e dello strumento di associazione, oltre all'indirizzo di esecuzione corrente, sono il contesto in cui le espressioni vengono valutate. Le informazioni che queste interfacce producono e utilizzano rappresentano i concetti principali nell'architettura di un EE.  
  
## <a name="overview"></a>Panoramica  
  
### <a name="parsing-the-expression"></a>L'analisi dell'espressione  
 Quando si esegue il debug di un programma, le espressioni vengono valutate per diversi motivi, ma sempre quando il programma sottoposto a debug è stato arrestato a un punto di interruzione (un punto di interruzione inserito dall'utente o uno causato da un'eccezione). È il momento quando Visual Studio Ottiene uno stack frame, come rappresentate dal [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia, dal motore di debug (DE). Visual Studio chiama quindi [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Questa interfaccia rappresenta un contesto in cui le espressioni possono essere valutate; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) è il punto di ingresso per il processo di valutazione. Fino a questo punto, tutte le interfacce vengono implementate per la Germania.  
  
 Quando si `IDebugExpressionContext2::ParseText` viene chiamato, la Germania crea un'istanza di motore di esecuzione associate alla lingua del file di origine in cui si è verificato il punto di interruzione (la Germania anche un'istanza di SH a questo punto). L'analizzatore di Espressioni è rappresentato dal [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaccia. Chiama quindi la Germania [analizzare](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per convertire l'espressione (in formato testo) in un'espressione analizzata, pronto per la valutazione. Questa espressione analizzata è rappresentata dal [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaccia. Si noti che l'espressione viene in genere analizzato e non valutato a questo punto.  
  
 La Germania crea un oggetto che implementa il [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) dell'interfaccia, inserisce il `IDebugParsedExpression` nell'oggetto il `IDebugExpression2` oggetto e restituisce il `IDebugExpression2` dall'oggetto `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>La valutazione dell'espressione  
 Visual Studio chiama uno [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oppure [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per valutare l'espressione analizzata. Entrambi questi metodi chiamano [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` chiama il metodo immediatamente, mentre `IDebugExpression2::EvaluateAsync` chiama il metodo mediante un thread in background) per valutare l'espressione analizzata e restituire un [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il valore e il tipo dell'espressione analizzata. `IDebugParsedExpression::EvaluateSync` Usa il SH, indirizzo e dello strumento di associazione forniti per convertire l'espressione analizzata in un valore effettivo, rappresentato dal `IDebugProperty2` interfaccia.  
  
### <a name="for-example"></a>Per esempio  
 Dopo che un punto di interruzione in un programma in esecuzione, l'utente sceglie di visualizzare una variabile nel **controllo immediato** nella finestra di dialogo. Questa finestra di dialogo Mostra il nome della variabile, il relativo valore e il relativo tipo. L'utente può modificare in genere il valore.  
  
 Quando la **controllo immediato** viene visualizzata la finestra di dialogo, il nome della variabile in corso l'analisi viene inviato come testo [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Restituisce un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto che rappresenta l'espressione analizzata, in questo caso, la variabile. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) viene quindi chiamato in modo da produrre un `IDebugProperty2` oggetto che rappresenta il valore della variabile e tipo, nonché il relativo nome. È questa informazioni visualizzate.  
  
 Se l'utente modifica il valore della variabile, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) viene chiamato con il nuovo valore, che modifica il valore della variabile in memoria in modo che verrà usato quando il programma riprende l'esecuzione.  
  
 Visualizzare [variabili locali visualizzazione](../../extensibility/debugger/displaying-locals.md) per altri dettagli su questo processo di visualizzazione dei valori delle variabili. Visualizzare [modificando il valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md) per altri dettagli sul modo in cui viene modificato il valore della variabile.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti passati durante la Germania chiama l'analizzatore di Espressioni.  
  
 [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Descrive le interfacce fondamentali necessari quando si scrive un EE, insieme al contesto di valutazione.  
  
## <a name="see-also"></a>Vedere anche  
 [La scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)   
 [Modifica del valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md)
