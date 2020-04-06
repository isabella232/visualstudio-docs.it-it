---
title: Scrittura di un analizzatore di espressioni di Common Language Runtime Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712317"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Scrittura di un analizzatore di espressioni di Common Language RuntimeWriting a common language runtime expression evaluator
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'analizzatore di espressioni (EE) è la parte di un motore di debug (DE) che gestisce la sintassi e la semantica del linguaggio di programmazione che ha prodotto il codice sottoposto a debug. Le espressioni devono essere valutate nel contesto di un linguaggio di programmazione. Ad esempio, in alcune lingue, l'espressione "A- B" significa "la somma di A e B". In altre lingue, la stessa espressione potrebbe significare "A o B". Pertanto, è necessario scrivere un EE separato per ogni linguaggio di programmazione che genera codice oggetto per eseguire il debug nell'IDE di Visual Studio.

 Alcuni aspetti del pacchetto di debug di Visual Studio devono interpretare il codice nel contesto del linguaggio di programmazione. Ad esempio, quando l'esecuzione si arresta in corrispondenza di un punto di interruzione, tutte le espressioni che l'utente ha digitato in una finestra **Espressioni di** controllo devono essere valutate e visualizzate. L'utente può modificare il valore di una variabile locale digitando un'espressione in una finestra **Espressioni di** controllo o nella finestra **Immediata.**

## <a name="in-this-section"></a>Contenuto della sezione
 [Common Language Runtime e valutazione delle espressioni](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Viene illustrato che quando si integra un linguaggio di programmazione proprietario nell'IDE di Visual Studio, la scrittura di un'analizzatore di Espressioni in grado di valutare espressioni nel contesto del linguaggio proprietario consente di compilare in un linguaggio MSIL (Microsoft Intermediate Language) senza scrivere un motore di debug.

 [Architettura dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-architecture.md) Viene illustrato come implementare le interfacce EE necessarie e chiamare il provider di simboli di Common Language Runtime (SP) e le interfacce del gestore di associazione.

 [Registrare un analizzatore di espressioniRegister an expression evaluator](../../extensibility/debugger/registering-an-expression-evaluator.md) Nota che EE deve registrarsi come class factory sia con Common Language Runtime che con gli ambienti di Runtime di Visual Studio.

 [Implementare un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md) Viene descritto come il processo di valutazione di un'espressione include il motore di debug (DE), il provider di simboli (SP), l'oggetto gestore di associazione e l'analizzatore di espressioni (EE).

 [Visualizza gente del posto](../../extensibility/debugger/displaying-locals.md) Descrive come, quando l'esecuzione viene sospesa, il pacchetto di debug chiama il DE per ottenere un elenco di variabili locali e argomenti.

 [Valutare un'espressione della finestra Espressioni di controlloEvaluate](../../extensibility/debugger/evaluating-a-watch-window-expression.md) a watch window expression Documenta il modo in cui il pacchetto di debug di Visual Studio chiama il DE per determinare il valore corrente di ogni espressione nella relativa lista di controllo.

 [Modificare il valore di un](../../extensibility/debugger/changing-the-value-of-a-local.md) Viene illustrato che nella modifica del valore di una riga locale, a ogni riga della finestra Variabili locali è associato un oggetto che fornisce il nome, il tipo e il valore corrente di un oggetto locale.

 [Implementare visualizzatori](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) di tipo e visualizzatori personalizzati Viene illustrato quale interfaccia deve essere implementata da quale componente per supportare i visualizzatori di tipo e visualizzatori personalizzati.

## <a name="see-also"></a>Vedere anche
 [Estendibilità del debugger di Visual StudioVisual Studio debugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
